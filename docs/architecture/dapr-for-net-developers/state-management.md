---
title: Davpr durum yönetimi yapı taşı
description: Durum yönetimi oluşturma bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı.
author: sanderm
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: 21fc8cb72a4eb2e03d388cbdf27b4021dc3af38b
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629444"
---
# <a name="the-dapr-state-management-building-block"></a>Davpr durum yönetimi yapı taşı

Dağıtılmış uygulamalar bağımsız hizmetlerden oluşur. Her hizmetin durum bilgisiz olması gerekir, ancak bazı hizmetler iş işlemlerinin tamamlanabilmesi için durumu izlemeli olmalıdır. Bir eCommerce sitesi için bir alışveriş sepeti hizmeti düşünün. Hizmet durumu izleyemiyor, müşteri web sitesini bırakarak alışveriş sepeti içeriğini gevşekerek kayıp satışı ve memnun olmayan müşteri deneyimine neden olur. Bu senaryolar için durumun dağıtılmış bir durum deposuna kalıcı olması gerekir. [Davpr durum yönetimi yapı taşı](https://docs.dapr.io/developing-applications/building-blocks/state-management/) durum izlemeyi basitleştirir ve çeşitli veri depoları arasında gelişmiş özellikler sunar.

> [!NOTE]
> Durumu bir **dış** veri deposunda depolayarak, bir hizmet **durum bilgisiz** olarak değerlendirilir. **Statefull** Hizmetleri genellikle durumu bellekte veya diskte bulunan tek bir sunucuda yerel olarak depolar. Durum bilgisi içermeyen hizmetler, durum bilgisi olan hizmetlerden daha sık kırmızıdır Belirli bir kullanıcıdan gelen isteklerin aynı hizmet örneği tarafından işlenmesini gerektirmez. Sonuç olarak, durum bilgisi olan hizmetler, istek hacmi arttıkça yatay olarak ölçeklendirebilir.

Durum yönetimi oluşturma bloğunu denemek için, [Bölüm 3 ' teki sayaç uygulaması örneğine](getting-started.md)göz atın.

## <a name="what-it-solves"></a>Ne çözdüğü

Dağıtılmış bir uygulamadaki izleme durumu zor olabilir. Örneğin:

- Uygulama farklı türlerde veri depoları gerektirebilir.
- Verilere erişmek ve verileri güncelleştirmek için farklı tutarlılık düzeyleri gerekebilir.
- Aynı anda birden çok Kullanıcı, çakışma çözümü gerektiren verileri güncelleştirebilir.
- Hizmetler, veri deposuyla etkileşim kurarken oluşan kısa süreli [geçici hataları](https://docs.microsoft.com/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) yeniden denemelidir.

Davpr durum yönetimi oluşturma bloğunda bu sorunlar ele alınmaktadır. Bağımlılıklar olmadan izleme durumunu veya üçüncü taraf depolama SDK 'lerinde öğrenme eğrisini kolaylaştırır.

> [!IMPORTANT]
> Davpr durum yönetimi bir [anahtar/değer](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview#keyvalue-stores) API 'si sağlar. Özelliği ilişkisel veya grafik veri depolamayı desteklemez.

## <a name="how-it-works"></a>Nasıl çalışır?

Uygulama, anahtar/değer verilerini depolamak ve almak için bir davpr sepet ile etkileşime girer. Altyapı API 'SI, dışarıdan veri kalıcı hale getirmek için yapılandırılabilir bir durum depolama bileşeni kullanır. Geliştiriciler Azure Cosmos DB, SQL Server ve Cassandra içeren [desteklenen bir durum depoları](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/) koleksiyonu arasından seçim yapabilir.

API, HTTP ya da gRPC ile çağrılabilir. HTTP API 'sini çağırmak için aşağıdaki URL 'YI kullanın:

```http
http://localhost:<dapr-port>/v1.0/state/<store-name>/
```

- `<dapr-port>`: Bu, Davpr 'nin dinlediği HTTP bağlantı noktasıdır.
- `<store-name>`: kullanılacak durum depolama bileşeninin adı.

Şekil 5-1 ' de, bir Davpr etkin alışveriş sepeti hizmetinin adlı bir anahtar/değer çiftini nasıl depoladığı gösterilmektedir `statestore` .

![Bir anahtar/değer çiftinin bir Davpr durum deposunda depolanması diyagramı.](media/state-management/state-management-flow.png)

**Şekil 5-1**. Bir anahtar/değer çiftinin bir Davpr durum deposunda depolanması.

Önceki şekildeki adımlara göz önünde edin:

1. Sepet hizmeti, Davpr sidecar 'den durum yönetimi API 'sini çağırır. İsteğin gövdesi birden çok anahtar/değer çifti içerebilen bir JSON dizisi barındırır.
1. Davpr sepet, bileşen yapılandırma dosyasına göre durum deposunu belirler. Bu durumda, Redsıs cache durum deposudur.
1. Sepet, verileri redsıs önbelleğine devam ettirir.

Depolanan verilerin alınması benzer bir API çağrıdır. Aşağıdaki örnekte, bir *kıvrımlı* komutu, bu verileri, davpr sepet API 'sini çağırarak alır:

```console
curl http://localhost:3500/v1.0/state/statestore/basket1
```

Komut, yanıt gövdesinde depolanan durumu döndürür:

```json
{
  "items": [
    {
      "itemId": "DaprHoodie",
      "quantity": 1
    }
  ],
  "customerId": 1
}
```

Aşağıdaki bölümlerde, durum yönetimi oluşturma bloğunun daha gelişmiş özelliklerinin nasıl kullanılacağı açıklanmaktadır.

### <a name="consistency"></a>Tutarlılık

[Cap](https://en.wikipedia.org/wiki/CAP_theorem) 'ler, durumu depolayan dağıtılmış sistemler için uygulanan bir ilkeler kümesidir. Şekil 5-2, CAP 'in üç özelliğini gösterir.

![Üst sınır.](media/state-management/cap-theorem.png)

**Şekil 5-2**. Üst sınır.

Bu, dağıtılmış veri sistemlerinin tutarlılık, kullanılabilirlik ve bölüm toleransı arasında bir denge sunmadığını belirtir. Ve tüm veri deposu, *üç özelliği yalnızca iki özelliği garanti* edebilir:

- *Tutarlılık* (**C**). Kümedeki her düğüm, sistemin tüm çoğaltmalar güncellene kadar isteği engellemeniz gerekir olsa bile en son verilerle yanıt verir. Şu anda güncelleştirilen bir öğe için "tutarlı bir sistem" sorgusu yaparsanız, tüm çoğaltmalar başarıyla güncelleştirilene kadar bir yanıt alırsınız. Ancak, en güncel verileri her zaman alacaksınız.

- *Kullanılabilirlik* (**A**). Her düğüm, bu yanıt en son veriler olmasa bile anında yanıt döndürür. Güncelleştiren bir öğe için "kullanılabilir sistem" i sorgulayıp, hizmetin bu anda sağlayabilmesini sağlayacak en iyi yanıtı alırsınız.

- *Bölüm toleransı* (**P**). Çoğaltılan bir veri düğümü başarısız olsa da veya diğer çoğaltılan veri düğümleriyle bağlantıyı kaybederse bile sistemin çalışmaya devam etmesini güvence altına alır.

Dağıtılmış uygulamalar **P** özelliğini işlemelidir. Hizmetler ağ çağrılarında birbirleriyle iletişim kurduklarında, ağ kesintileri (**P**) oluşur. Bu şekilde, Dağıtılmış uygulamaların **AP** veya **CP** olması gerekir.

**AP** uygulamaları tutarlılık üzerinde kullanılabilirlik seçer. Davpr, bu seçeneği **nihai tutarlılık** stratejisiyle destekler. Çok sayıda çoğaltmalarda gereksiz verileri depolayan Azure CosmosDB gibi temel bir veri deposunu göz önünde bulundurun. Nihai tutarlılık sayesinde, durum deposu güncelleştirmeyi bir çoğaltmaya yazar ve yazma isteğini istemcisiyle tamamlar. Bu süreden sonra mağaza, çoğaltmaları zaman uyumsuz olarak güncelleştirecektir. Okuma istekleri, en son güncelleştirmeyi henüz almamış olan çoğaltmalar dahil olmak üzere çoğaltmalardan herhangi birinden veri döndürebilir.

**CP** uygulamaları kullanılabilirlik üzerinden tutarlılık seçer. Davpr bu seçeneği **güçlü tutarlılık** stratejisi ile destekler. Bu senaryoda, durum deposu yazma isteğini tamamlamadan *önce* gerekli *çoğaltmaları (veya* bazı durumlarda, bir *çekirdeğin çekirdeği* ) zaman uyumlu olarak güncelleştirir. Okuma işlemleri, düzenli olarak çoğaltmalar genelinde en güncel verileri döndürür.

Bir durum işleminin tutarlılık düzeyi, işleme bir *tutarlılık ipucu* ekleyerek belirtilir. Aşağıdaki *kıvrımlı* komutu, güçlü bir `Hello=World` tutarlılık ipucu kullanarak bir durum deposuna bir anahtar/değer çifti Yazar:

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        {
          "key": "Hello",
          "value": "World",
          "options": {
            "consistency": "strong"
          }
        }
      ]' 
```

> [!IMPORTANT]
> Bu işlem, işleme eklenen tutarlılık ipucunu karşılamak için bir Davpr durum depolama bileşenine sahiptir. Tüm veri depoları, her iki tutarlılık düzeyini de desteklemez. Tutarlılık İpucu **ayarlanmamışsa, varsayılan** davranış son ' dur.

### <a name="concurrency"></a>Eşzamanlılık

Çok kullanıcılı bir uygulamada, birden çok kullanıcının aynı anda aynı verileri (aynı zamanda) güncelleştirmesidir. Davpr, çakışmaları yönetmek için iyimser eşzamanlılık denetimini (OCC) destekler. OCC, kullanıcıların verilerin farklı bölümlerinde çalıştığı için güncelleştirme çakışmalarının yaygın olmayan bir varsayımına dayanır. Bir güncelleştirmenin başarılı olacağını varsaymak ve değilse yeniden denemek daha etkilidir. Alternatif olarak, kötümser kilitlemeyi uygulamak, veri çekişmesine neden olan uzun süreli kilitleme ile performansı etkileyebilir.

DAPR, ETags kullanarak iyimser eşzamanlılık denetimini (OCC) destekler. ETag, depolanan anahtar/değer çiftinin belirli bir sürümüyle ilişkili bir değerdir. Anahtar/değer çifti her güncelleştirilişinde ETag değeri de güncelleştirilir. İstemci bir anahtar/değer çifti aldığında, yanıt geçerli ETag değerini içerir. Bir istemci bir anahtar/değer çiftini güncelleştirdiğinde veya sildiği zaman, bu ETag değerini istek gövdesinde geri göndermelidir. Bu sırada başka bir istemci verileri güncelleştirdiyseniz Eetiketler eşleşmez ve istek başarısız olur. Bu noktada, istemci güncelleştirilmiş verileri almalıdır, değişikliği yeniden yapar ve güncelleştirmeyi yeniden göndermelidir. Bu strateji **ilk yazma-WINS** olarak adlandırılır.

Davpr Ayrıca **son yazma WINS** stratejisini da destekler. Bu yaklaşımda istemci, yazma isteğine bir ETag iliştirmez. Durum depolama bileşeni, temel alınan değer oturum sırasında değişmiş olsa bile güncelleştirmeye her zaman izin verir. Son yazma-WINS, düşük veri çekişmesi sayesinde yüksek aktarım hızı yazma senaryolarında kullanışlıdır. Ayrıca, zaman zaman bir Kullanıcı güncelleştirmesinin üzerine yazılması toleranslı olabilir.

### <a name="transactions"></a>İşlemler

Davpr, bir veri deposuna bir işlem olarak uygulanan tek bir işlem olarak *çok öğe değişiklikleri* yazabilir. Bu işlevsellik yalnızca [ACID](https://en.wikipedia.org/wiki/ACID) işlemlerini destekleyen veri depoları için kullanılabilir. Bu yazma sırasında, bu depolar redin, MongoDB, PostgreSQL, SQL Server ve Azure CosmosDB 'yi içerir.

Aşağıdaki örnekte, tek bir işlemde durum deposuna çoklu öğe işlemi gönderilir. İşlemin yürütülmesi için tüm işlemlerin başarılı olması gerekir. Bir veya daha fazla işlem başarısız olursa, tüm işlem geri alınır.

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name>/transaction \
  -H "Content-Type: application/json" \
  -d '{
        "operations": [
          {
            "operation": "upsert",
            "request": { "key": "Key1", "value": "Value1"
            }
          },
          {
            "operation": "delete",
            "request": { "key": "Key2" }
          }
        ]
      }'
```

İşlemleri desteklemeyen veri depoları için, birden çok anahtar hala tek bir istek olarak gönderilebilir. Aşağıdaki örnek bir **toplu** yazma işlemini göstermektedir:

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        { "key": "Key1", "value": "Value1" },
        { "key": "Key2", "value": "Value2" }
      ]' 
```

Yığın işlemleri için, Davpr her anahtar/değer çifti güncelleştirmesini, veri deposuna ayrı bir istek olarak gönderir.

## <a name="use-the-dapr-net-sdk"></a>Davpr .NET SDK 'sını kullanma

Davpr .NET SDK, .NET Core platformu için dile özgü destek sağlar. Geliştiriciler, `DaprClient` veri okumak ve yazmak için [Bölüm 3](getting-started.md) ' te tanıtılan sınıfı kullanabilir. Aşağıdaki örnek, `DaprClient.GetStateAsync<TValue>` bir durum deposundan veri okumak için yönteminin nasıl kullanılacağını gösterir. Yöntemi, depolama adını, `statestore` ve anahtarını `AMS` Parametreler olarak bekler:

```csharp
var weatherForecast = await daprClient.GetStateAsync<WeatherForecast>("statestore", "AMS");
```

Durum deposu anahtar için veri içermiyorsa `AMS` , sonuç olur `default(WeatherForecast)` .

Veri deposuna veri yazmak için `DaprClient.SaveStateAsync<TValue>` yöntemini kullanın:

```csharp
daprClient.SaveStateAsync("statestore", "AMS", weatherForecast);
```

Örnek, **en son yazma WINS** stratejisini bir ETag değeri olarak durum depolama bileşenine geçirilmediğinden kullanır. İyimser eşzamanlılık denetimini (OCC) **ilk yazma WINS** stratejisi ile kullanmak için, ilk olarak yöntemi kullanarak geçerli ETag 'i alın `DaprClient.GetStateAndETagAsync` . Ardından, güncelleştirilmiş değeri yazın ve yöntemi kullanarak alınan ETag üzerinde geçiş yapın `DaprClient.TrySaveStateAsync` .

```csharp
var (weatherForecast, etag) = await daprClient.GetStateAndETagAsync<WeatherForecast>("statestore", city);

// ... make some changes to the retrieved weather forecast

var result = await daprClient.TrySaveStateAsync("statestore", city, weatherForecast, etag);
```

Veriler `DaprClient.TrySaveStateAsync` alındıktan sonra durum deposunda veri (ve Ilişkili ETag) değiştirildiğinde yöntem başarısız olur. Yöntemi, çağrının başarılı olup olmadığını göstermek için bir Boole değeri döndürür. Hata işleme stratejisi, güncelleştirilmiş verileri durum deposundan yeniden yüklemeniz, değişikliği yeniden yapmanız ve güncelleştirmeyi yeniden göndermelidir.

Verilerdeki diğer değişikliklerden bağımsız olarak her zaman bir yazma işleminin başarılı olmasını istiyorsanız, **son yazma WINS** stratejisini kullanın.

SDK, verileri toplu olarak alma, verileri silme ve işlemleri yürütme gibi diğer yöntemler sağlar. Daha fazla bilgi için bkz. [Davpr .NET SDK deposu](https://github.com/dapr/dotnet-sdk).

### <a name="aspnet-core-integration"></a>ASP.NET Core tümleştirme

Davpr, modern bulut tabanlı Web uygulamaları oluşturmaya yönelik platformlar arası bir çatı olan ASP.NET Core da destekler. Davpr SDK, durum yönetimi yeteneklerini doğrudan [ASP.NET Core modeli bağlama](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) özelliklerine tümleştirir. Yapılandırma basittir. Bir `IMVCBuilder.AddDapr` `.AddDapr` `Startup.cs` sonraki örnekte gösterildiği gibi sınıfınıza Extension metodunu ekleyerek öğesini ekleyin:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers().AddDapr();
}
```

Bir kez yapılandırıldıktan sonra, Davpr ASP.NET Core özniteliğini kullanarak doğrudan bir denetleyici eylemine bir anahtar/değer çifti ekleyebilir `FromState` . Nesnesine başvurmak `DaprClient` artık gerekli değildir. Sonraki örnekte, belirli bir şehirde Hava durumu tahminini döndüren bir Web API 'SI gösterilmektedir:

```csharp
[HttpGet("{city}")]
public ActionResult<WeatherForecast> Get([FromState("statestore", "city")] StateEntry<WeatherForecast> forecast)
{
    if (forecast.Value == null)
    {
      return NotFound();
    }

    return forecast.Value;
}
```

Örnekte, denetleyici, özelliği kullanarak hava durumu tahminini yükler `FromState` . İlk öznitelik parametresi durum deposudur, `statestore` . İkinci öznitelik parametresi, `city` , durum anahtarını almak için [yol şablonu](https://docs.microsoft.com/aspnet/core/mvc/controllers/routing?#route-templates) değişkeninin adıdır. İkinci parametreyi atlarsanız, `forecast` yol şablonu değişkenini aramak için, bağlantılı yöntem parametresi () adı kullanılır.

`StateEntry`Sınıfı, tek bir anahtar/değer çifti için alınan tüm bilgilerin özelliklerini içerir: `StoreName` , `Key` , `Value` ve `ETag` . ETag, iyimser eşzamanlılık denetimi (OCC) stratejisi uygulamak için yararlıdır. Sınıfı ayrıca bir örnek gerekmeden alınan anahtar/değer verilerini silmek veya güncelleştirmek için yöntemler sağlar `DaprClient` . Sonraki örnekte `TrySaveAsync` yöntemi, OCC kullanılarak alınan hava durumu tahminini güncelleştirmek için kullanılır.

```csharp
[HttpPut("{city}")]
public async Task Put(WeatherForecast updatedForecast, [FromState("statestore", "city")] StateEntry<WeatherForecast> currentForecast)
{
    // update cached current forecast with updated forecast passed into service endpoint
    currentForecast.Value = updatedForecast;

    // update state store
    var success = await currentForecast.TrySaveAsync();
    
    // ... check result
}
```

## <a name="state-store-components"></a>Durum depolama bileşenleri

Bu yazma sırasında, Davpr aşağıdaki işlemsel durum depoları için destek sağlar:

- Azure CosmosDB
- Azure SQL Sunucusu
- MongoDB
- PostgreSQL
- Redis

Davpr Ayrıca CRUD işlemlerini destekleyen durum depoları için destek içerir, ancak işlemsel özellikleri içermez:

- Hava çıkış
- Azure Blob Depolama
- Azure Tablo Depolama
- Cassandra
- Cloudstate
- Couchbase
- etcd
- Google Cloud Firestore
- HashiCorp Tüketil
- Tehlikeli elcast
- Memcached
- Zookeeper

### <a name="configuration"></a>Yapılandırma

Yerel, şirket içinde barındırılan geliştirme için başlatıldığında, Davpr kayıtları Reddir olarak varsayılan durum deposu olarak kaydedilir. Varsayılan durum deposu yapılandırmasına bir örnek aşağıda verilmiştir. Varsayılan adı aklınızda bulunan `statestore` :

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

 > [!NOTE]
 > Birçok durum deposu, her biri farklı bir ada sahip tek bir uygulamaya kaydedilebilir.

Redsıs durum deposu için `redisHost` ve `redisPassword` redsıs örneğine bağlanmak için meta veriler gerekir. Yukarıdaki örnekte, Red, Password (varsayılan olarak boş bir dize) düz bir dize olarak depolanır. En iyi uygulama, şifresiz metin dizelerinden kaçınmaktır ve her zaman gizli başvuruları kullanmalıdır. Gizli yönetim hakkında daha fazla bilgi edinmek için bkz. [Bölüm 10](secrets.md).

Diğer meta veri alanı, `actorStateStore` durum deposunun aktör yapı taşı tarafından kullanılıp kullanılamayacağını belirtir.

### <a name="key-prefix-strategies"></a>Anahtar öneki stratejileri

Durum depolama bileşenleri, temel depodaki anahtar/değer çiftlerini depolamak için farklı stratejileri etkinleştirir. Bir alışveriş sepeti hizmetinin önceki örneğini geri çekin bir müşteri dileklerimizin satın almasını isteyen öğeleri depoluyor:

```console
curl -X POST http://localhost:3500/v1.0/state/statestore \
  -H "Content-Type: application/json" \
  -d '[{
        "key": "basket1",
        "value": {
          "customerId": 1,
          "items": [
            { "itemId": "DaprHoodie", "quantity": 1 }
          ]
        }
     }]' 
```

Redsıs konsol aracını kullanarak redsıs durum deposu bileşeninin verileri nasıl kalıcı hale kullandığını görmek için redo önbelleğinin içine bakın:

```
127.0.0.1:6379> KEYS *
1) "basketservice||basket1"

127.0.0.1:6379> HGETALL basketservice||basket1
1) "data"
2) "{\"items\":[{\"itemId\":\"DaprHoodie\",\"quantity\":1}],\"customerId\":1}"
3) "version"
4) "1"
```

Çıktı, verilerin tam redin **anahtarını** olarak gösterir `basketservice||basket1` . Varsayılan olarak, Davpr, `application id` `basketservice` anahtar için ön ek olarak, davpr örneğinin () öğesini kullanır. Bu adlandırma kuralı, birden çok Davpr örneğinin, anahtar adı çakışmaları olmadan aynı veri deposunu paylaşmasını sağlar. Geliştirici için her zaman, `application id` uygulamayı Davpr ile çalıştırırken aynı şekilde belirtmeniz önemlidir. Atlanırsa, Davpr benzersiz bir uygulama kimliği oluşturacaktır. Değişiklikler varsa `application id` , uygulama önceki anahtar öneki ile depolanan duruma artık erişemez.

Yani, durum depolama bileşeni dosyasındaki meta veri alanındaki anahtar öneki için sabit bir *değer* yapılandırmak mümkündür `keyPrefix` . Aşağıdaki örneği inceleyin:

```yaml
spec:
  metadata:
  - name: keyPrefix
  - value: MyPrefix
```

Sabit anahtar ön eki, durum deposuna birden çok Davpr uygulamasında erişilmesine olanak sağlar. Daha fazlası, ' ı ' `keyPrefix` nin `none` öneki tamamen atlayacak şekilde ayarlanıyor.

## <a name="reference-application-eshopondapr"></a>Başvuru uygulaması: Eshopondadpr

Bu kitap, bir başvuru uygulaması içerir `eShopOnDapr` . Daha önceki bir Microsoft mikro hizmetler başvuru uygulamasından modellenmiştir `eShopOnContainers` .

Özgün [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) mimarisi, `IBasketRepository` sepet hizmeti için veri okumak ve yazmak üzere bir arabirim kullandı. `RedisBasketRepository`Temel veri deposu olarak Reddir kullanılarak uygulamayı sağlayan sınıf:

```csharp
public class RedisBasketRepository : IBasketRepository
{
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _database;

    public RedisBasketRepository(ConnectionMultiplexer redis)
    {
        _redis = redis;
        _database = redis.GetDatabase();
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        var data = await _database.StringGetAsync(customerId);

        if (data.IsNullOrEmpty)
        {
            return null;
        }

        return JsonConvert.DeserializeObject<CustomerBasket>(data);
    }

    // ...
}
```

Bu kod, üçüncü taraf `StackExchange.Redis` NuGet paketini kullanır. Belirli bir müşteri için alışveriş sepetini yüklemek için aşağıdaki adımlar gereklidir:

1. Oluşturucuya bir Ekle `ConnectionMultiplexer` . , `ConnectionMultiplexer` Dosyadaki bağımlılık ekleme çerçevesine kaydedilir `Startup.cs` :

   ```csharp
   services.AddSingleton<ConnectionMultiplexer>(sp =>
   {
       var settings = sp.GetRequiredService<IOptions<BasketSettings>>().Value;
       var configuration = ConfigurationOptions.Parse(settings.ConnectionString, true);
       configuration.ResolveDns = true;
       return ConnectionMultiplexer.Connect(configuration);
   });
   ```

1. `ConnectionMultiplexer`Her bir tüketen sınıfta bir örnek oluşturmak için öğesini kullanın `IDatabase` .

1. `IDatabase`Anahtar olarak verilen öğesini kullanarak bir redin StringGet çağrısını yürütmek için örneği kullanın `customerId` .

1. Redsıs 'ten verilerin yüklenip yüklenmediğini denetle; Aksi takdirde, döndürün `null` .

1. Redsıs 'den nesnesine veri serisini kaldırma `CustomerBasket` ve sonucu döndürme.

Güncelleştirilmiş [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr) başvuru uygulamasında, `DaprBasketRepository` sınıfının yerini alan yeni bir sınıf `RedisBasketRepository` :

```csharp
public class DaprBasketRepository : IBasketRepository
{
    private const string StoreName = "eshop-basket-statestore";

    private readonly DaprClient _daprClient;

    public DaprBasketRepository(DaprClient daprClient)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));;
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        return await _daprClient.GetStateAsync<CustomerBasket>(StoreName, customerId);
    }

    // ...
}
```

Güncelleştirilmiş kod, durum yönetimi yapı taşını kullanarak veri okumak ve yazmak için Davpr .NET SDK 'sını kullanır. Bir müşterinin sepetini yüklemeye yönelik yeni adımlar önemli ölçüde basitleştirilmiştir:

1. Oluşturucuya bir Ekle `DaprClient` . , `DaprClient` Dosyadaki bağımlılık ekleme çerçevesine kaydedilir `Startup.cs` .
1. Bu `DaprClient.GetStateAsync` yöntemi, müşterinin alışveriş sepeti öğelerini yapılandırılmış durum deposundan yüklemek ve sonucu döndürmek için kullanın.

Güncelleştirilmiş uygulama yine de temel alınan veri deposu olarak redde kullanır. Ancak, DAPR `StackExchange.Redis` başvuruları ve karmaşıklığı uygulamadan soyutlar. Bir Davpr yapılandırma dosyası gereklidir:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

Ayrıca, Davpr uygulamasının temel veri deposunun değiştirilmesini de basitleştirir. Örneğin, Azure Tablo depolamaya geçiş yalnızca yapılandırma dosyasının içeriğinin değiştirilmesini gerektirir. Kod değişikliği gerekli değildir.

## <a name="summary"></a>Özet

Davpr durum yönetimi yapı taşı, anahtar/değer verilerini çeşitli veri depolarında depolamak için bir API sağlar. API toplu işlemler, güçlü ve nihai tutarlılık, iyimser eşzamanlılık denetimi ve çoklu öğe işlemleri için destek sağlar.

.NET SDK, .NET Core ve ASP.NET Core için dile özgü destek sağlar. Model bağlama tümleştirmesi, ASP.NET Core denetleyicisi eylem yöntemlerinden durum erişimini ve güncelleştirilmesini basitleştirir.

Eshopondadpr başvuru uygulamasında, Davpr durum yönetimine geçme avantajları net değildir:

1. Yeni uygulama daha az kod satırı kullanır.
1. Üçüncü taraf API 'nin karmaşıklığını soyutlar `StackExchange.Redis` .
1. Temel Redsıs önbelleğinin farklı bir veri deposu türüyle değiştirilmesi artık yalnızca durum depolama yapılandırma dosyasında değişiklik yapılmasını gerektirir.

### <a name="references"></a>Başvurular

- [Davpr desteklenen durum depoları](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/)

> [!div class="step-by-step"]
> [Önceki](reference-application.md) 
>  [Sonraki](service-invocation.md)

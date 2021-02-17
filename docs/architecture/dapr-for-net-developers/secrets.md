---
title: Davpr gizli dizi oluşturma bloğu
description: Gizli dizi oluşturma bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: a1476abc6b224a525f6bb04c78209da5d1654e66
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629479"
---
# <a name="the-dapr-secrets-building-block"></a>Davpr gizli dizi oluşturma bloğu

Kurumsal uygulamalar gizli dizileri gerektirir. Ortak örnekler şunlardır:

- Kullanıcı adı ve parola içeren bir veritabanı bağlantı dizesi.
- Dış Web API 'SI çağırmak için bir API anahtarı.
- Bir dış sistemde kimlik doğrulaması için bir istemci sertifikası.

Gizli dizileri uygulamanın dışından hiçbir şekilde açıklanmayacak şekilde dikkatle yönetilmelidir.

Uzun bir süre önce, uygulama gizli dizilerini uygulama kod temelinin içindeki bir yapılandırma dosyasında depolamak yaygındır. .NET geliştiricileri *web.config* dosyasını fonla geri çekecektir. Basit hale getirme, parolaların kod ile birlikte ve güvenli bir şekilde tümleştirilmesi. Yaygın bir yanıltıcı, genel bir GIT deposuna gönderilirken dosyayı eklemek ve gizli dizileri dünya çapında ortaya çıkarmıştı.

Modern dağıtılmış uygulamalar oluşturmak için yaygın olarak kabul edilen bir metodolojide [Twelve-Factor uygulamasıdır](https://12factor.net/). İlke ve en iyi uygulamalar kümesini açıklar. Üçüncü etkeni, *yapılandırma ve parolaların kod tabanının dışında externalized olmasını önerir.*

Bu sorunu gidermek için .NET Core platformu, hassas verileri proje ağacının dışında bir fiziksel klasörde depolayan bir [gizli dizi Yöneticisi](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) özelliği içerir. Gizlilikler kaynak denetimi dışında olduğundan, bu özellik verileri şifrelemez. Yalnızca **geliştirme amacıyla** tasarlanmıştır.

Daha modern ve güvenli bir uygulama, **HashiCorp Kasası** veya **Azure Key Vault** gibi bir gizli dizi yönetim aracında gizli dizileri yalıtmak için kullanılır.  Bu araçlar, gizli dizileri dışarıda depolamanıza, ortamlarda kimlik bilgilerinin çeşitliliğine ve uygulama kodundan bunlara başvurmasına olanak tanır. Ancak, her aracın karmaşıklıkları ve öğrenme eğrisi vardır.

Davpr, gizli dizileri yönetmeyi kolaylaştıran bir yapı bloğu sunar.

## <a name="what-it-solves"></a>Ne çözdüğü

DAPR [gizli dizisi oluşturma bloğu](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) , gizli dizi ve gizli yönetim araçlarıyla çalışma karmaşıklığını soyutlar.

- Birleşik bir arabirim aracılığıyla temel alınan sıhhi tesisat 'yi gizler.
- Geliştirme ve üretim arasında değişebilen çeşitli *takılabilir* gizli depolama bileşenlerini destekler.
- Uygulamalar gizli depolama kitaplıklarında doğrudan bağımlılıklara gerek kalmaz.
- Geliştiriciler her gizli depolama hakkında ayrıntılı bilgi gerektirmez.

Davpr yukarıdaki kaygıların tümünü işler.

Gizli dizi erişiminin kimlik doğrulama ve yetkilendirme aracılığıyla güvenliği sağlanır. Yalnızca yeterli haklara sahip bir uygulama gizli anahtarlara erişebilir. Kubernetes 'te çalışan uygulamalar, yerleşik gizli dizi yönetim mekanizmasını da kullanabilir.

## <a name="how-it-works"></a>Nasıl çalışır?

Uygulamalar, gizli dizi oluşturma bloğunu iki şekilde kullanır:

- Doğrudan uygulama bloğundan gizli dizi alma.
- Bir Davpr bileşen yapılandırmasından dolaylı olarak bir gizli dizi başvurusu.

Parolaların doğrudan alınması ilk olarak ele alınmıştır. Bir Davpr bileşen yapılandırma dosyasından bir gizli dizi ile başvurulmaya, sonraki bir bölümde değinilmesi sağlanır.

Uygulama, gizli dizi yapı bloğu kullanılırken bir davpr sepet ile etkileşime girer. Sepet API 'sini kullanıma sunar. API, HTTP ya da gRPC ile çağrılabilir. HTTP API 'sini çağırmak için aşağıdaki URL 'YI kullanın:

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/<name>?<metadata>
```

URL aşağıdaki segmentleri içerir:

- `<dapr-port>` Davpr dışarıdan arabasının dinlediği bağlantı noktası numarasını belirtir.
- `<store-name>` Davpr gizli deposunun adını belirtir.
- `<name>` alınacak gizli dizi adını belirtir.
- `<metadata>` gizli anahtar için ek bilgi sağlar. Bu bölüm isteğe bağlıdır ve meta veri özellikleri gizli depolama başına farklılık gösterir. Meta veri özellikleri hakkında daha fazla bilgi için bkz. [GIZLILIKLER API başvurusu]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/)).

 > [!NOTE]
 > Yukarıdaki URL, HTTP veya gRPC 'yi destekleyen herhangi bir geliştirme platformunda kullanılabilen yerel bir Davpr API çağrısını temsil eder. .NET, Java ve Go gibi popüler platformlar kendi özel API 'Lerine sahiptir.

JSON yanıtı, gizli dizinin anahtarını ve değerini içerir.

Şekil 10-1, Davpr 'nin gizli API 'ler için bir isteği nasıl işlediğini gösterir:

![Davpr gizli API 'SI kullanılarak bir gizli dizi alma diyagramı.](media/secrets/secrets-flow.png)

**Şekil 10-1**. Davpr gizli API 'SI ile gizli dizi alma.

1. Hizmet, gizli deponun adı ve alınacak gizli anahtar ile birlikte, Davpr gizli anahtarını çağırır.
1. Davpr sepet, belirtilen gizli anahtarı gizli depolamadan alır.
1. Davpr sepet, gizli bilgileri hizmete geri döndürür.

Bazı gizli depolar, birden çok anahtar/değer çiftini tek bir gizli dizi içinde depolamayı destekler. Bu senaryolar için, yanıt, aşağıdaki örnekte olduğu gibi tek bir JSON yanıtında birden çok anahtar/değer çifti içerir:

```http
GET http://localhost:3500/v1.0/secrets/secret-store/interestRates?metadata.version_id=3
```

```json
{
  "tier1-percentage": "2.5",
  "tier2-percentage": "3.8",
  "tier3-percentage": "5.1"
}
```

Davpr gizli dizileri API 'SI, uygulamanın erişimi olan tüm gizli dizileri almak için de bir işlem sağlar:

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/bulk
```

## <a name="use-the-dapr-net-sdk"></a>Davpr .NET SDK 'sını kullanma

.NET geliştiricileri için, Davpr .NET SDK 'Sı, Davpr gizli yönetimini kolaylaştırır. Yöntemini göz önünde bulundurun `DaprClient.GetSecretAsync` . En az çabayla herhangi bir Davpr gizli deposundan doğrudan bir gizli dizi almanızı sağlar. Bir SQL Server veritabanı için bağlantı dizesi gizli dizisi getirmeye bir örnek aşağıda verilmiştir:

```csharp
var metadata = new Dictionary<string, string> { ["version_id"] = "3" };
Dictionary<string, string> secrets = await daprClient.GetSecretAsync("secret-store", "eshopsecrets", metadata);
string connectionString = secrets["customerdb"];
```

Yöntemi için bağımsız değişkenler `GetSecretAsync` şunları içerir:

- Davpr gizli deposu bileşeninin adı (' gizli-Store ')
- Alınacak gizli dizi (' eshopsecret ')
- İsteğe bağlı meta veri anahtar/değer çiftleri (' version_id = 3 ')

Yöntem bir sözlük nesnesi ile yanıt verir ve bir gizli dizi birden çok anahtar/değer çifti içerebilir. Yukarıdaki örnekte, adlı gizli dizinin `customerdb` bir bağlantı dizesi döndürecek şekilde koleksiyondan başvuruluyor.

Davpr .NET SDK 'Sı Ayrıca bir .NET yapılandırma sağlayıcısına de sahiptir. Belirtilen gizli dizileri temel [.NET Core Yapılandırma API](https://docs.microsoft.com/dotnet/core/extensions/configuration)'sine yükler. Çalışan uygulama daha sonra `IConfiguration` ASP.NET Core bağımlılık ekleme ' de kayıtlı sözlükten parolalara başvurabilir.

Gizli dizi yapılandırma sağlayıcısı, [Dapr.Extensions.Configurlama](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet paketinden kullanılabilir. Sağlayıcı, `Program.cs` bir ASP.NET Web API uygulamasında kayıtlı olabilir:  

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureAppConfiguration(config =>
        {
            var daprClient = new DaprClientBuilder().Build();
            var secretDescriptors = new List<DaprSecretDescriptor>
            {
                new DaprSecretDescriptor("eshopsecrets")
            };
            config.AddDaprSecretStore("secret-store", secretDescriptors, daprClient);
        })
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

Yukarıdaki örnek, `eshopsecrets` parolalar koleksiyonunu başlangıçta .NET yapılandırma sistemine yükler. Sağlayıcının kaydedilmesi için bir örneği gerekir ve bu `DaprClient` , Davpr sidecar üzerinde GIZLILIKLER API 'sini çağırır. Diğer bağımsız değişkenler, gizli deponun adını ve `DaprSecretDescriptor` gizli dizi adına sahip bir nesnesi içerir.

Yüklendikten sonra doğrudan uygulama kodundan gizli dizileri alabilirsiniz:

```csharp
public void GetCustomer(IConfiguration config)
{
    var connectionString = config["eshopsecrets"]["customerdb"];
}
```

## <a name="secret-store-components"></a>Gizli mağaza bileşenleri

Gizli dizi oluşturma bloğu birçok gizli depolama bileşenini destekler. Yazma sırasında, aşağıdaki gizli depolar kullanılabilir:

- Ortam Değişkenleri
- Yerel dosya
- Kubernetes gizli dizileri
- AWS gizli dizileri Yöneticisi
- Azure Key Vault
- GCP gizli Yöneticisi
- HashiCorp Kasası

> [!IMPORTANT]
> Ortam değişkenleri ve yerel dosya bileşenleri yalnızca geliştirme iş yükleri için tasarlanmıştır.

Aşağıdaki bölümlerde, gizli bir deponun nasıl yapılandırılacağı gösterilmektedir.

### <a name="configuration"></a>Yapılandırma

Bir Davpr bileşen yapılandırma dosyası kullanarak gizli bir mağaza yapılandırırsınız. Dosyanın tipik yapısı aşağıda gösterilmiştir:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: [component name]
  namespace: [namespace]
spec:
  type: secretstores.[secret store type]
  version: [secret store version]
  metadata:
  - name: [property name]
    value: [property value]
```

Tüm Davpr bileşen yapılandırma dosyaları `name` , isteğe bağlı bir değerle birlikte gerektirir `namespace` . Ayrıca, `type` `spec` bölümündeki alanı gizli depo bileşeni türünü belirtir. `metadata`Bölümdeki Özellikler gizli depolama alanı başına farklılık gösterir.

### <a name="indirectly-consume-dapr-secrets"></a>Dolaylı olarak Davpr gizli dizilerini kullanma

Bu bölümde daha önce bahsedildiği gibi uygulamalar, bileşen yapılandırma dosyalarında bunlara başvurarak gizli dizileri de kullanabilir. Durumu depolamak için Redsıs önbelleği kullanan bir [durum yönetimi bileşeni](state-management.md) düşünün:

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
    value: localhost:6379
  - name: redisPassword
    value: e$h0p0nD@pr
```

Yukarıdaki yapılandırma dosyası Redsıs sunucusuna bağlanmak için **düz metin** bir parola içerir. **Sabit kodlanmış** parolalar her zaman hatalı bir fikirdir. Bu yapılandırma dosyasını bir ortak depoya göndermek, parolayı kullanıma sunar. Parolayı gizli bir depoda depolamak bu senaryoyu önemli ölçüde iyileştirir.

Aşağıdaki örneklerde, birkaç farklı gizli mağaza kullanılarak bu gösterilmektedir.

### <a name="local-file"></a>Yerel dosya

Yerel dosya bileşeni, geliştirme senaryoları için tasarlanmıştır. Yerel dosya sisteminde bir JSON dosyası içinde gizli dizileri depolar. Adında bir örnek aşağıda verilmiştir `eshop-secrets.json` . Tek bir gizli dizi içerir: Redsıs için parola:

```json
{
  "eShopRedisPassword": "e$h0p0nD@pr"
}
```

Bu dosyayı `components` , Davpr uygulamasını çalıştırırken belirttiğiniz bir klasöre yerleştirebilirsiniz.

Aşağıdaki gizli depo yapılandırma dosyası JSON dosyasını gizli bir depo olarak tüketir. Ayrıca klasöre de yerleştirilir `components` :

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-local-secret-store
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secrets.json
  - name: nestedSeparator
    value: ":"
```

Bileşen türü `secretstore.local.file` . `secretsFile`Metadata öğesi, gizli dizi dosyasının yolunu belirtir.

> [!IMPORTANT]
> Bir gizli dizi dosyası yolu mutlak veya göreli bir yol olabilir. Göreli yol, uygulamanın başladığı klasörü temel alır. Örnekte, `components` klasörü .NET uygulamasını içeren dizinin bir alt klasörüdür.

Uygulama klasöründen, `components` yolu bir komut satırı bağımsız değişkeni olarak belirten Davpr uygulamasını başlatın:

```console
dapr run --app-id basket-api --components-path ./components dotnet run
```

> [!NOTE]
> Bu yukarıdaki örnek, şirket içinde barındırılan modda Davpr çalıştırmak için geçerlidir. Kubernetes barındırma için, birim bağlama kullanmayı düşünün.

`nestedSeparator`Bir Davpr yapılandırma dosyasında, BIR JSON hiyerarşisini *düzleştirmek* için bir karakter belirtir. Aşağıdaki kod parçacığını göz önünde bulundurun:

```json
{
    "redisPassword": "some password",
    "connectionStrings": {
        "customerdb": "some connection string",
        "productdb": "some connection string"
    }
}
```

Ayırıcı olarak bir iki nokta üst üste kullanarak, `customerdb` anahtarı kullanarak bağlantı dizesini alabilirsiniz `connectionStrings:customerdb` .

> [!NOTE]
> İki nokta üst üste `:` varsayılan ayırıcı değeridir.

Sonraki örnekte, bir durum yönetimi yapılandırma dosyası Redsıs sunucusuna bağlanmak için parolayı almak üzere yerel gizli dizi bileşenine başvurur:

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
    value: localhost:6379
  - name: redisPassword
    secretKeyRef:
      name: eShopRedisPassword
      key: eShopRedisPassword
auth:
  secretStore: eshop-local-secret-store
```

`secretKeyRef`Öğesi, parolayı içeren gizli dizi ile başvurur. Önceki *şifresiz metin* değerini değiştirir. Gizli dizi adı ve anahtar adı, `eShopRedisPassword` gizli dizi başvurusu. Gizli dizi yönetim bileşeninin adı `eshop-local-secret-store` `auth` meta veri öğesinde bulunur.

`eShopRedisPassword`Gizli dizi başvurusunda hem ad hem de anahtar için neden özdeş olduğunu merak ediyor olabilirsiniz. Yerel dosya gizli deposunda, gizli dizileri ayrı bir adla tanımlanmaz. Bu senaryo, Kubernetes gizli dizileri kullanılarak bir sonraki örnekte farklı olacaktır.

### <a name="kubernetes-secret"></a>Kubernetes gizli dizisi

Bu ikinci örnek, Kubernetes 'te çalışan bir Davpr uygulamasına odaklanır. Kubernetes 'in sunduğu standart gizli dizileri mekanizmasını kullanır. `kubectl`Parolayı içeren bir gizli dizi oluşturmak Için Kubernetes CLI () kullanın `eshop-redis-secret` :

```console
kubectl create secret generic eshopsecrets --from-literal=redisPassword=e$h0p0nD@pr -n eshop
```

Oluşturulduktan sonra, durum yönetimi için bileşen yapılandırma dosyasında gizli başvuruya başvurabilirsiniz:

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
      name: eshopsecrets
      key: redisPassword
auth:
  secretStore: kubernetes
```

`secretKeyRef`Öğesi, Kubernetes parolasının adını ve gizli anahtarı, `eshopsecrets` , ve ' ı belirtir `redisPassword` . `auth`Meta veri bölümü, Davpr 'Nin Kubernetes gizli anahtarları yönetim bileşenini kullanmasını söyler.

> [!NOTE]
> Auth, Kubernetes gizli dizileri kullanılırken varsayılan değerdir ve atlanabilir.

Bir üretim ayarında, parolalar genellikle otomatik bir CI/CD işlem hattının parçası olarak oluşturulur. Böylece, yalnızca yeterli izinlere sahip kişiler erişebilir ve gizli dizileri değiştirebilir. Geliştiriciler, parolaların gerçek değerini bilmeden yapılandırma dosyaları oluşturur.

### <a name="azure-key-vault"></a>Azure Key Vault

Sonraki örnek, gerçek dünyada bir üretim senaryosuna yöneliktir. Gizli depo olarak **Azure Key Vault** kullanır. Azure Key Vault, parolaların bulutta güvenli bir şekilde depolanmasını sağlayan yönetilen bir Azure hizmetidir.

Bu örneğin çalışması için aşağıdaki önkoşulların karşılanması gerekir:

- Azure aboneliğine yönetici erişimini güvenli hale getirdi.
- `eshopkv` `redisPassword` Redsıs sunucusuna bağlanmak için parolayı içeren adında bir gizli anahtar tutan adlı bir Azure Key Vault sağladınız.
- Azure Active Directory ' de [hizmet sorumlusu](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal) oluşturdunuz.
- Yerel dosya sistemine bu hizmet sorumlusu için bir x509 sertifikası yüklediniz (hem ortak hem de özel anahtar içeren).

> [!NOTE]
> Hizmet sorumlusu, bir Azure hizmetinin kimliğini doğrulamak için bir uygulama tarafından kullanılabilen bir kimliktir. Hizmet sorumlusu bir x509 sertifikası kullanır. Uygulama, kimlik doğrulaması için kimlik bilgisi olarak bu sertifikayı kullanır.

[Dadpr Azure Key Vault gizli dizi belgeleri](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/) , bir Key Vault ortamı oluşturmak ve yapılandırmak için adım adım yönergeler sağlar.

#### <a name="use-key-vault-when-running-in-self-hosted-mode"></a>Kendi kendine barındırılan modda çalışırken Key Vault kullan

Şirket içinde barındırılan modda Azure Key Vault tüketen aşağıdaki yapılandırma dosyası gerekir:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: eshopkv
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificateFile
    value : "azurekv-spn-cert.pfx"
```

Gizli depolama türü `secretstores.azure.keyvault` . `metadata`Key Vault erişimi yapılandırma öğesi aşağıdaki özellikleri gerektirir:

- , `vaultName` Azure Key Vault adını içerir.
- , `spnTenantId` Key Vault karşı kimlik doğrulaması yapmak için kullanılan hizmet sorumlusunun *Kiracı kimliğini* içerir.
- , `spnClientId` Key Vault göre kimlik doğrulaması yapmak için kullanılan hizmet sorumlusunun *uygulama kimliğini* içerir.
- , `spnCertificateFile` Key Vault karşı kimlik doğrulaması yapılacak hizmet sorumlusu için sertifika dosyasının yolunu içerir.

> [!TIP]
> Hizmet sorumlusu bilgilerini Azure portal veya Azure CLı 'dan kopyalayabilirsiniz.

Uygulama artık Redsıs parolasını Azure Key Vault alabilir.

#### <a name="use-key-vault-when-running-on-kubernetes"></a>Kubernetes üzerinde çalışırken Key Vault kullan

Davpr ve Kubernetes ile Azure Key Vault kullanmak ayrıca, Azure Key Vault için kimlik doğrulaması yapmak üzere bir hizmet sorumlusu gerektirir.

İlk olarak, kubectl CLı aracını kullanarak bir sertifika dosyası içeren bir *Kubernetes gizli* dizisi oluşturun:

```console
kubectl create secret generic [k8s_spn_secret_name] --from-file=[pfx_certificate_file_local_path] -n eshop
```

Komut iki komut satırı bağımsız değişkeni gerektirir:

- `[k8s_spn_secret_name]` , Kubernetes gizli deposundaki gizli addır.
- `[pfx_certificate_file_local_path]` x509 sertifika dosyasının yoludur.

Oluşturulduktan sonra gizli depolama bileşeni yapılandırma dosyasında Kubernetes gizli öğesine başvurabilirsiniz:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: [your_keyvault_name]
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificate
    secretKeyRef:
      name: [k8s_spn_secret_name]
      key: [pfx_certificate_file_local_name]
auth:
    secretStore: kubernetes
```

Bu noktada, Kubernetes 'de çalışan bir uygulama, Azure Key Vault redo parolasını alabilir.

> [!IMPORTANT]
> Hizmet sorumlusu için x509 sertifika dosyasını güvenli bir yerde tutmanız kritik öneme sahiptir. Bunu, kaynak kodu deposunun dışında iyi bilinen bir klasöre yerleştirmek en iyisidir. Yapılandırma dosyası daha sonra bu iyi bilinen klasörden sertifika dosyasına başvurabilir. Yerel bir geliştirme makinesinde, sertifikayı klasörüne kopyalamaktan sorumlu olursunuz. Otomatik dağıtımlar için, işlem hattı sertifikayı uygulamanın dağıtıldığı makineye kopyalar. Her ortam için farklı bir hizmet sorumlusu kullanmak en iyi uygulamadır. Bunun yapılması, bir GELIŞTIRME ortamından hizmet sorumlusunun bir ÜRETIM ortamındaki gizli dizileri erişimine engel olur.

Azure Kubernetes hizmeti 'nde (AKS) çalışırken, Azure Key Vault kimlik doğrulaması için bir [Azure yönetilen kimliği](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) kullanılması tercih edilir. Yönetilen kimlikler bu kitabın kapsamı dışındadır, ancak [Azure Key Vault Yönetilen kimlikler](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) belgeleriyle açıklanmıştır.

### <a name="scope-secrets"></a>Kapsam gizli dizileri

Gizli kapsamlar, uygulamanızın erişebileceği gizli dizileri denetlemenize olanak tanır. Kapsamları bir davpr sepet yapılandırma dosyasında yapılandırırsınız. [Davpr yapılandırma belgeleri](https://docs.dapr.io/operations/configuration/configuration-overview/) , parolaların kapsamını belirlemek için yönergeler sağlar.

Gizli kapsamlar içeren bir davpr sepet yapılandırma dosyasına bir örnek aşağıda verilmiştir:

```yml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  secrets:
    scopes:
      - storeName: eshop-azurekv-secret-store
        defaultAccess: allow
        deniedSecrets: ["redisPassword", "apiKey"]
```

Her gizli dizi için kapsam belirtirsiniz. Yukarıdaki örnekte, gizli depo olarak adlandırılmıştır `eshop-azurekv-secret-store` . Gizli dizi erişimini aşağıdaki özellikleri kullanarak yapılandırırsınız:

| Özellik         | Değer               | Açıklama                                                                                                                       |
|------------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `defaultAccess`  | `allow` veya `deny`   | Belirtilen gizli depodaki *Tüm* gizli dizi erişimine izin verir veya erişimi reddeder. Bu özellik varsayılan değeri ile isteğe bağlıdır `allow` . |
| `allowedSecrets` | Gizli anahtar listesi | Dizide belirtilen gizli dizileri erişilebilir olacaktır. Bu özellik isteğe bağlıdır.                                                     |
| `deniedSecrets`  | Gizli anahtar listesi | Dizide belirtilen gizli dizileri erişilebilir olmayacak. Bu özellik isteğe bağlıdır.                                                 |

`allowedSecrets`Ve `deniedSecrets` özellikleri `defaultAccess` özelliğinden önceliklidir. `defaultAccess: allowed`Ve bir liste belirtmeyi düşünün `allowedSecrets` . Bu durumda, uygulama tarafından yalnızca listedeki gizli anahtarlara `allowedSecrets` erişilebilir.

## <a name="reference-application-eshopondapr"></a>Başvuru uygulaması: Eshopondadpr

Eshopondadpr başvuru uygulaması, iki gizli dizi için gizli dizi derleme bloğunu kullanır:

- Redsıs önbelleğine bağlanmak için parola.
- Twilio SendGrid API 'sini kullanmak için API anahtarı. Uygulama, bir Davpr çıkış bağlaması ( [bağlamalar yapı taşı](bindings.md)bölümünde açıklandığı gibi) kullanarak e-posta göndermek Için twilo kullanır.

Docker Compose kullanarak uygulamayı çalıştırırken, **yerel dosya** gizli deposu kullanılır. Bileşen yapılandırma dosyası `eshop-secretstore.yaml` `dapr/components` Eshopondadpr deposunun klasöründe bulunur:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-secretstore
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secretstore.json
```

Yapılandırma dosyası, aynı klasörde bulunan yerel depo dosyasına başvurur `eshop-secretstore.json` :

```json
{
    "redisPassword": "**********",
    "sendgridAPIKey": "**********"
}
```

`components`Klasör komut satırında belirtilir ve davpr sepet kapsayıcısının içinde yerel bir klasör olarak bağlanır. `docker-compose.override.yml`Depo kökündeki, birim bağlama belirten bir kod parçacığı aşağıda verilmiştir:

```yaml
  ordering-backgroundtasks-dapr:
    command: ["./daprd",
      "-app-id", "ordering-backgroundtasks",
      "-app-port", "80",
      "-dapr-grpc-port", "50004",
      "-components-path", "/components",
      "-config", "/configuration/eshop-config.yaml"
      ]
    volumes:
      - "./dapr/components/:/components"
      - "./dapr/configuration/:/configuration"
```

> [!NOTE]
> Docker Compose geçersiz kılma dosyası çevresel özel yapılandırma değerlerini içerir.

`/components`Birim bağlama ve `--components-path` komut satırı bağımsız değişkeni `daprd` Başlangıç komutuna geçirilir.

Yapılandırıldıktan sonra diğer bileşen yapılandırma dosyaları gizli dizileri de başvurabilir. Gizli dizileri kullanan yayımla/abone ol bileşen yapılandırmasına bir örnek aşağıda verilmiştir:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: eshop
spec:
  type: pubsub.redis
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

Yukarıdaki örnekte, yerel redin deposu gizli dizi başvurusunda bulunmak için kullanılır.

## <a name="summary"></a>Özet

Davpr gizli dizi oluşturma bloğu, parolalar ve bağlantı dizeleri gibi hassas yapılandırma ayarlarının depolanması ve alınması için yetenekler sağlar. Gizli dizileri korur ve yanlışlıkla açıklanmalarını önler.

Yapı taşı birçok farklı gizli depolar destekler ve DAPR gizli API 'SI ile karmaşıklığını gizler.

Davpr .NET SDK, gizli dizileri `DaprClient` almak için bir nesne sağlar. Ayrıca .NET Core yapılandırma sistemine gizli diziler ekleyen bir .NET yapılandırma sağlayıcısı da içerir. Yüklendikten sonra .NET kodunuzda bu gizli dizileri kullanabilirsiniz.

Belirli gizli dizileri erişimi denetlemek için gizli kapsamları kullanabilirsiniz.

## <a name="references"></a>Başvurular

- [Twelve-Factor uygulamanın ötesinde](https://tanzu.vmware.com/content/blog/beyond-the-twelve-factor-app)

>[!div class="step-by-step"]
>[Önceki](observability.md) 
> [Sonraki](summary.md)

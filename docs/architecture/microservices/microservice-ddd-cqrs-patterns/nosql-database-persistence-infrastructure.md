---
title: NoSQL veritabanlarını bir kalıcılık altyapısı olarak kullanma
description: Kalıcılığı uygulamak için bir seçenek olarak, genel olarak NoSql veritabanlarının ve özellikle Azure Cosmos DB'nin kullanımını anlayın.
ms.date: 01/30/2020
ms.openlocfilehash: 9c51e48d82aa0cf0234275f09df43f7a654f0ca8
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988446"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Kalıcılık altyapısı olarak NoSQL veritabanlarını kullanma

Altyapı veri katmanınız için NoSQL veritabanlarını kullandığınızda, genellikle Entity Framework Core gibi bir ORM kullanmazsınız. Bunun yerine Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB veya Azure Depolama Tabloları gibi NoSQL altyapısı tarafından sağlanan API'yi kullanırsınız.

Ancak, bir NoSQL veritabanı, özellikle Azure Cosmos DB, CouchDB veya RavenDB gibi belge yönelimli bir veritabanı kullandığınızda, modelinizi DDD agregalarıyla tasarlama şekliniz, toplu köklerin, alt varlık sınıflarının ve değer nesne sınıflarının tanımlanması açısından EF Core'da bunu nasıl yapabileceğinize kısmen benzer. Ancak, sonuçta, veritabanı seçimi tasarımınızı etkileyecektir.

Belge yönelimli bir veritabanı kullandığınızda, json veya başka bir biçimde seri hale getirilmiş tek bir belge olarak bir agrega uygularsınız. Ancak, veritabanının kullanımı bir etki alanı modeli kodu açısından saydamdır. Bir NoSQL veritabanı kullanırken, kalıcılık ilişkisel olmadığından, varlık sınıflarını ve toplu kök sınıflarını kullanmaya devam emkişi kullanıyorsunuz, ancak EF Core'u kullanırken daha fazla esneklikle.

Aradaki fark, bu modeli nasıl devam ettirdiğinizdir. Etki alanı modelinizi, altyapı kalıcılığına agnostik olan POCO varlık sınıflarını temel alan olarak uyguladıysanız, ilişkiselden NoSQL'e kadar farklı bir kalıcılık altyapısına geçebilirsiniz gibi görünebilir. Ancak, bu hedef olmamalıdır. Farklı veritabanı teknolojilerinde her zaman kısıtlamalar ve dengeler vardır, bu nedenle ilişkisel veya NoSQL veritabanları için aynı modele sahip olamazsınız. Kalıcılık modellerini değiştirmek önemsiz bir görev değildir, çünkü işlemler ve kalıcılık işlemleri çok farklı olacaktır.

Örneğin, belge yönelimli bir veritabanında, bir toplu kökiçin birden çok alt koleksiyon özelliği olması tamamdır. İlişkisel bir veritabanında, EF'den union ALL SQL deyimi aldığınızdan, birden çok alt koleksiyon özelliğini sorgulamak kolayca en iyi duruma getirilmiş değildir. İlişkisel veritabanları veya NoSQL veritabanları için aynı etki alanı modeline sahip olmak basit değildir ve bunu yapmaya çalışmamalısınız. Modelinizi, verilerin her bir veritabanında nasıl kullanılacağını anlayarak tasarlamanız gerekir.

NoSQL veritabanları nı kullanırken bir yararı varlıkların daha denormalized olmasıdır, bu yüzden bir tablo eşleme ayarlamak değil. Etki alanı modeliniz ilişkisel bir veritabanı kullanırken daha esnek olabilir.

Etki alanı modelinizi agregalara göre tasarlarken, NoSQL'e ve belge yönelimli veritabanlarına geçmek ilişkisel bir veritabanı kullanmaktan daha kolay olabilir, çünkü tasarladığınız agregalar belge yönelimli bir veritabanındaki serileştirilmiş belgelere benzer. Sonra bu "çanta" bu toplam için ihtiyaç duyabileceğiniz tüm bilgileri ekleyebilirsiniz.

Örneğin, aşağıdaki JSON kodu, belge yönelimli bir veritabanı kullanırken bir sipariş toplamının örnek uygulamasıdır. Bu eShopOnContainers örnek uygulanan sipariş toplam benzer, ancak altında EF Core kullanmadan.

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Azure Cosmos DB ve yerli Cosmos DB API'ye giriş

[Azure Cosmos DB,](https://docs.microsoft.com/azure/cosmos-db/introduction) Görev açısından kritik uygulamalar için Microsoft'un genel olarak dağıtılmış veritabanı hizmetidir. Azure Cosmos DB tarafından [kullanıma hazır genel dağıtım](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), dünya çapında [aktarım hızı ve depolama için elastik ölçeklendirme](https://docs.microsoft.com/azure/cosmos-db/partition-data), 99. yüzdebirlik dilimde tek haneli milisaniyelik gecikme süreleri, [beş iyi tanımlanmış tutarlılık düzeyi](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) ve garantili yüksek kullanılabilirlik olanakları sağlanır ve bunların tamamı [sektör lideri SLA’lar](https://azure.microsoft.com/support/legal/sla/cosmos-db/) ile desteklenir. Azure Cosmos DB, şema ve dizin yönetimiyle ilgilenmenize gerek kalmadan [otomatik olarak verilerin dizinini oluşturur](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf). Çok modelli olan bu hizmet belge, anahtar-değer, grafik ve sütunlu veri modellerini destekler.

![Azure Cosmos DB genel dağıtımını gösteren diyagram.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

**Şekil 7-19**. Azure Cosmos DB genel dağıtımı

Azure Cosmos\# DB API tarafından kullanılacak toplamı uygulamak için bir C modeli kullandığınızda,\# toplam EF Core ile kullanılan C POCO sınıflarına benzer olabilir. Aradaki fark, aşağıdaki kodda olduğu gibi uygulama ve altyapı katmanlarından bunları kullanma nın yoludur:

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot's methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

Etki alanı modelinizle çalışma şekliniz, altyapı EF olduğunda etki alanı modeli katmanınızda kullanma şeklinize benzer olabileceğini görebilirsiniz. Toplam da tutarlılık, değişmezler ve doğrulamalar sağlamak için yine de aynı toplu kök yöntemlerini kullanıyorsunuz.

Ancak, modelinizi NoSQL veritabanında kalıcı olarak sağınızda, kod ve API, EF Core koduveya ilişkisel veritabanlarıyla ilgili diğer kodlarla karşılaştırıldığında önemli ölçüde değişir.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>MongoDB ve Azure Cosmos DB'yi hedefleyen .NET kodunu uygulayın

### <a name="use-azure-cosmos-db-from-net-containers"></a>.NET kapsayıcılarından Azure Cosmos DB'yi kullanma

Azure Cosmos DB veritabanlarına diğer .NET uygulamalarında olduğu gibi kapsayıcılarda çalışan .NET kodundan erişebilirsiniz. Örneğin, eShopOnContainers'daki Locations.API ve Marketing.API mikro hizmetleri Azure Cosmos DB veritabanlarını kullanabilmeleri için uygulanır.

Ancak, Docker geliştirme ortamı açısından Azure Cosmos DB'de bir sınırlama vardır. Yerel bir geliştirme makinesinde çalıştırılabilen bir şirket içi [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) olsa da, yalnızca Windows'u destekler. Linux ve macOS desteklenmez.

Ayrıca docker bu emülatör çalıştırmak için imkanı var, ama sadece Windows Kapsayıcılar değil, Linux Containers ile. Uygulamanız Linux kapsayıcıları olarak dağıtılırsa, şu anda Aynı anda Docker for Windows'da Linux ve Windows Kapsayıcıları dağıtamadığınız için, geliştirme ortamı için ilk engel dir. Dağıtılan tüm kapsayıcılar Linux veya Windows için olmalıdır.

Bir geliştirme/test çözümü için ideal ve daha basit dağıtım, veritabanı sistemlerinizi özel kapsayıcılarınizle birlikte kapsayıcı olarak dağıtabilmektir, böylece geliştirme/test ortamlarınız her zaman tutarlıdır.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Yerel dev/test Linux/Windows kapsayıcıları ve Azure Cosmos DB için MongoDB API'yi kullanın

Cosmos DB veritabanları .NET için MongoDB API yanı sıra yerli MongoDB tel protokolü destekler. Bu, varolan sürücüleri kullanarak, MongoDB için yazılmış uygulamanızın artık Şekil 7-20'de gösterildiği gibi Cosmos DB ile iletişim kurabileceği ve MongoDB veritabanları yerine Cosmos DB veritabanlarını kullanabileceği anlamına gelir.

![Cosmos DB'nin .NET ve MongoDB tel protokolünü desteklediğini gösteren diyagram.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

**Şekil 7-20**. Azure Cosmos DB'ye erişmek için MongoDB API ve protokolünü kullanma

[MongoDB Docker görüntü](https://hub.docker.com/r/_/mongo/) Docker Linux kapları ve Docker Windows kapları destekleyen bir çok kemerli görüntü olduğundan Bu Linux kapları ile Docker ortamlarda kavramların kanıtı için çok uygun bir yaklaşımdır.

Aşağıdaki resimde gösterildiği gibi, MongoDB API kullanarak, eShopOnContainers yerel geliştirme ortamı için MongoDB Linux ve Windows kapsayıcıları destekler ama sonra, sadece [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)işaret Ederek ölçeklenebilir, PaaS bulut çözümü taşıyabilirsiniz.

![EShopOnContainers Konum microservice cosmos DB veya Mongo DB kullanabilirsiniz gösteren diyagram.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

**Şekil 7-21**. üretim için dev-env veya Azure Cosmos DB için MongoDB kapları kullanan eShopOnContainers

Azure Cosmos DB üretimi, Azure bulutunda PaaS ve ölçeklenebilir bir hizmet olarak çalışır.

Özel .NET Core kapsayıcılarınız yerel bir geliştirme Docker ana bilgisayarda çalıştırılabilir (Windows 10 makinesinde Docker kullanıyor) veya Azure AKS veya Azure Hizmet Kumaşı'ndaki Kubernetes gibi bir üretim ortamına dağıtılabilir. Bu ikinci ortamda, üretimdeki verileri işlemek için bulutta Azure Cosmos DB kullandığınızdan, yalnızca .NET Core özel kapsayıcılarını dağıtamaz, ancak MongoDB kapsayıcısını dağıtmazsınız.

MongoDB API'yi kullanmanın açık bir yararı, çözümünüzünüzün her iki veritabanı motorunda, MongoDB'de veya Azure Cosmos DB'de çalıştırılamasıdır, bu nedenle farklı ortamlara geçişler kolay olmalıdır. Ancak, bazen belirli bir veritabanı altyapısının özelliklerinden tam olarak yararlanmak için yerel bir API (yani yerel Cosmos DB API) kullanmak faydalıdır.

Bulutta Sadece MongoDB ile Cosmos DB'yi kullanmak arasında daha fazla karşılaştırma için [bu sayfada Azure Cosmos DB kullanmanın avantajlarına](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)bakın.

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Üretim uygulamaları için yaklaşımınızı analiz edin: MongoDB API vs Cosmos DB API

eShopOnContainers'da MongoDB API kullanıyoruz çünkü önceliğimiz Azure Cosmos DB ile de çalışabilen bir NoSQL veritabanı nı kullanarak tutarlı bir geliştirme/test ortamına sahip olmaktı.

Ancak, üretim uygulamaları için Azure'da Azure Cosmos DB'ye erişmek için MongoDB API'sini kullanmayı planlıyorsanız, Azure Cosmos DB veritabanlarına erişmek için MongoDB API'sini kullanırken yerel Azure Cosmos DB API'sini kullanmaya kıyasla yetenek ve performans farklılıklarını çözümlemeniz gerekir. Benzer se, MongoDB API'yi kullanabilirsiniz ve aynı anda iki NoSQL veritabanı altyapısını destekleme avantajına ulaşabilirsiniz.

MongoDB Azure Hizmeti ile [MongoDB](https://www.mongodb.com/scale/mongodb-azure-service)kümelerini Azure bulutundaki üretim veritabanı olarak da kullanabilirsiniz. Ancak bu, Microsoft tarafından sağlanan bir PaaS hizmeti değildir. Bu durumda Azure, MongoDB'den gelen bu çözümü barındırıyor.

Temel olarak, bu sadece bir feragat her zaman Azure Cosmos DB karşı MongoDB API kullanmamalısınız belirten, biz Linux kapsayıcılar için uygun bir seçim olduğu için eShopOnContainers yaptığı gibi. Karar, üretim uygulamanız için yapmanız gereken özel gereksinimlere ve testlere dayanmalıdır.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kod: .NET Core uygulamalarında MongoDB API'yi kullanın

.NET için MongoDB API, aşağıdaki şekilde gösterilen Locations.API projesinde olduğu gibi projelerinize eklemeniz gereken NuGet paketlerini temel alır.

![MongoDB NuGet paketlerindeki bağımlılıkların ekran görüntüsü.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

**Şekil 7-22**. MongoDB API NuGet bir .NET Core projesinde referansları alın

Aşağıdaki bölümlerdeki kodu inceleyelim.

#### <a name="a-model-used-by-mongodb-api"></a>MongoDB API tarafından kullanılan bir model

İlk olarak, uygulamanızın bellek alanında veritabanından gelen verileri tutacak bir model tanımlamanız gerekir. İşte eShopOnContainers konumlar için kullanılan modelin bir örneği.

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList)
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

MongoDB NuGet paketlerinden gelen birkaç öznitelik ve tür olduğunu görebilirsiniz.

NoSQL veritabanları genellikle ilişkisel olmayan hiyerarşik verilerle çalışmak için çok uygundur. Bu örnekte, özellikle coğrafi konumlar için yapılmış MongoDB `GeoJson2DGeographicCoordinates`türleri kullanıyoruz, gibi.

#### <a name="retrieve-the-database-and-the-collection"></a>Veritabanını ve koleksiyonu alma

eShopOnContainers olarak, aşağıdaki kod gibi, veritabanı ve MongoCollections almak için kodu uygulamak özel bir veritabanı bağlamı oluşturduk.

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }
}
```

#### <a name="retrieve-the-data"></a>Verileri alma

Web API denetleyicileri veya özel Depolar uygulaması gibi C# kodunda, MongoDB API üzerinden sorgu yaparken aşağıdakilere benzer kod yazabilirsiniz. Nesnenin `_context` önceki `LocationsContext` sınıfın bir örneği olduğunu unutmayın.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>MongoDB bağlantı dizesi için docker-compose.override.yml dosyasında env-var kullanın

Bir MongoClient nesnesi oluştururken, tam olarak doğru `ConnectionString` veritabanını gösteren parametre olan temel bir parametre gerekir. eShopOnContainers durumunda, bağlantı dizesi yerel bir MongoDB Docker kapsayıcısına veya bir "üretim" Azure Cosmos DB veritabanına işaret edebilir.  Bu bağlantı dizesi, aşağıdaki yml kodunda olduğu gibi docker-compose veya Visual Studio ile dağıtılırken kullanılan `docker-compose.override.yml` dosyalarda tanımlanan ortam değişkenlerinden gelir.

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations-api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}

```

`ConnectionString` Ortam değişkeni şu şekilde çözülür: `ESHOP_AZURE_COSMOSDB` Genel değişken `.env` dosyada Azure Cosmos DB bağlantı dizesiyle tanımlanırsa, buluttaki Azure Cosmos DB veritabanına erişmek için bu değişkeni kullanır. Tanımlanmamışsa, `mongodb://nosqldata` değeri alır ve geliştirme MongoDB konteyner kullanır.

Aşağıdaki kod, `.env` eShopOnContainers'da uygulandığı gibi Azure Cosmos DB bağlantı dizesi global ortam değişkenine sahip dosyayı gösterir:

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

ESHOP_AZURE_COSMOSDB hattını açıklamamayı ve Azure portalından elde edilen Azure Cosmos DB bağlantı dizenizi, [MongoDB uygulamasını Azure Cosmos DB'ye](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)bağlayın'da açıklandığı gibi güncelleyin.

`ESHOP_AZURE_COSMOSDB` Genel değişken boşsa, yani `.env` dosyada yorumlanırsa, kapsayıcı varsayılan bir MongoDB bağlantı dizesini kullanır. Bu bağlantı dizesi, aşağıdaki .yml kodunda gösterildiği gibi docker-compose dosyasında adı verilen `nosqldata` ve tanımlanan eShopOnContainers'da dağıtılan yerel MongoDB kapsayıcısını işaret ediyor:

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a>Ek kaynaklar

- **NoSQL veritabanları için belge verilerini modelleme** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon' u. İdeal etki alanı odaklı tasarım agrega deposu?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Azure Cosmos DB'ye Giriş: MongoDB için API**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB: .NET ve Azure portalı ile bir MongoDB API web uygulaması oluşturun**  \
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- **Yerel geliştirme ve test için Azure Cosmos DB Emülatörü'ni kullanın**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Bir MongoDB uygulamasını Azure Cosmos DB'ye bağlayın**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Cosmos DB Emülatör Docker görüntü (Windows Konteyner)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **MongoDB Docker görüntüsü (Linux ve Windows Container)**  \
  <https://hub.docker.com/_/mongo/>

- **MongoChef'i (Studio 3T) Azure Cosmos DB ile kullanın: MongoDB hesabı için API**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Önceki](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[Sonraki](microservice-application-layer-web-api-design.md)

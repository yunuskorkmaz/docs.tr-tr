---
title: NoSQL veritabanı olarak Kalıcılık altyapısı kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | NoSQL veritabanı olarak Kalıcılık altyapısı kullanma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: cf43f9914a05c2745f914a6e36fcab13fb7feffa
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106651"
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a>NoSQL veritabanı olarak Kalıcılık altyapısı kullanma

NoSQL veritabanları için altyapı veri katmanını kullandığınızda, Entity Framework Çekirdek gibi bir ORM genellikle kullanmayın. Bunun yerine Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB veya Azure depolama tabloları gibi NoSQL altyapısı tarafından sağlanan API kullanın.

Özellikle bir belge yönelimli veritabanı Azure Cosmos DB, CouchDB veya RavenDB, gibi bir NoSQL veritabanı kullandığınızda ancak modelinizi DDD toplamalar tasarlayın nasıl EF çekirdek gelince tanımlaması için bunu yapabilirsiniz için kısmen benzer yoludur Birleşik kökleri, alt sınıflar ve değer nesne sınıfları. Ancak, veritabanı seçimi tasarımınızda nihayetinde etkiler.

Bir belge yönelimli veritabanı kullandığınızda, JSON veya başka bir biçimde serileştirilmiş tek bir belge olarak bir toplama uygulayın. Ancak, bir etki alanı modeli kod açısından bakıldığında veritabanının kullanılmasını saydamdır. Bir NoSQL veritabanı kullanırken, sınıflar ve birleşik kök sınıfları kullanmaya devam ancak EF çekirdek çünkü kullanırken'den daha fazla esneklik Kalıcılık ilişkisel değil.

Bu modelin nasıl kalıcı olarak farktır. POCO varlık sınıflara göre etki alanı modeli uygulanırsa, farklı Kalıcılık altyapısına bile NoSQL ilişkisel taşıma gibi altyapı Kalıcılık belirsiz onu görünebilir. Ancak, amacınız olmamalıdır. Her zaman kısıtlamaları farklı veritabanlarındaki itme, geri için aynı modeline sahip mümkün olmayacak şekilde ilişkisel veya NoSQL veritabanı. İşlemler ve sürdürme işlemleri çok farklı olacağından Kalıcılık modelleri değiştirme Önemsiz, olmayacaktır.

Örneğin, bir belge yönelimli veritabanında birden çok alt koleksiyon özellikleri bir toplama kökü için sorun değildir. Bir birleşim tüm SQL deyimi EF geri alma ilişkisel bir veritabanında birden çok alt koleksiyon özellikleri sorgulama awful, çünkü. İlişkisel veritabanları veya NoSQL veritabanları için aynı etki alanı modeline sahip basit değildir ve denemek. Gerçekten anlayarak, her bir veritabanı içinde kullanılacak verileri nasıl gittiğini modelinizi tasarlamak sahip.

Bir tablo eşleme ayarlamayın NoSQL veritabanlarını kullanırken bir avantajı varlıkları daha Normalleştirilmemiş olduğundan. Etki alanı modeli ilişkisel veritabanı kullanırken daha fazla esnek olabilir.

Ne zaman için NoSQL taşıma etki alanı modelinizi toplamalarda, tasarım ve tasarım toplamalar benzer olduğundan belge yönelimli veritabanları ilişkisel veritabanı kullanmaktan daha kolay olabilir bir belge yönelimli veritabanı belgelerde seri. Ardından bu "paketler" içinde bu toplama için gerekebilecek tüm bilgiler içerebilir.

Örneğin, aşağıdaki JSON kodunu bir örnek bir sipariş toplama belge yönelimli bir veritabanı kullanılırken uygulamasıdır. Biz eShopOnContainers örnekteki ancak EF çekirdek altında kullanmadan uygulandığı sırayı toplama benzer.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Azure Cosmos DB ve yerel Cosmos DB API giriş

[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) görev açısından kritik uygulamalar için Microsoft'un Genel dağıtılmış veritabanı hizmetidir. Azure Cosmos DB sağlar [anahtar teslim genel dağıtım](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [üretilen iş ve depolama esnek ölçeklendirme](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) 99, dünya çapında, tek basamaklı milisaniyelik gecikme [beş iyi tanımlanmış tutarlılık düzeylerini](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), yüksek oranda kullanılabilirlik, tarafından yedeklenen tüm garanti [endüstri lideri SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [verileri otomatik olarak dizinler](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) gerektirmeden şema ve dizin yönetimi ile ilgilidir. Birden çok model ve belge, anahtar-değer, grafik ve sütunlu veri modelleri destekler.

![](./media/image19.1.png) Şekil 9-19. Azure Cosmos DB genel dağıtım

Bir C kullandığınızda\# Azure Cosmos DB API'si tarafından toplama kullanılacak toplama uygulamak için model C benzer olabilir\# EF çekirdek ile kullanılan POCO sınıflar. Aşağıdaki kod olduğu gibi uygulama ve altyapı katmanlardan kullanılacakları şekilde fark vardır:

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
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
orderAggregate.AddOrderItem(orderItem2);
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

Etki alanı modeliyle çalışacak şekilde benzer altyapı EF olduğunda, etki alanı modeli katmanda kullandığınız şekilde olabileceğini görebilirsiniz. Hala tutarlılık, invariants ve toplama içinde doğrulamaları emin olmak için aynı toplama kök yöntemlerini kullanın.

Ancak, ne zaman, modelinizi NoSQL veritabanı, kod ve önemli ölçüde EF çekirdek kodu karşılaştırıldığında API değişiklik veya ilişkisel veritabanları için ilgili başka bir kod kalıcı olmasını sağlar.

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a>.NET kodu MongoDB ve Azure Cosmos DB hedefleyen uygulama

### <a name="using-azure-cosmos-db-from-net-containers"></a>Azure Cosmos DB'den .NET kapsayıcıları kullanma

Diğer bir .NET uygulamasından gibi kapsayıcılara çalışan .NET kodundan Azure Cosmos DB veritabanları erişebilir. Örneğin, Azure Cosmos DB veritabanları tüketebileceği şekilde eShopOnContainers Locations.API ve Marketing.API mikro hizmetler uygulanır.

Ancak, açısından bir Docker geliştirme ortamı Azure Cosmos veritabanı bir sınırlama yoktur. Bir şirket içi olduğunda bile [Azure Cosmos DB öykünücüsü](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) kullanabilirsiniz (örneğin, bir bilgisayar) yerel geliştirme makinede çalıştırmak, geç 2017 yalnızca Windows, Linux değil destekliyorsa. 

Ayrıca bu öykünücüsü Docker, ancak yalnızca Windows kapsayıcıları çalıştırmak için olasılığı vardır, not ile Linux kapsayıcıları. Uygulamanızı Linux kapsayıcılar olarak bu yana, şu anda dağıtılırsa, geliştirme ortamı için bir başlangıç handicap, Linux ve Windows kapsayıcıları için Docker Windows'da aynı anda dağıtamazsınız. Dağıtılan ya da tüm kapsayıcıları Windows veya Linux için olması gerekir.  

İdeal ve daha kolay bir geliştirme ve test çözümü için geliştirme ve test ortamları her zaman tutarlı şekilde veritabanı sistemlerinizi özel kapsayıcılarınızı birlikte kapsayıcı olarak dağıtabilmesi için dağıtımıdır.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Yerel geliştirme ve test Linux/Windows kapsayıcıları artı Azure Cosmos DB için MongoDB API kullanın

Cosmos DB veritabanları yerel MongoDB kablo protokolü yanı sıra .NET API MongoDB destekler. MongoDB için yazılmış uygulamanızı mevcut sürücüleri kullanarak artık Cosmos DB ile iletişim kurmak ve Cosmos DB veritabanları MongoDB veritabanı yerine, Şekil 9-20'de gösterildiği gibi kullanın. Bu anlamına gelir.

![](./media/image19.2.png) Şekil 9-20. MongoDB API ve protokolü kullanarak Azure Cosmos DB erişmek için

Bunun nedeni Linux kapsayıcılarla Docker ortamlarda kavramları kanıtı için çok uygun bir yaklaşım, [MongoDB Docker görüntü](https://hub.docker.com/r/_/mongo/) Docker Linux kapsayıcıları ve Docker Windows kapsayıcıları destekler çok yay bir görüntü.

9-21, görüntüde gösterildiği gibi MongoDB API'sini kullanarak eShopOnContainers yerel geliştirme ortamı için MongoDB Linux ve Windows kapsayıcıları destekler, ancak daha sonra bir biçimde ölçeklendirilebilir, taşıyabilirsiniz PaaS çözümü olarak Azure Cosmos DB tarafından yalnızca bulut [değiştirme Azure Cosmos Veritabanına işaret edecek şekilde MongoDB bağlantı dizesi](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account). 

![](./media/image20-bis.png) Şekil 9-21. eShopOnContainers üretim için geliştirme env ya da Azure Cosmos DB için MongoDB kapsayıcıları kullanma

Üretim Azure Cosmos DB Azure'un bulutta bir PaaS ve ölçeklenebilir hizmet olarak çalışır.

Özel .NET Core kapsayıcıları (Windows için Docker bir Windows 10 makinede kullanarak) bir yerel geliştirme Docker ana bilgisayarda çalıştırabilir veya Azure AKS veya Azure Service Fabric Kubernetes gibi bir üretim ortamına dağıtılır. Bu ikinci bir ortamda, yalnızca .NET çekirdeği özel kapsayıcılar ancak MongoDB kapsayıcı Azure Cosmos DB bulutta üretim verileri işlemek için kullanacağınızı beri dağıtımı.

MongoDB API kullanımının Temizle nedenle geçişler farklı ortamlar için kolay olmalıdır, çözümünüzün her iki veritabanı altyapıların, MongoDB ya da Azure Cosmos DB çalıştırabilir avantajdır. Ancak, bazen onu belirli Veritabanı Altyapısı'nın özelliklerinden tam anlamıyla yararlanabilmek için (yani yerel Cosmos DB API) yerel bir API kullanmak için faydalı olur.

Yalnızca bulutta MongoDB Cosmos DB karşı kullanarak arasında daha fazla karşılaştırma için bkz [bu sayfada Azure Cosmos DB kullanmanın yararları](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction). 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Üretim uygulamaları için durum yaklaşımınızı analiz: MongoDB API vs. Cosmos DB API

Bizim öncelik Azure Cosmos DB ile de işe yarayabilir bir NoSQL veritabanı kullanarak tutarlı geliştirme ve test ortamı için temelde olduğundan eShopOnContainers biz MongoDB API kullanıyorsunuz.

Ancak, üretim uygulamaları için Azure Cosmos Azure DB'de erişmek için MongoDB API kullanmak planlama, özellikleri ve performansı farklılıkları yerel kullanmaya kıyasla Azure Cosmos DB veritabanlarına erişim için MongoDB API'si kullanılırken çözümlemeniz gerekir, Azure Cosmos DB API. Benzer ise MongoDB API'sini kullanabilirsiniz ve aynı anda iki NoSQL veritabanı altyapıları destekleme yararı alın. 

Azure'nın bulutta üretim veritabanı olarak Mongodb'yi kümeleri kullanabilirsiniz çok, ile [MongoDB Azure hizmet](https://www.mongodb.com/scale/mongodb-azure-service). Ancak, Microsoft tarafından sağlanan bir PaaS hizmeti değil. Bu durumda, Azure adresinden gelen bu çözüm yalnızca barındırıyor.

Temel olarak, yalnızca Linux kapsayıcıları için kullanışlı bir seçim olduğundan içinde eShopOnContainers yaptığımız gibi Azure Cosmos DB karşı API MongoDB her zaman kullanmamanız belirten bir bildirim budur. Karar belirli gereksinimleri ve üretim uygulamanız için gerçekleştirmeniz gereken testleri dayanmalıdır.  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a>Kod: MongoDB API .NET Core uygulamalarında kullanma

.NET için API MongoDB Şekil 9-22'de gösterilen Locations.API gibi projelerinizi eklemeniz gerekir NuGet paketlerini temel alır.

![](./media/image21-bis.png) Şekil 9-22. .NET Core projede başvuruları MongoDB API NuGet paketleri

Şimdi aşağıdaki bölümlerde kodda araştırın.

#### <a name="a-model-used-by-mongodb-api"></a>MongoDB API tarafından kullanılan bir modeli

İlk olarak, uygulamanızın bellek alanı veritabanından gelen veriler tutacak bir model tanımlamanız gerekir. EShopOnContainers konumları için kullanılan modelle bir örneği burada verilmiştir.

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

Birkaç öznitelikleri ve MongoDB NuGet paketleri gelen türleri görebilirsiniz.

NoSQL veritabanları genellikle ilişkisel olmayan hiyerarşik verilerle çalışmak için oldukça uygundur. Bu örnekte, MongoDB türleri expecially gibi coğrafi konumları için yapılan kullanıyoruz `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Veritabanı ve koleksiyonu alma

Burada biz veritabanı ve aşağıdaki kodu olduğu gibi MongoCollections almak için kodu uygulayan bir özel veritabanı bağlamı eShopOnContainers içinde oluşturduk.

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

#### <a name="retrieve-the-data"></a>Veri alma

C# kod, Web API denetleyicilerinin veya özel depoları uygulama gibi benzer bir kod şu şekilde MongoDB API aracılığıyla sorgulanırken yazabilirsiniz. Unutmayın `_context` nesnesidir önceki örneği `LocationsContext` sınıfı.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>MongoDB bağlantı dizesi için docker compose.override.yml dosyasında env var kullanın

MongoClient nesnesi oluşturulurken, tam olarak olan temel bir parametre gereken `ConnectionString` sağ veritabanına işaret eden parametresi. EShopOnContainers söz konusu olduğunda bağlantı dizesi yerel MongoDB Docker kapsayıcısı veya "üretim" Azure Cosmos DB veritabanına işaret edebilir.  Tanımlanan ortam değişkenleri bağlantı dizesini geldiği `docker-compose.override.yml` docker-compose ya da Visual Studio ile olduğu gibi aşağıdaki yml kod dağıtırken kullanılan dosyaları.

```yml
# docker-compose.override.yml
version: '3'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

`ConnectionString` Ortam değişkeni bu şekilde çözümlendi: varsa `ESHOP_AZURE_COSMOSDB` genel değişkeni tanımlanmış `.env` dosya Azure Cosmos DB bağlantı dizesi ile onu bulutta Azure Cosmos DB veritabanına erişmek için kullanır. 

Aşağıdaki kodda gösterildiği `.env` eShopOnContainers içinde uygulandığı şekilde Azure Cosmos DB bağlantı dizesi genel ortam değişkeni'ile dosya:

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

İçinde Azure portalından alınan Azure Cosmos DB bağlantı dizesi ile açıklanan güncelleştirmeyi ve ESHOP_AZURE_COSMOSDB satırı açıklamadan kaldırmasına [Azure Cosmos DB MongoDB uygulamaya bağlama](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).

Varsa `ESHOP_AZURE_COSMOSDB` genel değişkeni, out olarak geçersiz kılınan, yani boş olduğundan, `.env` kapsayıcı adlandırılaneShopOnContainersdağıtılanyerelMongoDBkapsayıcıişaretedenbirvarsayılanMongoDBbağlantıdizesikullanıyorsa,dosya`nosql.data`aşağıdaki .yml kodda gösterildiği gibi. 

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Belge verileri NoSQL veritabanları için modelleme**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)

-   **Vaughn Vernon. Ideal etki alanı tabanlı tasarım toplama deposu?**
    [*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Azure Cosmos DB giriş: API MongoDB için** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)

-   **Azure Cosmos DB: .NET ve Azure portal ile bir MongoDB API web uygulaması oluşturma** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )

-   **Yerel geliştirme ve sınama için Azure Cosmos DB öykünücüsünü kullanma** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)

-   **Azure Cosmos DB MongoDB uygulamaya bağlama** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)

-   **Cosmos DB öykünücüsü Docker görüntünün (Windows kapsayıcısı)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)

-   **MongoDB Docker görüntünün (Linux ve Windows kapsayıcı)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)

-   **Bir Azure Cosmos DB ile MongoChef (Studio 3T) kullanın: API MongoDB hesabı** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)


>[!div class="step-by-step"]
[Önceki](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[sonraki](microservice-application-layer-web-api-design.md)

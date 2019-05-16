---
title: NoSQL veritabanlarını bir kalıcılık altyapısı olarak kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Genel ve Azure Cosmos DB NoSql veritabanlarının kullanımını özellikle kalıcılığı uygulamak için bir seçenek olarak anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 023904319651ec91000ff036850c773f66d1a267
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644463"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>NoSQL veritabanlarını bir Kalıcılık altyapısı olarak kullanma

Altyapı veri katmanınız için NoSQL veritabanları kullandığınızda, Entity Framework Core gibi bir ORM genellikle kullanmayın. Bunun yerine Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB veya Azure depolama tabloları gibi NoSQL altyapısı tarafından sağlanan API kullanın.

Özellikle bir belge yönelimli veritabanı gibi Azure Cosmos DB, CouchDB veya RavenDB, bir NoSQL veritabanı kullandığınızda, ancak modelinizi DDD toplamalar tasarlayın nasıl EF Core kimliği ilgili bunu yapabilirsiniz için kısmen benzer yoludur Toplama kökleri, alt varlık sınıfları ve değer nesne sınıfları. Ancak sonuç olarak, veritabanı seçimi tasarımınızda etkiler.

Bir belge yönelimli veritabanı kullandığınızda, JSON veya başka bir biçimde seri hale getirilmiş bir tek belge olarak toplama uygulayın. Ancak, veritabanı kullanımını bir etki alanı modeli kodu bakıldığında saydamdır. Bir NoSQL veritabanı kullanırken, varlık sınıfları ve toplama kök sınıfları kullanmaya devam ancak EF Core için kullanırken değerinden daha esnek Kalıcılık ilişkisel değil.

Bu modelin nasıl kalıcı olarak farktır. Etki alanı modeliniz POCO varlık sınıflarında uygulanması durumunda bile gelen ilişkisel, NoSQL için bir farklı Kalıcılık altyapısı için taşıyabilirsiniz gibi altyapı Kalıcılık için dilden bağımsız, görünebilir. Ancak, amacınız olmamalıdır. Her zaman kısıtlamaları ve farklı veritabanı teknolojileri dezavantajlarına sahip aynı modelin mümkün olmayacak şekilde ilişkisel veya NoSQL veritabanları. İşlemler ve Kalıcılık işlemleri çok farklı olacağı için Kalıcılık modelleri değiştirme çok basit bir görev değil.

Örneğin, bir belge yönelimli veritabanı, bir toplama kök birden çok alt koleksiyonu özelliklerine sahip olmayı sorun değildir. Bir birleşim tüm SQL deyimi EF geri dönmek için ilişkisel bir veritabanında birden çok alt koleksiyon özelliklerini sorgulama kolayca, getirilmemiştir. İlişkisel veritabanları veya NoSQL veritabanları için aynı etki alanı modeli sahip basit değildir ve bunu yapmanın denememelisiniz. Her bir veritabanı içinde kullanılacak veriler nasıl kolaylaştıracağını anlamak modelinizi tasarlamak olması.

NoSQL veritabanlarını kullanırken bir avantajı varlıkları daha normalleştirilmişlikten çıkarılmış bir tablo eşleme ayarlanmamış olduğundan. Etki alanı modeliniz ilişkisel bir veritabanı kullanırken değerinden daha esnek olabilir.

Ne zaman NoSQL için taşıma etki alanı modeliniz toplamalarda, tasarım ve tasarım toplamalar benzer çünkü belge yönelimli veritabanı ilişkisel bir veritabanı kullanmaktan daha kolay olabilir bir belge yönelimli veritabanı belgelerine seri hale getirilmiş. Ardından, bu toplama için ihtiyacınız olabilecek tüm bilgileri bu "paketleri" ekleyebilirsiniz.

Örneği için aşağıdaki JSON kodunu bir örnek bir sipariş toplama bir belge yönelimli veritabanı kullanılırken uygulamasıdır. Hizmetine örnek, ancak EF Core altında kullanmadan uyguladık sırasını toplama benzerdir.

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

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) görev açısından kritik uygulamalar için Microsoft'un Global olarak dağıtılmış veritabanı hizmetidir. Azure Cosmos DB sağlar [anahtar teslim küresel dağıtım](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [aktarım hızı ve depolama esnek ölçeklendirme](https://docs.microsoft.com/azure/cosmos-db/partition-data) 99. yüzdebirlik dilimde dünya, tek basamaklı milisaniyelik gecikme süreleri [beş iyi tanımlanmış tutarlılık düzeyi](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)ve garantili yüksek kullanılabilirlik, olanaklarına [sektörde lider SLA'lar](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB, şema ve dizin yönetimiyle ilgilenmenize gerek kalmadan [otomatik olarak verilerin dizinini oluşturur](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf). Çok modelli olan bu hizmet belge, anahtar-değer, grafik ve sütunlu veri modellerini destekler.

![Azure Cosmos DB ile dört API protokolleri erişilebilen bir Global olarak dağıtılmış garantili düşük gecikme süreli veritabanıdır. ](./media/image19.1.png)
**Şekil 7-19**. Azure Cosmos DB genel dağıtım

Bir C kullandığınızda\# Azure Cosmos DB API'si tarafından toplama kullanılacak toplama uygulamak için modeli C benzer olabilir\# EF Core ile kullanılan POCO sınıflar. Bunları, aşağıdaki kodda gösterildiği gibi uygulama ve altyapı katmanları arasından kullanılacak şekilde fark vardır:

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

Etki alanı modeliniz çalışma biçiminizi altyapı EF olduğunda, etki alanı model katmanında kullandığınıza benzer bir biçimde olabilir görebilirsiniz. Yine de tutarlılık okuduğunuzda ve toplama içinde doğrulamaları emin olmak için aynı birleşik kök yöntemleri kullanın.

Ancak, ne zaman, modelinizi NoSQL veritabanı, kod ve EF Core kodu önemli ölçüde karşılaştırıldığında API değişiklik veya ilişkisel veritabanları için ilgili herhangi bir kod kalıcı hale getirin.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>MongoDB ve Azure Cosmos DB hedefleyen .NET kodu uygulama

### <a name="use-azure-cosmos-db-from-net-containers"></a>Azure Cosmos DB .NET kapsayıcıları kullanma

Azure Cosmos DB veritabanları, diğer bir .NET uygulamasından gibi kapsayıcılarda, çalıştırılan .NET kodundan erişebilirsiniz. Örneğin, Azure Cosmos DB veritabanları kullandıkları için Locations.API ve Marketing.API mikro Hizmetleri hizmetine uygulanır.

Ancak, bir Docker geliştirme ortamı açısından Azure Cosmos DB'de bir sınırlama yoktur. Bir şirket içi olduğunda bile [Azure Cosmos DB öykünücüsü'nü](https://docs.microsoft.com/azure/cosmos-db/local-emulator) (bilgisayar gibi) bir yerel geliştirme makineniz çalıştırmak kullanabilir, geç 2017, yalnızca Windows, Linux olmayan destekler. 

Docker, ancak yalnızca Windows kapsayıcıları hakkında Linux kapsayıcılarıyla bu öykünücüyü çalıştırmak için olasılık yoktur. Uygulamanızı Linux kapsayıcıları olarak bu yana, şu anda dağıtılırsa, geliştirme ortamı için bir başlangıç handicap, Linux ve Windows kapsayıcıları için Docker Windows üzerinde aynı anda dağıtamazsınız. Dağıtılan ya da tüm kapsayıcıları, Windows veya Linux için yapılması gerekir.

Çözüm Geliştirme/test için ideal ve daha basit dağıtım, geliştirme ve test ortamlarınızı her zaman tutarlı olacak şekilde özel kapsayıcılarınızı yanı sıra kapsayıcıları olarak dağıtabilir, veritabanı sistemleri sağlamaktır.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Yerel geliştirme ve test Linux/Windows kapsayıcıları ayrıca Azure Cosmos DB için MongoDB API'si kullanma

Cosmos DB veritabanları, yerel MongoDB kablo protokolüne yanı sıra .NET için MongoDB API'si desteği. MongoDB için yazılmış uygulamanız mevcut sürücüleri kullanarak artık Cosmos DB ile iletişim kurmak ve Cosmos DB veritabanı MongoDB veritabanları yerine, Şekil 7-20'de gösterildiği gibi kullanabilirsiniz. Bu anlamına gelir.

![Cosmos DB MongoDB API'si için .NET ve MongoDB kablo protokolünü destekler, Mongodb'den Cosmos DB'ye kolayca geçiş yapabilirsiniz. ](./media/image19.2.png)
 **Şekil 7-20**. Azure Cosmos DB'ye erişmek için MongoDB API'si ve protokolü kullanma

Bunun nedeni Linux kapsayıcılar ile Docker ortamlarında kavramları kanıtı için kullanışlı bir yaklaşım, [MongoDB Docker görüntüsü](https://hub.docker.com/r/_/mongo/) Docker Linux kapsayıcıları ve Docker Windows kapsayıcıları destekleyen bir çok yay görüntüsüdür.

Aşağıdaki görüntüde gösterildiği gibi MongoDB API'sini kullanarak, yerel geliştirme ortamı için MongoDB, Linux ve Windows kapsayıcıları hizmetine destekler ancak daha sonra bir biçimde ölçeklendirilebilir, taşıyabilirsiniz PaaS olarak Azure Cosmos DB tarafından yalnızca bulut çözümünü [ Azure Cosmos DB'ye işaret edecek şekilde MongoDB bağlantı dizesini değiştirerek](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Konum mikro hizmetine MongoDB kullanılarak uygulanır, ancak Cosmos DB bağlantı dizesini değiştirerek değiştirilebilir. ](./media/image20-bis.png)
 **Şekil 7-21**. Hizmetine üretim için dev-env veya Azure Cosmos DB için MongoDB kapsayıcıları kullanma

Üretim Azure Cosmos DB, PaaS ve ölçeklenebilir bir hizmet olarak Azure'nın bulutta çalıştırıyordur.

Özel .NET Core kapsayıcılarınızı veya Kubernetes AKS Azure veya Azure Service Fabric gibi bir üretim ortamına dağıtılıp (kullanan için Docker Windows içinde bir Windows 10 makinesi) yerel geliştirme Docker konağı üzerinde çalıştırabilirsiniz. Azure Cosmos DB bulutta üretim verileri işlemek için kullanacağınızı olduğundan bu ikinci bir ortamda, yalnızca .NET Core özel kapsayıcılar ancak MongoDB kapsayıcı dağıtabilirsiniz.

MongoDB API'sini kullanarak, açık bir avantajı, çözümünüzü farklı ortamlara geçişleri kolayca bu nedenle her iki veritabanı motorlarında, MongoDB veya Azure Cosmos DB, çalıştırabilir içindir. Ancak, bazen, belirli bir veritabanı altyapısı özellikleri tam olarak yararlanabilmek için (yani yerel Cosmos DB API) yerel bir API kullanmak faydalı olur.

Yalnızca bulutta Cosmos DB ile MongoDB kullanarak arasında daha fazla karşılaştırması için bkz [bu sayfa, Azure Cosmos DB kullanmanın avantajları](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction). 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Üretim uygulamaları için yaklaşımı analiz edin: MongoDB API'si vs. Cosmos DB API

Azure Cosmos DB ile de çalışabilir bir NoSQL veritabanı kullanarak bir tutarlı geliştirme ve test ortamı sağlamak için bizim önceliğimiz temelde olduğundan hizmetine MongoDB API'sini kullanıyoruz.

Ancak, varsa, üretim uygulamaları için Azure Cosmos DB azure'da erişmek için MongoDB API'sini kullanmayı planlama, özelliklerine ve performans farkı yerel kullanmaya kıyasla Azure Cosmos DB veritabanlarına erişmek için MongoDB API'si kullanılırken çözümlemeniz gerekir Azure Cosmos DB API. Benzer ise MongoDB API'si kullanabilir ve aynı anda iki NoSQL veritabanı altyapılarını destekleyen avantajı alın.

Azure'nın bulutta üretim veritabanı olarak MongoDB kümeleri de kullanabilirsiniz, ile [Azure hizmet MongoDB](https://www.mongodb.com/scale/mongodb-azure-service). Ancak, Microsoft tarafından sağlanan bir PaaS hizmeti değil. Bu durumda, Azure adresinden gelen bu çözüm yalnızca barındırma sağlayıcılarıdır.

Temel olarak, yalnızca Linux kapsayıcıları için kullanışlı bir seçim olduğundan hizmetine yaptığımız gibi Azure Cosmos DB MongoDB API'si her zaman kullanmamalısınız belirten bir bildirim budur. Karar üretim uygulamanız için gerçekleştirmeniz gereken testleri ve ihtiyaçlarınıza bağlı olmalıdır.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kodu: MongoDB API'si, .NET Core uygulamalarında kullanma

MongoDB API'si için .NET Locations.API projesinde aşağıdaki şekilde gösterildiği gibi projenize eklemek için gereken NuGet paketlerini temel alır.

![Bağımlılıklar MongoDB NuGet paketleri gösteren Çözüm Gezgini görünümü.](./media/image21-bis.png)

**Şekil 7-22**. .NET Core projesi başvuruları MongoDB API NuGet paketleri

Şimdi aşağıdaki bölümlerde kodu inceleyin.

#### <a name="a-model-used-by-mongodb-api"></a>MongoDB API'si tarafından kullanılan bir Model

İlk olarak, uygulamanızın bellek alanı veritabanından gelen verileri barındıracak bir modeli tanımlamak gerekir. Hizmetine konumları için kullanılan model örneği aşağıda verilmiştir.

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

Bazı öznitelikler ve MongoDB NuGet paketlerinden gelen türleri görebilirsiniz.

NoSQL veritabanları genellikle ilişkisel olmayan hiyerarşik veriler ile çalışmak için çok uygundur. Bu örnekte, özellikle gibi coğrafi konumları için yapılan MongoDB türlerini kullanıyoruz `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Veritabanı ve koleksiyonu alın

Biz burada veritabanı ve aşağıdaki kodda gösterildiği gibi MongoCollections almak için kod uygulamak özel veritabanı bağlamında hizmetine oluşturduk.

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

C# kodunda, Web APİ'si denetleyicilerinin veya özel depolarda uygulaması gibi benzer kod şu şekilde MongoDB API'si sorgulanırken yazabilirsiniz. Unutmayın `_context` nesnedir, önceki örneği `LocationsContext` sınıfı.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>MongoDB bağlantı dizesi için docker-compose.override.yml dosyasında bir env-var kullanın

MongoClient nesnesini oluştururken, tam olarak olan temel bir parametre gerekli `ConnectionString` doğru veritabanına işaret eden bir parametre. Hizmetine söz konusu olduğunda, yerel bir MongoDB Docker kapsayıcısı veya "üretim" Azure Cosmos DB veritabanına bağlantı dizesi işaret edebilir.  Tanımlanan ortam değişkenleri Bu bağlantı dizesi geldiği `docker-compose.override.yml` docker-compose ya da Visual Studio ile olduğu gibi aşağıdaki yml kodu dağıtırken kullanılan dosyaları.

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

`ConnectionString` Ortam değişkeni bu şekilde çözümlendi: Varsa `ESHOP_AZURE_COSMOSDB` genel değişken tanımlanmış `.env` dosyası ile Azure Cosmos DB bağlantı dizesi, onu bulutta Azure Cosmos DB veritabanına erişmek için kullanır. Tanımlanmazsa, mongodb://nosql.data değeri ve geliştirme mongodb kapsayıcısını kullanın.

Aşağıdaki kodda gösterildiği `.env` hizmetine uygulandığı şekilde Azure Cosmos DB bağlantı dizesi genel ortam değişkeni'ile dosya:

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

Azure Cosmos DB bağlantı dizenizi Azure portalından olarak elde edilen ile açıklanan güncelleştirmeyi ve ESHOP_AZURE_COSMOSDB satırı açıklamadan çıkarın [bir MongoDB uygulamasını Azure Cosmos DB'ye bağlanmak](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Varsa `ESHOP_AZURE_COSMOSDB` genel değişkeni, out olarak geçersiz kılınan, yani, boş `.env` kapsayıcı adlıhizmetinedağıtılanyerelMongoDBkapsayıcısınıişaretedenbirvarsayılanMongoDBbağlantıdizesikullanır,dosya`nosql.data`ve docker-compose dosyasından aşağıdaki .yml kodda gösterildiği gibi tanımlanmıştır. 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a>Ek kaynaklar

- **NoSQL veritabanları için belge verilerini modelleme** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon. Ideal etki alanı Odaklı Tasarım toplama Store?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Azure Cosmos DB'ye giriş: MongoDB API'si**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB: .NET ve Azure portalıyla bir MongoDB API'si web uygulaması derleme**  \
  [https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet](https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet )

- **Yerel geliştirme ve test için Azure Cosmos DB öykünücüsü'nü kullanın**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Bir MongoDB uygulamasını Azure Cosmos DB'ye bağlanma**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Cosmos DB öykünücüsü Docker görüntüsünü (Windows kapsayıcı)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **MongoDB Docker görüntü (Linux ve Windows kapsayıcı)**  \
  <https://hub.docker.com/\_/mongo/>

- **MongoChef (Studio 3T), Azure Cosmos DB ile kullanın: MongoDB hesabı için API**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Önceki](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[İleri](microservice-application-layer-web-api-design.md)

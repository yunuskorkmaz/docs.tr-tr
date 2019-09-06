---
title: NoSQL veritabanlarını bir kalıcılık altyapısı olarak kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Genel olarak NoSql veritabanlarının kullanımını ve özellikle de Azure Cosmos DB, persistance uygulama seçeneği olarak anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 7a8573f8f668a5b75f50acde57a2f4c42ce4d189
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374033"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="44250-103">Kalıcı altyapı olarak NoSQL veritabanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="44250-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="44250-104">Altyapı veri katmanınız için NoSQL veritabanlarını kullandığınızda, genellikle Entity Framework Core gibi bir ORM kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="44250-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="44250-105">Bunun yerine, Azure Cosmos DB, MongoDB, Cassandra, Rayvendb, Couşdb veya Azure depolama tabloları gibi NoSQL altyapısı tarafından sunulan API 'YI kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="44250-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="44250-106">Ancak, bir NoSQL veritabanı kullandığınızda, özellikle de Azure Cosmos DB, Couşdb veya Avendb gibi bir belge yönelimli bir veritabanı kullandığınızda, EF Core bu modeli DDD toplamalarda tasarlama şekliniz, Toplam kökleri, alt varlık sınıfları ve değer nesnesi sınıfları.</span><span class="sxs-lookup"><span data-stu-id="44250-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="44250-107">Ancak, sonunda veritabanı seçimi tasarımınızda etkileyecektir.</span><span class="sxs-lookup"><span data-stu-id="44250-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="44250-108">Belge yönelimli bir veritabanı kullandığınızda, bir toplamı JSON veya başka bir biçimde sıralanmış tek bir belge olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="44250-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="44250-109">Ancak, veritabanının kullanımı bir görünüm etki alanı modeli kod noktasından saydamdır.</span><span class="sxs-lookup"><span data-stu-id="44250-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="44250-110">Bir NoSQL veritabanı kullanırken, hala varlık sınıfları ve toplama kök sınıfları kullanıyorsunuz, ancak Kalıcılık ilişkisel olmadığından EF Core kullanmaktan daha fazla esneklik elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="44250-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="44250-111">Fark, bu modeli nasıl kalıcı hale getiribir modeldir.</span><span class="sxs-lookup"><span data-stu-id="44250-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="44250-112">Etki alanı modelinizi POCO varlık sınıflarına göre uyguladıysanız, altyapı kalıcılığına göre bağımsız olarak, ilişkisel ve NoSQL arasında bile farklı bir kalıcılık altyapısına geçebilirsiniz gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="44250-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="44250-113">Bununla birlikte, hedefiniz olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44250-113">However, that should not be your goal.</span></span> <span data-ttu-id="44250-114">Farklı veritabanı teknolojilerinde her zaman kısıtlamalar ve denge bulunur, bu nedenle ilişkisel veya NoSQL veritabanları için aynı modele sahip olmayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="44250-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="44250-115">İşlem ve Kalıcılık işlemleri çok farklı olacağı için kalıcılık modellerinin değiştirilmesi önemsiz bir görev değildir.</span><span class="sxs-lookup"><span data-stu-id="44250-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="44250-116">Örneğin, belge odaklı bir veritabanında, bir toplama kökünün birden çok alt koleksiyon özelliği olması normaldir.</span><span class="sxs-lookup"><span data-stu-id="44250-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="44250-117">Bir ilişkisel veritabanında, bir UNıON ALL SQL ifadesini bir UNıON 'den geri alacağınız için, birden çok alt koleksiyon özelliklerini sorgulama özelliği kolayca iyileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="44250-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="44250-118">İlişkisel veritabanları veya NoSQL veritabanları için aynı etki alanı modeline sahip olmak basit değildir ve bunu yapmayı denememelisiniz.</span><span class="sxs-lookup"><span data-stu-id="44250-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="44250-119">Gerçekten de, verilerin belirli bir veritabanında nasıl kullanılacağına ilişkin bir anlama sahip olacak şekilde modelinizin tasarımını yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44250-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="44250-120">NoSQL veritabanları kullanmanın bir avantajı, varlıkların daha fazla normalleştirilmiştir, bu nedenle tablo eşlemesi ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="44250-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="44250-121">Etki alanı modeliniz, ilişkisel bir veritabanı kullanmaktan daha esnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="44250-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="44250-122">Etki alanı modelinizi toplamalara göre tasarladığınızda, NoSQL ve belge odaklı veritabanlarına geçiş, bir ilişkisel veritabanı kullanmaktan daha da kolay olabilir, çünkü tasarladığınız toplamalar belge odaklı veritabanında seri hale getirilmiş belgelere benzerdir.</span><span class="sxs-lookup"><span data-stu-id="44250-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="44250-123">Daha sonra bu toplama için ihtiyaç duyduğunuz tüm bilgileri bu "Batı" ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44250-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="44250-124">Örneğin, aşağıdaki JSON kodu, belge yönelimli bir veritabanı kullanılırken bir sıra toplamanın örnek uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="44250-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="44250-125">EShopOnContainers örneğinde uyguladığımız sıra toplamasına benzerdir, ancak altında EF Core kullanmadan.</span><span class="sxs-lookup"><span data-stu-id="44250-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="44250-126">Azure Cosmos DB ve yerel Cosmos DB API 'sine giriş</span><span class="sxs-lookup"><span data-stu-id="44250-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="44250-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) , Microsoft 'un görev açısından kritik uygulamalar için genel olarak dağıtılmış veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="44250-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="44250-128">Azure Cosmos DB, [ön anahtar genel dağıtımı](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [Esnek işleme ve depolama için esnek ölçeklendirme](https://docs.microsoft.com/azure/cosmos-db/partition-data) , 99. yüzdebirlik, [beş adet iyi tanımlanmış tutarlılık düzeyi](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)ve garantili yüksek gecikme süreleriyle birlikte, tek basamaklı milisaniyelik gecikme süresi sağlar kullanılabilirlik, hepsi [sektörde önde gelen SLA 'lar](https://azure.microsoft.com/support/legal/sla/cosmos-db/)tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="44250-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="44250-129">Azure Cosmos DB, şema ve dizin yönetimiyle ilgilenmenize gerek kalmadan [otomatik olarak verilerin dizinini oluşturur](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf).</span><span class="sxs-lookup"><span data-stu-id="44250-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="44250-130">Çok modelli olan bu hizmet belge, anahtar-değer, grafik ve sütunlu veri modellerini destekler.</span><span class="sxs-lookup"><span data-stu-id="44250-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![<span data-ttu-id="44250-131">Azure Cosmos DB, dört API protokolleriyle erişilebilen, küresel olarak dağıtılmış garantili düşük gecikme süreli bir veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="44250-131">Azure Cosmos DB is a globally distributed guaranteed low-latency database that can be accessed with four API protocols.</span></span> ](./media/image19.1.png)

<span data-ttu-id="44250-132">**Şekil 7-19**.</span><span class="sxs-lookup"><span data-stu-id="44250-132">**Figure 7-19**.</span></span> <span data-ttu-id="44250-133">Azure Cosmos DB küresel dağıtım</span><span class="sxs-lookup"><span data-stu-id="44250-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="44250-134">Azure Cosmos DB API tarafından kullanılacak toplamı\# uygulamak için bir C modeli kullandığınızda, toplama, EF Core kullanılan c\# poco sınıflarına benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="44250-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="44250-135">Bu fark, aşağıdaki kodda olduğu gibi uygulama ve altyapı katmanlarından kullanmanın bir yoludur:</span><span class="sxs-lookup"><span data-stu-id="44250-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="44250-136">Altyapı EF olduğunda, etki alanı modelinize çalışırken kullandığınız şekilde, etki alanı modeli katmanınızda kullanma biçimine benzer bir şekilde bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44250-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="44250-137">Toplama içindeki tutarlılığı, ınvaryantları ve doğrulamaları sağlamak için yine de aynı toplama kök yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="44250-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="44250-138">Ancak, modelinizi NoSQL veritabanına kalıcı hale getirebilmeniz durumunda kod ve API değişikliği EF Core kodla veya ilişkisel veritabanlarıyla ilgili diğer herhangi bir kodla karşılaştırıldığında önemli ölçüde değişir.</span><span class="sxs-lookup"><span data-stu-id="44250-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="44250-139">MongoDB hedefleme ve Azure Cosmos DB .NET kodu uygulama</span><span class="sxs-lookup"><span data-stu-id="44250-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="44250-140">.NET kapsayıcılarından Azure Cosmos DB kullanma</span><span class="sxs-lookup"><span data-stu-id="44250-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="44250-141">Kapsayıcılarda çalışan .NET kodundan, diğer tüm .NET uygulamaları gibi Azure Cosmos DB veritabanlarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44250-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="44250-142">Örneğin, eShopOnContainers içindeki locations. API ve Marketing. API mikro hizmetleri, Azure Cosmos DB veritabanlarını tüketebilecekleri şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="44250-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="44250-143">Ancak, bir Docker geliştirme ortamı görünümündeki Azure Cosmos DB bir sınırlama vardır.</span><span class="sxs-lookup"><span data-stu-id="44250-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="44250-144">Bir şirket içi [Azure Cosmos DB öykünücü](https://docs.microsoft.com/azure/cosmos-db/local-emulator) , bir bilgisayar gibi bir yerel geliştirme makinesinde (PC gibi) çalıştırılabilse de, en geç 2017 Itibariyle yalnızca Windows 'u destekler.</span><span class="sxs-lookup"><span data-stu-id="44250-144">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="44250-145">Ayrıca, Linux kapsayıcılarıyla değil, yalnızca Windows kapsayıcılarında bu öykünücüyü çalıştırma olasılığı da vardır.</span><span class="sxs-lookup"><span data-stu-id="44250-145">There is also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="44250-146">Uygulamanız Linux kapsayıcıları olarak dağıtılmışsa geliştirme ortamı için bir ilk Handicap olan bu, şu anda Linux ve Windows kapsayıcılarını Docker for Windows aynı anda dağıtamazsınız.</span><span class="sxs-lookup"><span data-stu-id="44250-146">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="44250-147">Dağıtılmakta olan tüm kapsayıcıların Linux veya Windows için olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44250-147">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="44250-148">Geliştirme/test çözümüne yönelik ideal ve daha basit dağıtım, geliştirme ve test ortamlarınızın her zaman tutarlı olması için veritabanı sistemlerinizi özel kapsayıcılarınızla birlikte kapsayıcı olarak dağıtabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="44250-148">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="44250-149">Yerel geliştirme ve test için MongoDB API 'SI kullanma ve Linux/Windows kapsayıcıları Plus Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="44250-149">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="44250-150">Cosmos DB veritabanları, .NET için MongoDB API 'nin yanı sıra yerel MongoDB kablo protokolünü de destekler.</span><span class="sxs-lookup"><span data-stu-id="44250-150">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="44250-151">Bu, var olan sürücüler kullanılarak MongoDB için yazılmış uygulamanız artık Cosmos DB ile iletişim kurabilir ve Şekil 7-20 ' de gösterildiği gibi MongoDB veritabanları yerine Cosmos DB veritabanlarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="44250-151">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Cosmos DB .NET ve MongoDB kablo protokolü için MongoDB API 'sini destekler, MongoDb 'den Cosmos DB 'e kolayca geçiş yapabilirsiniz.](./media/image19.2.png)

<span data-ttu-id="44250-153">**Şekil 7-20**.</span><span class="sxs-lookup"><span data-stu-id="44250-153">**Figure 7-20**.</span></span> <span data-ttu-id="44250-154">Azure Cosmos DB erişmek için MongoDB API 'sini ve protokolünü kullanma</span><span class="sxs-lookup"><span data-stu-id="44250-154">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="44250-155">[MongoDB Docker görüntüsü](https://hub.docker.com/r/_/mongo/) , Docker Linux kapsayıcılarını ve Docker Windows kapsayıcılarını destekleyen çok katmanlı bir görüntü olduğundan, Linux kapsayıcılarıyla Docker ortamlarında kavram kanıtı açısından çok kullanışlı bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="44250-155">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="44250-156">Aşağıdaki görüntüde gösterildiği gibi, MongoDB API 'sini kullanarak, eShopOnContainers yerel geliştirme ortamı için MongoDB Linux ve Windows kapsayıcılarını destekler, ancak Azure Cosmos DB daha [sonra yalnızca Azure Cosmos DB işaret etmek için MongoDB bağlantı dizesi](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="44250-156">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![EShopOnContainers 'daki location mikro hizmeti MongoDB kullanılarak uygulanır, ancak bağlantı dizesi değiştirilerek yalnızca Cosmos DB ' a geçiş yapılabilir.](./media/image20-bis.png)

<span data-ttu-id="44250-158">**Şekil 7-21**.</span><span class="sxs-lookup"><span data-stu-id="44250-158">**Figure 7-21**.</span></span> <span data-ttu-id="44250-159">geliştirme için MongoDB kapsayıcılarını kullanan eShopOnContainers-env veya Azure Cosmos DB for Production</span><span class="sxs-lookup"><span data-stu-id="44250-159">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="44250-160">Üretim Azure Cosmos DB, Azure 'un bulutta PaaS ve ölçeklenebilir bir hizmet olarak çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="44250-160">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="44250-161">Özel .NET Core kapsayıcılarınız yerel bir geliştirme Docker ana bilgisayarında (bir Windows 10 makinesinde Docker for Windows kullanan) veya Azure AKS veya Azure Service Fabric 'de Kubernetes gibi bir üretim ortamına dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="44250-161">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="44250-162">Bu ikinci ortamda, üretimde verileri işlemek için bulutta Azure Cosmos DB kullandığınızdan bu yana MongoDB kapsayıcısını değil yalnızca .NET Core özel kapsayıcılarını dağıtırsınız.</span><span class="sxs-lookup"><span data-stu-id="44250-162">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="44250-163">MongoDB API 'sini kullanmanın net bir avantajı, çözümünüzün her iki veritabanı altyapıda, MongoDB veya Azure Cosmos DB çalışmasına, böylece farklı ortamlara geçişlerin kolay olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44250-163">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="44250-164">Ancak bazı durumlarda, belirli bir veritabanı altyapısının yetilerinden tam olarak yararlanabilmek için yerel bir API (yerel Cosmos DB API) kullanılması çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="44250-164">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="44250-165">Yalnızca MongoDB ile bulutta Cosmos DB karşılaştırması arasında daha fazla karşılaştırma için [Bu sayfada Azure Cosmos DB kullanmanın avantajları](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="44250-165">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span> 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="44250-166">Üretim uygulamaları için yaklaşımınızı çözümleyin: MongoDB API 'SI ile Cosmos DB API 'SI</span><span class="sxs-lookup"><span data-stu-id="44250-166">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="44250-167">EShopOnContainers 'da, MongoDB API 'sini kullandık. önceliklerimiz, Azure Cosmos DB ile de çalışan bir NoSQL veritabanı kullanarak tutarlı bir geliştirme/test ortamına sahip olacak.</span><span class="sxs-lookup"><span data-stu-id="44250-167">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="44250-168">Ancak, Azure 'da üretim uygulamaları için Azure Cosmos DB erişmek üzere MongoDB API 'sini kullanmayı planlıyorsanız, yerel veritabanını kullanmaya kıyasla Azure Cosmos DB veritabanlarına erişmek için MongoDB API 'sini kullanırken yetenekler ve performans farklılıklarını çözümlemeniz gerekir Azure Cosmos DB API 'SI.</span><span class="sxs-lookup"><span data-stu-id="44250-168">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="44250-169">Benzer bir şekilde, MongoDB API 'sini kullanabilir ve aynı anda iki NoSQL veritabanı altyapısını destekleme avantajına sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="44250-169">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="44250-170">Ayrıca MongoDB kümelerini, [MongoDB Azure hizmeti](https://www.mongodb.com/scale/mongodb-azure-service)ile Azure bulutu 'nda bulunan üretim veritabanı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44250-170">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="44250-171">Ancak Microsoft tarafından sağlanmış bir PaaS hizmeti değildir.</span><span class="sxs-lookup"><span data-stu-id="44250-171">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="44250-172">Bu durumda, Azure yalnızca bu çözümün MongoDB 'den geldiğini barındırıyor.</span><span class="sxs-lookup"><span data-stu-id="44250-172">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="44250-173">Temel olarak bu yalnızca, Azure Cosmos DB karşı MongoDB API 'sini her zaman bir Linux kapsayıcıları için kullanışlı bir seçenek olduğu için, her zaman bir karşı kullanacağınızı belirten bir vazgeçme belgesi.</span><span class="sxs-lookup"><span data-stu-id="44250-173">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="44250-174">Karar, üretim uygulamanız için yapmanız gereken belirli ihtiyaçları ve Testleri temel almalıdır.</span><span class="sxs-lookup"><span data-stu-id="44250-174">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="44250-175">Kod: .NET Core uygulamalarında MongoDB API 'sini kullanma</span><span class="sxs-lookup"><span data-stu-id="44250-175">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="44250-176">.NET için MongoDB API 'SI, aşağıdaki şekilde gösterilen konumlar. API projesinde olduğu gibi, projelerinize eklemeniz gereken NuGet paketlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="44250-176">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![MongoDB NuGet paketlerindeki bağımlılıkları gösteren Çözüm Gezgini görünümü.](./media/image21-bis.png)

<span data-ttu-id="44250-178">**Şekil 7-22**.</span><span class="sxs-lookup"><span data-stu-id="44250-178">**Figure 7-22**.</span></span> <span data-ttu-id="44250-179">.NET Core projesinde MongoDB API NuGet paketleri başvuruları</span><span class="sxs-lookup"><span data-stu-id="44250-179">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="44250-180">Aşağıdaki bölümlerde kodu araştıralım.</span><span class="sxs-lookup"><span data-stu-id="44250-180">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="44250-181">MongoDB API tarafından kullanılan bir model</span><span class="sxs-lookup"><span data-stu-id="44250-181">A Model used by MongoDB API</span></span>

<span data-ttu-id="44250-182">İlk olarak, uygulamanızın bellek alanındaki veritabanından gelen verileri tutacak bir model tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44250-182">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="44250-183">EShopOnContainers konumundaki konumlar için kullanılan modele bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="44250-183">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="44250-184">MongoDB NuGet paketlerinden birkaç öznitelik ve tür olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44250-184">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="44250-185">NoSQL veritabanları genellikle ilişkisel olmayan hiyerarşik verilerle çalışmaya yönelik oldukça uygundur.</span><span class="sxs-lookup"><span data-stu-id="44250-185">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="44250-186">Bu örnekte, özellikle gibi `GeoJson2DGeographicCoordinates`coğrafi konumlar Için oluşturulan MongoDB türlerini kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="44250-186">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="44250-187">Veritabanını ve koleksiyonu alma</span><span class="sxs-lookup"><span data-stu-id="44250-187">Retrieve the database and the collection</span></span>

<span data-ttu-id="44250-188">EShopOnContainers 'da, aşağıdaki kodda olduğu gibi veritabanını ve MongoCollections 'ı almak için kodu uyguladığımız özel bir veritabanı bağlamı oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="44250-188">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="44250-189">Verileri alma</span><span class="sxs-lookup"><span data-stu-id="44250-189">Retrieve the data</span></span>

<span data-ttu-id="44250-190">Web C# API denetleyicileri veya özel depolar uygulama gibi kodda, MongoDB API 'si ile sorgulama yaparken aşağıdakine benzer bir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44250-190">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="44250-191">`_context` Nesnenin önceki`LocationsContext` sınıfın bir örneği olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="44250-191">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="44250-192">MongoDB bağlantı dizesi için Docker-Compose. override. yıml dosyasında bir env-var kullanın</span><span class="sxs-lookup"><span data-stu-id="44250-192">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="44250-193">Mongoclient nesnesi oluştururken doğru veritabanına işaret eden bir `ConnectionString` parametre olan temel bir parametreye ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="44250-193">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="44250-194">EShopOnContainers söz konusu olduğunda, bağlantı dizesi bir yerel MongoDB Docker kapsayıcısına veya bir "üretim" Azure Cosmos DB veritabanına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="44250-194">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="44250-195">Bu bağlantı dizesi, aşağıdaki-ml kodunda olduğu gibi Docker-Compose veya Visual Studio ile dağıtım yaparken kullanılan `docker-compose.override.yml` dosyalarda tanımlanan ortam değişkenlerinden gelir.</span><span class="sxs-lookup"><span data-stu-id="44250-195">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="44250-196">`ConnectionString` Ortam değişkeni şu şekilde çözümlenir: Genel değişken `.env` dosyada Azure Cosmos DB bağlantı dizesiyle tanımlanmışsa, Bulutta Azure Cosmos db veritabanına erişmek için onu kullanır. `ESHOP_AZURE_COSMOSDB`</span><span class="sxs-lookup"><span data-stu-id="44250-196">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="44250-197">Tanımlı değilse, mongodb://nosql.data değerini alır ve geliştirme MongoDB kapsayıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="44250-197">If it’s not defined, it will take the mongodb://nosql.data value and use the development mongodb container.</span></span>

<span data-ttu-id="44250-198">Aşağıdaki kod, eshoponcontainers içinde uygulandığı gibi Azure Cosmos DB bağlantı dizesi genel ortam değişkeniyle birlikte `.env` dosyayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="44250-198">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="44250-199">ESHOP_AZURE_COSMOSDB satırının açıklamasını kaldırın ve [bir MongoDB uygulamasını Azure Cosmos DB 'e bağlama](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)bölümünde açıklandığı gibi Azure Portal elde edilen Azure Cosmos DB bağlantı dizeniz ile güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44250-199">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="44250-200">Genel değişken boşsa, bu, `.env` dosyada açıklama eklendiğinde, bu durumda kapsayıcı, şu şekilde adlandırılan eshoponcontainers içinde dağıtılan yerel MongoDB kapsayıcısını işaret eden bir varsayılan MongoDB bağlantı dizesi kullanır. `ESHOP_AZURE_COSMOSDB` `nosql.data`ve, aşağıdaki. yıml kodunda gösterildiği gibi Docker-Compose dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="44250-200">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data` and was defined at the docker-compose file, as shown in the following .yml code.</span></span> 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="44250-201">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="44250-201">Additional resources</span></span>

- <span data-ttu-id="44250-202">**NoSQL veritabanları için belge verilerini modelleme** </span><span class="sxs-lookup"><span data-stu-id="44250-202">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="44250-203">**Vaughn versuz. Ideal etki alanı odaklı tasarım toplama deposu?**</span><span class="sxs-lookup"><span data-stu-id="44250-203">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="44250-204">**Azure Cosmos DB giriş: MongoDB için API**  </span><span class="sxs-lookup"><span data-stu-id="44250-204">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="44250-205">**Azure Cosmos DB: .NET ve Azure portal bir MongoDB API web uygulaması oluşturun**  </span><span class="sxs-lookup"><span data-stu-id="44250-205">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  [https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet](https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet )

- <span data-ttu-id="44250-206">**Yerel geliştirme ve test için Azure Cosmos DB öykünücüsü kullanma**  </span><span class="sxs-lookup"><span data-stu-id="44250-206">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="44250-207">**MongoDB uygulamasını Azure Cosmos DB bağlama**  </span><span class="sxs-lookup"><span data-stu-id="44250-207">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="44250-208">**Cosmos DB öykünücü Docker görüntüsü (Windows kapsayıcısı)**   </span><span class="sxs-lookup"><span data-stu-id="44250-208">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="44250-209">**MongoDB Docker görüntüsü (Linux ve Windows kapsayıcısı)**   </span><span class="sxs-lookup"><span data-stu-id="44250-209">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="44250-210">**MongoChef (Studio 3T) öğesini bir Azure Cosmos DB kullanın: MongoDB hesabı için API**  </span><span class="sxs-lookup"><span data-stu-id="44250-210">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="44250-211">[Önceki](infrastructure-persistence-layer-implemenation-entity-framework-core.md)İleri
>[](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="44250-211">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>

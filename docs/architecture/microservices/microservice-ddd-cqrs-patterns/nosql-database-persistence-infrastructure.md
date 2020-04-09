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
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="a39da-103">Kalıcılık altyapısı olarak NoSQL veritabanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="a39da-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="a39da-104">Altyapı veri katmanınız için NoSQL veritabanlarını kullandığınızda, genellikle Entity Framework Core gibi bir ORM kullanmazsınız.</span><span class="sxs-lookup"><span data-stu-id="a39da-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="a39da-105">Bunun yerine Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB veya Azure Depolama Tabloları gibi NoSQL altyapısı tarafından sağlanan API'yi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a39da-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="a39da-106">Ancak, bir NoSQL veritabanı, özellikle Azure Cosmos DB, CouchDB veya RavenDB gibi belge yönelimli bir veritabanı kullandığınızda, modelinizi DDD agregalarıyla tasarlama şekliniz, toplu köklerin, alt varlık sınıflarının ve değer nesne sınıflarının tanımlanması açısından EF Core'da bunu nasıl yapabileceğinize kısmen benzer.</span><span class="sxs-lookup"><span data-stu-id="a39da-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="a39da-107">Ancak, sonuçta, veritabanı seçimi tasarımınızı etkileyecektir.</span><span class="sxs-lookup"><span data-stu-id="a39da-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="a39da-108">Belge yönelimli bir veritabanı kullandığınızda, json veya başka bir biçimde seri hale getirilmiş tek bir belge olarak bir agrega uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="a39da-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="a39da-109">Ancak, veritabanının kullanımı bir etki alanı modeli kodu açısından saydamdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="a39da-110">Bir NoSQL veritabanı kullanırken, kalıcılık ilişkisel olmadığından, varlık sınıflarını ve toplu kök sınıflarını kullanmaya devam emkişi kullanıyorsunuz, ancak EF Core'u kullanırken daha fazla esneklikle.</span><span class="sxs-lookup"><span data-stu-id="a39da-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="a39da-111">Aradaki fark, bu modeli nasıl devam ettirdiğinizdir.</span><span class="sxs-lookup"><span data-stu-id="a39da-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="a39da-112">Etki alanı modelinizi, altyapı kalıcılığına agnostik olan POCO varlık sınıflarını temel alan olarak uyguladıysanız, ilişkiselden NoSQL'e kadar farklı bir kalıcılık altyapısına geçebilirsiniz gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a39da-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="a39da-113">Ancak, bu hedef olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-113">However, that should not be your goal.</span></span> <span data-ttu-id="a39da-114">Farklı veritabanı teknolojilerinde her zaman kısıtlamalar ve dengeler vardır, bu nedenle ilişkisel veya NoSQL veritabanları için aynı modele sahip olamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a39da-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="a39da-115">Kalıcılık modellerini değiştirmek önemsiz bir görev değildir, çünkü işlemler ve kalıcılık işlemleri çok farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a39da-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="a39da-116">Örneğin, belge yönelimli bir veritabanında, bir toplu kökiçin birden çok alt koleksiyon özelliği olması tamamdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="a39da-117">İlişkisel bir veritabanında, EF'den union ALL SQL deyimi aldığınızdan, birden çok alt koleksiyon özelliğini sorgulamak kolayca en iyi duruma getirilmiş değildir.</span><span class="sxs-lookup"><span data-stu-id="a39da-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="a39da-118">İlişkisel veritabanları veya NoSQL veritabanları için aynı etki alanı modeline sahip olmak basit değildir ve bunu yapmaya çalışmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a39da-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="a39da-119">Modelinizi, verilerin her bir veritabanında nasıl kullanılacağını anlayarak tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a39da-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="a39da-120">NoSQL veritabanları nı kullanırken bir yararı varlıkların daha denormalized olmasıdır, bu yüzden bir tablo eşleme ayarlamak değil.</span><span class="sxs-lookup"><span data-stu-id="a39da-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="a39da-121">Etki alanı modeliniz ilişkisel bir veritabanı kullanırken daha esnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="a39da-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="a39da-122">Etki alanı modelinizi agregalara göre tasarlarken, NoSQL'e ve belge yönelimli veritabanlarına geçmek ilişkisel bir veritabanı kullanmaktan daha kolay olabilir, çünkü tasarladığınız agregalar belge yönelimli bir veritabanındaki serileştirilmiş belgelere benzer.</span><span class="sxs-lookup"><span data-stu-id="a39da-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="a39da-123">Sonra bu "çanta" bu toplam için ihtiyaç duyabileceğiniz tüm bilgileri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a39da-123">Then you can include in those "bags" all the information you might need for that aggregate.</span></span>

<span data-ttu-id="a39da-124">Örneğin, aşağıdaki JSON kodu, belge yönelimli bir veritabanı kullanırken bir sipariş toplamının örnek uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="a39da-125">Bu eShopOnContainers örnek uygulanan sipariş toplam benzer, ancak altında EF Core kullanmadan.</span><span class="sxs-lookup"><span data-stu-id="a39da-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="a39da-126">Azure Cosmos DB ve yerli Cosmos DB API'ye giriş</span><span class="sxs-lookup"><span data-stu-id="a39da-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="a39da-127">[Azure Cosmos DB,](https://docs.microsoft.com/azure/cosmos-db/introduction) Görev açısından kritik uygulamalar için Microsoft'un genel olarak dağıtılmış veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="a39da-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="a39da-128">Azure Cosmos DB tarafından [kullanıma hazır genel dağıtım](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), dünya çapında [aktarım hızı ve depolama için elastik ölçeklendirme](https://docs.microsoft.com/azure/cosmos-db/partition-data), 99. yüzdebirlik dilimde tek haneli milisaniyelik gecikme süreleri, [beş iyi tanımlanmış tutarlılık düzeyi](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) ve garantili yüksek kullanılabilirlik olanakları sağlanır ve bunların tamamı [sektör lideri SLA’lar](https://azure.microsoft.com/support/legal/sla/cosmos-db/) ile desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a39da-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="a39da-129">Azure Cosmos DB, şema ve dizin yönetimiyle ilgilenmenize gerek kalmadan [otomatik olarak verilerin dizinini oluşturur](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf).</span><span class="sxs-lookup"><span data-stu-id="a39da-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="a39da-130">Çok modelli olan bu hizmet belge, anahtar-değer, grafik ve sütunlu veri modellerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a39da-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![Azure Cosmos DB genel dağıtımını gösteren diyagram.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

<span data-ttu-id="a39da-132">**Şekil 7-19**.</span><span class="sxs-lookup"><span data-stu-id="a39da-132">**Figure 7-19**.</span></span> <span data-ttu-id="a39da-133">Azure Cosmos DB genel dağıtımı</span><span class="sxs-lookup"><span data-stu-id="a39da-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="a39da-134">Azure Cosmos\# DB API tarafından kullanılacak toplamı uygulamak için bir C modeli kullandığınızda,\# toplam EF Core ile kullanılan C POCO sınıflarına benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="a39da-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="a39da-135">Aradaki fark, aşağıdaki kodda olduğu gibi uygulama ve altyapı katmanlarından bunları kullanma nın yoludur:</span><span class="sxs-lookup"><span data-stu-id="a39da-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="a39da-136">Etki alanı modelinizle çalışma şekliniz, altyapı EF olduğunda etki alanı modeli katmanınızda kullanma şeklinize benzer olabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a39da-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="a39da-137">Toplam da tutarlılık, değişmezler ve doğrulamalar sağlamak için yine de aynı toplu kök yöntemlerini kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a39da-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="a39da-138">Ancak, modelinizi NoSQL veritabanında kalıcı olarak sağınızda, kod ve API, EF Core koduveya ilişkisel veritabanlarıyla ilgili diğer kodlarla karşılaştırıldığında önemli ölçüde değişir.</span><span class="sxs-lookup"><span data-stu-id="a39da-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="a39da-139">MongoDB ve Azure Cosmos DB'yi hedefleyen .NET kodunu uygulayın</span><span class="sxs-lookup"><span data-stu-id="a39da-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="a39da-140">.NET kapsayıcılarından Azure Cosmos DB'yi kullanma</span><span class="sxs-lookup"><span data-stu-id="a39da-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="a39da-141">Azure Cosmos DB veritabanlarına diğer .NET uygulamalarında olduğu gibi kapsayıcılarda çalışan .NET kodundan erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a39da-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="a39da-142">Örneğin, eShopOnContainers'daki Locations.API ve Marketing.API mikro hizmetleri Azure Cosmos DB veritabanlarını kullanabilmeleri için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a39da-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="a39da-143">Ancak, Docker geliştirme ortamı açısından Azure Cosmos DB'de bir sınırlama vardır.</span><span class="sxs-lookup"><span data-stu-id="a39da-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="a39da-144">Yerel bir geliştirme makinesinde çalıştırılabilen bir şirket içi [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) olsa da, yalnızca Windows'u destekler.</span><span class="sxs-lookup"><span data-stu-id="a39da-144">Even though there’s an on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) that can run in a local development machine, it only supports Windows.</span></span> <span data-ttu-id="a39da-145">Linux ve macOS desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a39da-145">Linux and macOS aren't supported.</span></span>

<span data-ttu-id="a39da-146">Ayrıca docker bu emülatör çalıştırmak için imkanı var, ama sadece Windows Kapsayıcılar değil, Linux Containers ile.</span><span class="sxs-lookup"><span data-stu-id="a39da-146">There's also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="a39da-147">Uygulamanız Linux kapsayıcıları olarak dağıtılırsa, şu anda Aynı anda Docker for Windows'da Linux ve Windows Kapsayıcıları dağıtamadığınız için, geliştirme ortamı için ilk engel dir.</span><span class="sxs-lookup"><span data-stu-id="a39da-147">That's an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you can't deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="a39da-148">Dağıtılan tüm kapsayıcılar Linux veya Windows için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-148">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="a39da-149">Bir geliştirme/test çözümü için ideal ve daha basit dağıtım, veritabanı sistemlerinizi özel kapsayıcılarınizle birlikte kapsayıcı olarak dağıtabilmektir, böylece geliştirme/test ortamlarınız her zaman tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-149">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="a39da-150">Yerel dev/test Linux/Windows kapsayıcıları ve Azure Cosmos DB için MongoDB API'yi kullanın</span><span class="sxs-lookup"><span data-stu-id="a39da-150">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="a39da-151">Cosmos DB veritabanları .NET için MongoDB API yanı sıra yerli MongoDB tel protokolü destekler.</span><span class="sxs-lookup"><span data-stu-id="a39da-151">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="a39da-152">Bu, varolan sürücüleri kullanarak, MongoDB için yazılmış uygulamanızın artık Şekil 7-20'de gösterildiği gibi Cosmos DB ile iletişim kurabileceği ve MongoDB veritabanları yerine Cosmos DB veritabanlarını kullanabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a39da-152">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Cosmos DB'nin .NET ve MongoDB tel protokolünü desteklediğini gösteren diyagram.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

<span data-ttu-id="a39da-154">**Şekil 7-20**.</span><span class="sxs-lookup"><span data-stu-id="a39da-154">**Figure 7-20**.</span></span> <span data-ttu-id="a39da-155">Azure Cosmos DB'ye erişmek için MongoDB API ve protokolünü kullanma</span><span class="sxs-lookup"><span data-stu-id="a39da-155">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="a39da-156">[MongoDB Docker görüntü](https://hub.docker.com/r/_/mongo/) Docker Linux kapları ve Docker Windows kapları destekleyen bir çok kemerli görüntü olduğundan Bu Linux kapları ile Docker ortamlarda kavramların kanıtı için çok uygun bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-156">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="a39da-157">Aşağıdaki resimde gösterildiği gibi, MongoDB API kullanarak, eShopOnContainers yerel geliştirme ortamı için MongoDB Linux ve Windows kapsayıcıları destekler ama sonra, sadece [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)işaret Ederek ölçeklenebilir, PaaS bulut çözümü taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a39da-157">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![EShopOnContainers Konum microservice cosmos DB veya Mongo DB kullanabilirsiniz gösteren diyagram.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

<span data-ttu-id="a39da-159">**Şekil 7-21**.</span><span class="sxs-lookup"><span data-stu-id="a39da-159">**Figure 7-21**.</span></span> <span data-ttu-id="a39da-160">üretim için dev-env veya Azure Cosmos DB için MongoDB kapları kullanan eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="a39da-160">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="a39da-161">Azure Cosmos DB üretimi, Azure bulutunda PaaS ve ölçeklenebilir bir hizmet olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="a39da-161">The production Azure Cosmos DB would be running in Azure's cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="a39da-162">Özel .NET Core kapsayıcılarınız yerel bir geliştirme Docker ana bilgisayarda çalıştırılabilir (Windows 10 makinesinde Docker kullanıyor) veya Azure AKS veya Azure Hizmet Kumaşı'ndaki Kubernetes gibi bir üretim ortamına dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="a39da-162">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="a39da-163">Bu ikinci ortamda, üretimdeki verileri işlemek için bulutta Azure Cosmos DB kullandığınızdan, yalnızca .NET Core özel kapsayıcılarını dağıtamaz, ancak MongoDB kapsayıcısını dağıtmazsınız.</span><span class="sxs-lookup"><span data-stu-id="a39da-163">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you'd be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="a39da-164">MongoDB API'yi kullanmanın açık bir yararı, çözümünüzünüzün her iki veritabanı motorunda, MongoDB'de veya Azure Cosmos DB'de çalıştırılamasıdır, bu nedenle farklı ortamlara geçişler kolay olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-164">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="a39da-165">Ancak, bazen belirli bir veritabanı altyapısının özelliklerinden tam olarak yararlanmak için yerel bir API (yani yerel Cosmos DB API) kullanmak faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-165">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="a39da-166">Bulutta Sadece MongoDB ile Cosmos DB'yi kullanmak arasında daha fazla karşılaştırma için [bu sayfada Azure Cosmos DB kullanmanın avantajlarına](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)bakın.</span><span class="sxs-lookup"><span data-stu-id="a39da-166">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="a39da-167">Üretim uygulamaları için yaklaşımınızı analiz edin: MongoDB API vs Cosmos DB API</span><span class="sxs-lookup"><span data-stu-id="a39da-167">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="a39da-168">eShopOnContainers'da MongoDB API kullanıyoruz çünkü önceliğimiz Azure Cosmos DB ile de çalışabilen bir NoSQL veritabanı nı kullanarak tutarlı bir geliştirme/test ortamına sahip olmaktı.</span><span class="sxs-lookup"><span data-stu-id="a39da-168">In eShopOnContainers, we're using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="a39da-169">Ancak, üretim uygulamaları için Azure'da Azure Cosmos DB'ye erişmek için MongoDB API'sini kullanmayı planlıyorsanız, Azure Cosmos DB veritabanlarına erişmek için MongoDB API'sini kullanırken yerel Azure Cosmos DB API'sini kullanmaya kıyasla yetenek ve performans farklılıklarını çözümlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a39da-169">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="a39da-170">Benzer se, MongoDB API'yi kullanabilirsiniz ve aynı anda iki NoSQL veritabanı altyapısını destekleme avantajına ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a39da-170">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="a39da-171">MongoDB Azure Hizmeti ile [MongoDB](https://www.mongodb.com/scale/mongodb-azure-service)kümelerini Azure bulutundaki üretim veritabanı olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a39da-171">You could also use MongoDB clusters as the production database in Azure's cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="a39da-172">Ancak bu, Microsoft tarafından sağlanan bir PaaS hizmeti değildir.</span><span class="sxs-lookup"><span data-stu-id="a39da-172">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="a39da-173">Bu durumda Azure, MongoDB'den gelen bu çözümü barındırıyor.</span><span class="sxs-lookup"><span data-stu-id="a39da-173">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="a39da-174">Temel olarak, bu sadece bir feragat her zaman Azure Cosmos DB karşı MongoDB API kullanmamalısınız belirten, biz Linux kapsayıcılar için uygun bir seçim olduğu için eShopOnContainers yaptığı gibi.</span><span class="sxs-lookup"><span data-stu-id="a39da-174">Basically, this is just a disclaimer stating that you shouldn't always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="a39da-175">Karar, üretim uygulamanız için yapmanız gereken özel gereksinimlere ve testlere dayanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a39da-175">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="a39da-176">Kod: .NET Core uygulamalarında MongoDB API'yi kullanın</span><span class="sxs-lookup"><span data-stu-id="a39da-176">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="a39da-177">.NET için MongoDB API, aşağıdaki şekilde gösterilen Locations.API projesinde olduğu gibi projelerinize eklemeniz gereken NuGet paketlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a39da-177">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![MongoDB NuGet paketlerindeki bağımlılıkların ekran görüntüsü.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

<span data-ttu-id="a39da-179">**Şekil 7-22**.</span><span class="sxs-lookup"><span data-stu-id="a39da-179">**Figure 7-22**.</span></span> <span data-ttu-id="a39da-180">MongoDB API NuGet bir .NET Core projesinde referansları alın</span><span class="sxs-lookup"><span data-stu-id="a39da-180">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="a39da-181">Aşağıdaki bölümlerdeki kodu inceleyelim.</span><span class="sxs-lookup"><span data-stu-id="a39da-181">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="a39da-182">MongoDB API tarafından kullanılan bir model</span><span class="sxs-lookup"><span data-stu-id="a39da-182">A Model used by MongoDB API</span></span>

<span data-ttu-id="a39da-183">İlk olarak, uygulamanızın bellek alanında veritabanından gelen verileri tutacak bir model tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a39da-183">First, you need to define a model that will hold the data coming from the database in your application's memory space.</span></span> <span data-ttu-id="a39da-184">İşte eShopOnContainers konumlar için kullanılan modelin bir örneği.</span><span class="sxs-lookup"><span data-stu-id="a39da-184">Here's an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="a39da-185">MongoDB NuGet paketlerinden gelen birkaç öznitelik ve tür olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a39da-185">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="a39da-186">NoSQL veritabanları genellikle ilişkisel olmayan hiyerarşik verilerle çalışmak için çok uygundur.</span><span class="sxs-lookup"><span data-stu-id="a39da-186">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="a39da-187">Bu örnekte, özellikle coğrafi konumlar için yapılmış MongoDB `GeoJson2DGeographicCoordinates`türleri kullanıyoruz, gibi.</span><span class="sxs-lookup"><span data-stu-id="a39da-187">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="a39da-188">Veritabanını ve koleksiyonu alma</span><span class="sxs-lookup"><span data-stu-id="a39da-188">Retrieve the database and the collection</span></span>

<span data-ttu-id="a39da-189">eShopOnContainers olarak, aşağıdaki kod gibi, veritabanı ve MongoCollections almak için kodu uygulamak özel bir veritabanı bağlamı oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="a39da-189">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="a39da-190">Verileri alma</span><span class="sxs-lookup"><span data-stu-id="a39da-190">Retrieve the data</span></span>

<span data-ttu-id="a39da-191">Web API denetleyicileri veya özel Depolar uygulaması gibi C# kodunda, MongoDB API üzerinden sorgu yaparken aşağıdakilere benzer kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a39da-191">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="a39da-192">Nesnenin `_context` önceki `LocationsContext` sınıfın bir örneği olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a39da-192">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="a39da-193">MongoDB bağlantı dizesi için docker-compose.override.yml dosyasında env-var kullanın</span><span class="sxs-lookup"><span data-stu-id="a39da-193">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="a39da-194">Bir MongoClient nesnesi oluştururken, tam olarak doğru `ConnectionString` veritabanını gösteren parametre olan temel bir parametre gerekir.</span><span class="sxs-lookup"><span data-stu-id="a39da-194">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="a39da-195">eShopOnContainers durumunda, bağlantı dizesi yerel bir MongoDB Docker kapsayıcısına veya bir "üretim" Azure Cosmos DB veritabanına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="a39da-195">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a "production" Azure Cosmos DB database.</span></span>  <span data-ttu-id="a39da-196">Bu bağlantı dizesi, aşağıdaki yml kodunda olduğu gibi docker-compose veya Visual Studio ile dağıtılırken kullanılan `docker-compose.override.yml` dosyalarda tanımlanan ortam değişkenlerinden gelir.</span><span class="sxs-lookup"><span data-stu-id="a39da-196">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="a39da-197">`ConnectionString` Ortam değişkeni şu şekilde çözülür: `ESHOP_AZURE_COSMOSDB` Genel değişken `.env` dosyada Azure Cosmos DB bağlantı dizesiyle tanımlanırsa, buluttaki Azure Cosmos DB veritabanına erişmek için bu değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="a39da-197">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="a39da-198">Tanımlanmamışsa, `mongodb://nosqldata` değeri alır ve geliştirme MongoDB konteyner kullanır.</span><span class="sxs-lookup"><span data-stu-id="a39da-198">If it’s not defined, it will take the `mongodb://nosqldata` value and use the development MongoDB container.</span></span>

<span data-ttu-id="a39da-199">Aşağıdaki kod, `.env` eShopOnContainers'da uygulandığı gibi Azure Cosmos DB bağlantı dizesi global ortam değişkenine sahip dosyayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="a39da-199">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="a39da-200">ESHOP_AZURE_COSMOSDB hattını açıklamamayı ve Azure portalından elde edilen Azure Cosmos DB bağlantı dizenizi, [MongoDB uygulamasını Azure Cosmos DB'ye](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)bağlayın'da açıklandığı gibi güncelleyin.</span><span class="sxs-lookup"><span data-stu-id="a39da-200">Uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="a39da-201">`ESHOP_AZURE_COSMOSDB` Genel değişken boşsa, yani `.env` dosyada yorumlanırsa, kapsayıcı varsayılan bir MongoDB bağlantı dizesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a39da-201">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning it's commented out in the `.env` file, then the container uses a default MongoDB connection string.</span></span> <span data-ttu-id="a39da-202">Bu bağlantı dizesi, aşağıdaki .yml kodunda gösterildiği gibi docker-compose dosyasında adı verilen `nosqldata` ve tanımlanan eShopOnContainers'da dağıtılan yerel MongoDB kapsayıcısını işaret ediyor:</span><span class="sxs-lookup"><span data-stu-id="a39da-202">This connection string points to the local MongoDB container deployed in eShopOnContainers that is named `nosqldata` and was defined at the docker-compose file, as shown in the following .yml code:</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="a39da-203">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a39da-203">Additional resources</span></span>

- <span data-ttu-id="a39da-204">**NoSQL veritabanları için belge verilerini modelleme** </span><span class="sxs-lookup"><span data-stu-id="a39da-204">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="a39da-205">**Vaughn Vernon' u. İdeal etki alanı odaklı tasarım agrega deposu?**</span><span class="sxs-lookup"><span data-stu-id="a39da-205">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="a39da-206">**Azure Cosmos DB'ye Giriş: MongoDB için API**  </span><span class="sxs-lookup"><span data-stu-id="a39da-206">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="a39da-207">**Azure Cosmos DB: .NET ve Azure portalı ile bir MongoDB API web uygulaması oluşturun**  </span><span class="sxs-lookup"><span data-stu-id="a39da-207">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="a39da-208">**Yerel geliştirme ve test için Azure Cosmos DB Emülatörü'ni kullanın**  </span><span class="sxs-lookup"><span data-stu-id="a39da-208">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="a39da-209">**Bir MongoDB uygulamasını Azure Cosmos DB'ye bağlayın**  </span><span class="sxs-lookup"><span data-stu-id="a39da-209">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="a39da-210">**Cosmos DB Emülatör Docker görüntü (Windows Konteyner)**  </span><span class="sxs-lookup"><span data-stu-id="a39da-210">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="a39da-211">**MongoDB Docker görüntüsü (Linux ve Windows Container)**  </span><span class="sxs-lookup"><span data-stu-id="a39da-211">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="a39da-212">**MongoChef'i (Studio 3T) Azure Cosmos DB ile kullanın: MongoDB hesabı için API**  </span><span class="sxs-lookup"><span data-stu-id="a39da-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="a39da-213">[Önceki](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[Sonraki](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="a39da-213">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>

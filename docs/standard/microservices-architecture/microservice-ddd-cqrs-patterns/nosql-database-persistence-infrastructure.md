---
title: NoSQL veritabanlarını bir Kalıcılık altyapısı olarak kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Genel ve Azure Cosmos DB NoSql veritabanlarının kullanımını özellikle kalıcılığı uygulamak için bir seçenek olarak anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 7a9c6c64f5aa482b6d21aab0c88fc204c6427a41
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974789"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="8aefe-103">NoSQL veritabanlarını bir Kalıcılık altyapısı olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="8aefe-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="8aefe-104">Altyapı veri katmanınız için NoSQL veritabanları kullandığınızda, Entity Framework Core gibi bir ORM genellikle kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8aefe-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="8aefe-105">Bunun yerine Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB veya Azure depolama tabloları gibi NoSQL altyapısı tarafından sağlanan API kullanın.</span><span class="sxs-lookup"><span data-stu-id="8aefe-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="8aefe-106">Özellikle bir belge yönelimli veritabanı gibi Azure Cosmos DB, CouchDB veya RavenDB, bir NoSQL veritabanı kullandığınızda, ancak modelinizi DDD toplamalar tasarlayın nasıl EF Core kimliği ilgili bunu yapabilirsiniz için kısmen benzer yoludur Toplama kökleri, alt varlık sınıfları ve değer nesne sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8aefe-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="8aefe-107">Ancak sonuç olarak, veritabanı seçimi tasarımınızda etkiler.</span><span class="sxs-lookup"><span data-stu-id="8aefe-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="8aefe-108">Bir belge yönelimli veritabanı kullandığınızda, JSON veya başka bir biçimde seri hale getirilmiş bir tek belge olarak toplama uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8aefe-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="8aefe-109">Ancak, veritabanı kullanımını bir etki alanı modeli kodu bakıldığında saydamdır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="8aefe-110">Bir NoSQL veritabanı kullanırken, varlık sınıfları ve toplama kök sınıfları kullanmaya devam ancak EF Core için kullanırken değerinden daha esnek Kalıcılık ilişkisel değil.</span><span class="sxs-lookup"><span data-stu-id="8aefe-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="8aefe-111">Bu modelin nasıl kalıcı olarak farktır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="8aefe-112">Etki alanı modeliniz POCO varlık sınıflarında uygulanması durumunda bile gelen ilişkisel, NoSQL için bir farklı Kalıcılık altyapısı için taşıyabilirsiniz gibi altyapı Kalıcılık için dilden bağımsız, görünebilir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="8aefe-113">Ancak, amacınız olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-113">However, that should not be your goal.</span></span> <span data-ttu-id="8aefe-114">Her zaman kısıtlamaları ve farklı veritabanı teknolojileri dezavantajlarına sahip aynı modelin mümkün olmayacak şekilde ilişkisel veya NoSQL veritabanları.</span><span class="sxs-lookup"><span data-stu-id="8aefe-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="8aefe-115">İşlemler ve Kalıcılık işlemleri çok farklı olacağı için Kalıcılık modelleri değiştirme çok basit bir görev değil.</span><span class="sxs-lookup"><span data-stu-id="8aefe-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="8aefe-116">Örneğin, bir belge yönelimli veritabanı, bir toplama kök birden çok alt koleksiyonu özelliklerine sahip olmayı sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="8aefe-117">Bir birleşim tüm SQL deyimi EF geri dönmek için ilişkisel bir veritabanında birden çok alt koleksiyon özelliklerini sorgulama kolayca, getirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="8aefe-118">İlişkisel veritabanları veya NoSQL veritabanları için aynı etki alanı modeli sahip basit değildir ve bunu yapmanın denememelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="8aefe-119">Her bir veritabanı içinde kullanılacak veriler nasıl kolaylaştıracağını anlamak modelinizi tasarlamak olması.</span><span class="sxs-lookup"><span data-stu-id="8aefe-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="8aefe-120">NoSQL veritabanlarını kullanırken bir avantajı varlıkları daha normalleştirilmişlikten çıkarılmış bir tablo eşleme ayarlanmamış olduğundan.</span><span class="sxs-lookup"><span data-stu-id="8aefe-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="8aefe-121">Etki alanı modeliniz ilişkisel bir veritabanı kullanırken değerinden daha esnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="8aefe-122">Ne zaman NoSQL için taşıma etki alanı modeliniz toplamalarda, tasarım ve tasarım toplamalar benzer çünkü belge yönelimli veritabanı ilişkisel bir veritabanı kullanmaktan daha kolay olabilir bir belge yönelimli veritabanı belgelerine seri hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="8aefe-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="8aefe-123">Ardından, bu toplama için ihtiyacınız olabilecek tüm bilgileri bu "paketleri" ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="8aefe-124">Örneği için aşağıdaki JSON kodunu bir örnek bir sipariş toplama bir belge yönelimli veritabanı kullanılırken uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="8aefe-125">Hizmetine örnek, ancak EF Core altında kullanmadan uyguladık sırasını toplama benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="8aefe-126">Azure Cosmos DB ve yerel Cosmos DB API giriş</span><span class="sxs-lookup"><span data-stu-id="8aefe-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="8aefe-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) görev açısından kritik uygulamalar için Microsoft'un Global olarak dağıtılmış veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="8aefe-128">Azure Cosmos DB sağlar [anahtar teslim küresel dağıtım](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [aktarım hızı ve depolama esnek ölçeklendirme](https://docs.microsoft.com/azure/cosmos-db/partition-data) 99. yüzdebirlik dilimde dünya, tek basamaklı milisaniyelik gecikme süreleri [beş iyi tanımlanmış tutarlılık düzeyi](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)ve garantili yüksek kullanılabilirlik, olanaklarına [sektörde lider SLA'lar](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="8aefe-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="8aefe-129">Azure Cosmos DB, şema ve dizin yönetimiyle ilgilenmenize gerek kalmadan [otomatik olarak verilerin dizinini oluşturur](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf).</span><span class="sxs-lookup"><span data-stu-id="8aefe-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="8aefe-130">Çok modelli olan bu hizmet belge, anahtar-değer, grafik ve sütunlu veri modellerini destekler.</span><span class="sxs-lookup"><span data-stu-id="8aefe-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

<span data-ttu-id="8aefe-131">![Azure Cosmos DB ile dört API protokolleri erişilebilen bir Global olarak dağıtılmış garantili düşük gecikme süreli veritabanıdır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-131">![Azure Cosmos DB is a globally distributed guaranteed low-latency database that can be accessed with four API protocols.</span></span> <span data-ttu-id="8aefe-132">](./media/image19.1.png)
**Şekil 7-19**.</span><span class="sxs-lookup"><span data-stu-id="8aefe-132">](./media/image19.1.png)
**Figure 7-19**.</span></span> <span data-ttu-id="8aefe-133">Azure Cosmos DB genel dağıtım</span><span class="sxs-lookup"><span data-stu-id="8aefe-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="8aefe-134">Bir C kullandığınızda\# Azure Cosmos DB API'si tarafından toplama kullanılacak toplama uygulamak için modeli C benzer olabilir\# EF Core ile kullanılan POCO sınıflar.</span><span class="sxs-lookup"><span data-stu-id="8aefe-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="8aefe-135">Bunları, aşağıdaki kodda gösterildiği gibi uygulama ve altyapı katmanları arasından kullanılacak şekilde fark vardır:</span><span class="sxs-lookup"><span data-stu-id="8aefe-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="8aefe-136">Etki alanı modeliniz çalışma biçiminizi altyapı EF olduğunda, etki alanı model katmanında kullandığınıza benzer bir biçimde olabilir görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="8aefe-137">Yine de tutarlılık okuduğunuzda ve toplama içinde doğrulamaları emin olmak için aynı birleşik kök yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8aefe-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="8aefe-138">Ancak, ne zaman, modelinizi NoSQL veritabanı, kod ve EF Core kodu önemli ölçüde karşılaştırıldığında API değişiklik veya ilişkisel veritabanları için ilgili herhangi bir kod kalıcı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="8aefe-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="8aefe-139">MongoDB ve Azure Cosmos DB hedefleyen .NET kodu uygulama</span><span class="sxs-lookup"><span data-stu-id="8aefe-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="8aefe-140">Azure Cosmos DB .NET kapsayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="8aefe-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="8aefe-141">Azure Cosmos DB veritabanları, diğer bir .NET uygulamasından gibi kapsayıcılarda, çalıştırılan .NET kodundan erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="8aefe-142">Örneğin, Azure Cosmos DB veritabanları kullandıkları için Locations.API ve Marketing.API mikro Hizmetleri hizmetine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="8aefe-143">Ancak, bir Docker geliştirme ortamı açısından Azure Cosmos DB'de bir sınırlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="8aefe-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="8aefe-144">Bir şirket içi olduğunda bile [Azure Cosmos DB öykünücüsü'nü](https://docs.microsoft.com/azure/cosmos-db/local-emulator) (bilgisayar gibi) bir yerel geliştirme makineniz çalıştırmak kullanabilir, geç 2017, yalnızca Windows, Linux olmayan destekler.</span><span class="sxs-lookup"><span data-stu-id="8aefe-144">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="8aefe-145">Docker, ancak yalnızca Windows kapsayıcıları hakkında Linux kapsayıcılarıyla bu öykünücüyü çalıştırmak için olasılık yoktur.</span><span class="sxs-lookup"><span data-stu-id="8aefe-145">There is also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="8aefe-146">Uygulamanızı Linux kapsayıcıları olarak bu yana, şu anda dağıtılırsa, geliştirme ortamı için bir başlangıç handicap, Linux ve Windows kapsayıcıları için Docker Windows üzerinde aynı anda dağıtamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8aefe-146">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="8aefe-147">Dağıtılan ya da tüm kapsayıcıları, Windows veya Linux için yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-147">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="8aefe-148">Çözüm Geliştirme/test için ideal ve daha basit dağıtım, geliştirme ve test ortamlarınızı her zaman tutarlı olacak şekilde özel kapsayıcılarınızı yanı sıra kapsayıcıları olarak dağıtabilir, veritabanı sistemleri sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-148">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="8aefe-149">Yerel geliştirme ve test Linux/Windows kapsayıcıları ayrıca Azure Cosmos DB için MongoDB API'si kullanma</span><span class="sxs-lookup"><span data-stu-id="8aefe-149">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="8aefe-150">Cosmos DB veritabanları, yerel MongoDB kablo protokolüne yanı sıra .NET için MongoDB API'si desteği.</span><span class="sxs-lookup"><span data-stu-id="8aefe-150">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="8aefe-151">MongoDB için yazılmış uygulamanız mevcut sürücüleri kullanarak artık Cosmos DB ile iletişim kurmak ve Cosmos DB veritabanı MongoDB veritabanları yerine, Şekil 7-20'de gösterildiği gibi kullanabilirsiniz. Bu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-151">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

<span data-ttu-id="8aefe-152">![Cosmos DB MongoDB API'si için .NET ve MongoDB kablo protokolünü destekler, Mongodb'den Cosmos DB'ye kolayca geçiş yapabilirsiniz. ](./media/image19.2.png)
 **Şekil 7-20**.</span><span class="sxs-lookup"><span data-stu-id="8aefe-152">![Cosmos DB supports MongoDB API for .NET and MongoDB wire protocol, you can easily switch from MongoDb to Cosmos DB.](./media/image19.2.png)
**Figure 7-20**.</span></span> <span data-ttu-id="8aefe-153">Azure Cosmos DB'ye erişmek için MongoDB API'si ve protokolü kullanma</span><span class="sxs-lookup"><span data-stu-id="8aefe-153">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="8aefe-154">Bunun nedeni Linux kapsayıcılar ile Docker ortamlarında kavramları kanıtı için kullanışlı bir yaklaşım, [MongoDB Docker görüntüsü](https://hub.docker.com/r/_/mongo/) Docker Linux kapsayıcıları ve Docker Windows kapsayıcıları destekleyen bir çok yay görüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="8aefe-154">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="8aefe-155">Aşağıdaki görüntüde gösterildiği gibi MongoDB API'sini kullanarak, yerel geliştirme ortamı için MongoDB, Linux ve Windows kapsayıcıları hizmetine destekler ancak daha sonra bir biçimde ölçeklendirilebilir, taşıyabilirsiniz PaaS olarak Azure Cosmos DB tarafından yalnızca bulut çözümünü [ Azure Cosmos DB'ye işaret edecek şekilde MongoDB bağlantı dizesini değiştirerek](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="8aefe-155">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="8aefe-156">![Konum mikro hizmetine MongoDB kullanılarak uygulanır, ancak Cosmos DB bağlantı dizesini değiştirerek değiştirilebilir. ](./media/image20-bis.png)
 **Şekil 7-21**.</span><span class="sxs-lookup"><span data-stu-id="8aefe-156">![The Location microservice in eShopOnContainers is implemented using MongoDB, but can be switched over to Cosmos DB by just changing the connection string.](./media/image20-bis.png)
**Figure 7-21**.</span></span> <span data-ttu-id="8aefe-157">Hizmetine üretim için dev-env veya Azure Cosmos DB için MongoDB kapsayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="8aefe-157">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="8aefe-158">Üretim Azure Cosmos DB, PaaS ve ölçeklenebilir bir hizmet olarak Azure'nın bulutta çalıştırıyordur.</span><span class="sxs-lookup"><span data-stu-id="8aefe-158">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="8aefe-159">Özel .NET Core kapsayıcılarınızı veya Kubernetes AKS Azure veya Azure Service Fabric gibi bir üretim ortamına dağıtılıp (kullanan için Docker Windows içinde bir Windows 10 makinesi) yerel geliştirme Docker konağı üzerinde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-159">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="8aefe-160">Azure Cosmos DB bulutta üretim verileri işlemek için kullanacağınızı olduğundan bu ikinci bir ortamda, yalnızca .NET Core özel kapsayıcılar ancak MongoDB kapsayıcı dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-160">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="8aefe-161">MongoDB API'sini kullanarak, açık bir avantajı, çözümünüzü farklı ortamlara geçişleri kolayca bu nedenle her iki veritabanı motorlarında, MongoDB veya Azure Cosmos DB, çalıştırabilir içindir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-161">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="8aefe-162">Ancak, bazen, belirli bir veritabanı altyapısı özellikleri tam olarak yararlanabilmek için (yani yerel Cosmos DB API) yerel bir API kullanmak faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="8aefe-162">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="8aefe-163">Yalnızca bulutta Cosmos DB ile MongoDB kullanarak arasında daha fazla karşılaştırması için bkz [bu sayfa, Azure Cosmos DB kullanmanın avantajları](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="8aefe-163">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span> 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="8aefe-164">Üretim uygulamaları için yaklaşımı analiz edin: MongoDB API'si vs. Cosmos DB API</span><span class="sxs-lookup"><span data-stu-id="8aefe-164">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="8aefe-165">Azure Cosmos DB ile de çalışabilir bir NoSQL veritabanı kullanarak bir tutarlı geliştirme ve test ortamı sağlamak için bizim önceliğimiz temelde olduğundan hizmetine MongoDB API'sini kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-165">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="8aefe-166">Ancak, varsa, üretim uygulamaları için Azure Cosmos DB azure'da erişmek için MongoDB API'sini kullanmayı planlama, özelliklerine ve performans farkı yerel kullanmaya kıyasla Azure Cosmos DB veritabanlarına erişmek için MongoDB API'si kullanılırken çözümlemeniz gerekir Azure Cosmos DB API.</span><span class="sxs-lookup"><span data-stu-id="8aefe-166">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="8aefe-167">Benzer ise MongoDB API'si kullanabilir ve aynı anda iki NoSQL veritabanı altyapılarını destekleyen avantajı alın.</span><span class="sxs-lookup"><span data-stu-id="8aefe-167">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="8aefe-168">Azure'nın bulutta üretim veritabanı olarak MongoDB kümeleri de kullanabilirsiniz, ile [Azure hizmet MongoDB](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="8aefe-168">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="8aefe-169">Ancak, Microsoft tarafından sağlanan bir PaaS hizmeti değil.</span><span class="sxs-lookup"><span data-stu-id="8aefe-169">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="8aefe-170">Bu durumda, Azure adresinden gelen bu çözüm yalnızca barındırma sağlayıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-170">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="8aefe-171">Temel olarak, yalnızca Linux kapsayıcıları için kullanışlı bir seçim olduğundan hizmetine yaptığımız gibi Azure Cosmos DB MongoDB API'si her zaman kullanmamalısınız belirten bir bildirim budur.</span><span class="sxs-lookup"><span data-stu-id="8aefe-171">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="8aefe-172">Karar üretim uygulamanız için gerçekleştirmeniz gereken testleri ve ihtiyaçlarınıza bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-172">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="8aefe-173">Kodu: MongoDB API'si, .NET Core uygulamalarında kullanma</span><span class="sxs-lookup"><span data-stu-id="8aefe-173">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="8aefe-174">MongoDB API'si için .NET Locations.API projesinde aşağıdaki şekilde gösterildiği gibi projenize eklemek için gereken NuGet paketlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-174">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![Bağımlılıklar MongoDB NuGet paketleri gösteren Çözüm Gezgini görünümü.](./media/image21-bis.png)

<span data-ttu-id="8aefe-176">**Şekil 7-22**.</span><span class="sxs-lookup"><span data-stu-id="8aefe-176">**Figure 7-22**.</span></span> <span data-ttu-id="8aefe-177">.NET Core projesi başvuruları MongoDB API NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="8aefe-177">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="8aefe-178">Şimdi aşağıdaki bölümlerde kodu inceleyin.</span><span class="sxs-lookup"><span data-stu-id="8aefe-178">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="8aefe-179">MongoDB API'si tarafından kullanılan bir Model</span><span class="sxs-lookup"><span data-stu-id="8aefe-179">A Model used by MongoDB API</span></span>

<span data-ttu-id="8aefe-180">İlk olarak, uygulamanızın bellek alanı veritabanından gelen verileri barındıracak bir modeli tanımlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-180">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="8aefe-181">Hizmetine konumları için kullanılan model örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-181">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="8aefe-182">Bazı öznitelikler ve MongoDB NuGet paketlerinden gelen türleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-182">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="8aefe-183">NoSQL veritabanları genellikle ilişkisel olmayan hiyerarşik veriler ile çalışmak için çok uygundur.</span><span class="sxs-lookup"><span data-stu-id="8aefe-183">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="8aefe-184">Bu örnekte, özellikle gibi coğrafi konumları için yapılan MongoDB türlerini kullanıyoruz `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="8aefe-184">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="8aefe-185">Veritabanı ve koleksiyonu alın</span><span class="sxs-lookup"><span data-stu-id="8aefe-185">Retrieve the database and the collection</span></span>

<span data-ttu-id="8aefe-186">Biz burada veritabanı ve aşağıdaki kodda gösterildiği gibi MongoCollections almak için kod uygulamak özel veritabanı bağlamında hizmetine oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="8aefe-186">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="8aefe-187">Veri alma</span><span class="sxs-lookup"><span data-stu-id="8aefe-187">Retrieve the data</span></span>

<span data-ttu-id="8aefe-188">C# kodunda, Web APİ'si denetleyicilerinin veya özel depolarda uygulaması gibi benzer kod şu şekilde MongoDB API'si sorgulanırken yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8aefe-188">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="8aefe-189">Unutmayın `_context` nesnedir, önceki örneği `LocationsContext` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8aefe-189">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="8aefe-190">MongoDB bağlantı dizesi için docker-compose.override.yml dosyasında bir env-var kullanın</span><span class="sxs-lookup"><span data-stu-id="8aefe-190">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="8aefe-191">MongoClient nesnesini oluştururken, tam olarak olan temel bir parametre gerekli `ConnectionString` doğru veritabanına işaret eden bir parametre.</span><span class="sxs-lookup"><span data-stu-id="8aefe-191">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="8aefe-192">Hizmetine söz konusu olduğunda, yerel bir MongoDB Docker kapsayıcısı veya "üretim" Azure Cosmos DB veritabanına bağlantı dizesi işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="8aefe-192">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="8aefe-193">Tanımlanan ortam değişkenleri Bu bağlantı dizesi geldiği `docker-compose.override.yml` docker-compose ya da Visual Studio ile olduğu gibi aşağıdaki yml kodu dağıtırken kullanılan dosyaları.</span><span class="sxs-lookup"><span data-stu-id="8aefe-193">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="8aefe-194">`ConnectionString` Ortam değişkeni bu şekilde çözümlendi: Varsa `ESHOP_AZURE_COSMOSDB` genel değişken tanımlanmış `.env` dosyası ile Azure Cosmos DB bağlantı dizesi, onu bulutta Azure Cosmos DB veritabanına erişmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-194">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="8aefe-195">Tanımlanmazsa, mongodb://nosql.data değeri ve geliştirme mongodb kapsayıcısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8aefe-195">If it’s not defined, it will take the mongodb://nosql.data value and use the development mongodb container.</span></span>

<span data-ttu-id="8aefe-196">Aşağıdaki kodda gösterildiği `.env` hizmetine uygulandığı şekilde Azure Cosmos DB bağlantı dizesi genel ortam değişkeni'ile dosya:</span><span class="sxs-lookup"><span data-stu-id="8aefe-196">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="8aefe-197">Azure Cosmos DB bağlantı dizenizi Azure portalından olarak elde edilen ile açıklanan güncelleştirmeyi ve ESHOP_AZURE_COSMOSDB satırı açıklamadan çıkarın [bir MongoDB uygulamasını Azure Cosmos DB'ye bağlanmak](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="8aefe-197">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="8aefe-198">Varsa `ESHOP_AZURE_COSMOSDB` genel değişkeni, out olarak geçersiz kılınan, yani, boş `.env` kapsayıcı adlıhizmetinedağıtılanyerelMongoDBkapsayıcısınıişaretedenbirvarsayılanMongoDBbağlantıdizesikullanır,dosya`nosql.data`ve docker-compose dosyasından aşağıdaki .yml kodda gösterildiği gibi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8aefe-198">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data` and was defined at the docker-compose file, as shown in the following .yml code.</span></span> 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="8aefe-199">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8aefe-199">Additional resources</span></span>

- <span data-ttu-id="8aefe-200">**NoSQL veritabanları için belge verilerini modelleme** \\</span><span class="sxs-lookup"><span data-stu-id="8aefe-200">**Modeling document data for NoSQL databases** \\</span></span>
  [*https://docs.microsoft.com/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/azure/cosmos-db/modeling-data)

- <span data-ttu-id="8aefe-201">**Vaughn Vernon. Ideal etki alanı Odaklı Tasarım toplama Store?**</span><span class="sxs-lookup"><span data-stu-id="8aefe-201">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="8aefe-202">**Azure Cosmos DB'ye giriş: MongoDB API'si**  \\</span><span class="sxs-lookup"><span data-stu-id="8aefe-202">**Introduction to Azure Cosmos DB: API for MongoDB**  \\</span></span>
  [*https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)

- <span data-ttu-id="8aefe-203">**Azure Cosmos DB: .NET ve Azure portalıyla bir MongoDB API'si web uygulaması derleme**  \\</span><span class="sxs-lookup"><span data-stu-id="8aefe-203">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  \\</span></span>
  [*https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet*](https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet )

- <span data-ttu-id="8aefe-204">**Yerel geliştirme ve test için Azure Cosmos DB öykünücüsü'nü kullanın**  \\</span><span class="sxs-lookup"><span data-stu-id="8aefe-204">**Use the Azure Cosmos DB Emulator for local development and testing**  \\</span></span>
  [*https://docs.microsoft.com/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/azure/cosmos-db/local-emulator)

- <span data-ttu-id="8aefe-205">**Bir MongoDB uygulamasını Azure Cosmos DB'ye bağlanma**  \\</span><span class="sxs-lookup"><span data-stu-id="8aefe-205">**Connect a MongoDB application to Azure Cosmos DB**  \\</span></span>
  [*https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)

- <span data-ttu-id="8aefe-206">**Cosmos DB öykünücüsü Docker görüntüsünü (Windows kapsayıcı)**  \\</span><span class="sxs-lookup"><span data-stu-id="8aefe-206">**The Cosmos DB Emulator Docker image (Windows Container)**  \\</span></span>
  [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)

- <span data-ttu-id="8aefe-207">**MongoDB Docker görüntü (Linux ve Windows kapsayıcı)**  \\</span><span class="sxs-lookup"><span data-stu-id="8aefe-207">**The MongoDB Docker image (Linux and Windows Container)**  \\</span></span>
  [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)

- <span data-ttu-id="8aefe-208">**MongoChef (Studio 3T), Azure Cosmos DB ile kullanın: MongoDB hesabı için API**  \\</span><span class="sxs-lookup"><span data-stu-id="8aefe-208">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  \\</span></span>
  [*https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef)

>[!div class="step-by-step"]
><span data-ttu-id="8aefe-209">[Önceki](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[İleri](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="8aefe-209">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>

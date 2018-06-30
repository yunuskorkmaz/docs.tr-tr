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
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="682ef-103">NoSQL veritabanı olarak Kalıcılık altyapısı kullanma</span><span class="sxs-lookup"><span data-stu-id="682ef-103">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="682ef-104">NoSQL veritabanları için altyapı veri katmanını kullandığınızda, Entity Framework Çekirdek gibi bir ORM genellikle kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="682ef-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="682ef-105">Bunun yerine Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB veya Azure depolama tabloları gibi NoSQL altyapısı tarafından sağlanan API kullanın.</span><span class="sxs-lookup"><span data-stu-id="682ef-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="682ef-106">Özellikle bir belge yönelimli veritabanı Azure Cosmos DB, CouchDB veya RavenDB, gibi bir NoSQL veritabanı kullandığınızda ancak modelinizi DDD toplamalar tasarlayın nasıl EF çekirdek gelince tanımlaması için bunu yapabilirsiniz için kısmen benzer yoludur Birleşik kökleri, alt sınıflar ve değer nesne sınıfları.</span><span class="sxs-lookup"><span data-stu-id="682ef-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="682ef-107">Ancak, veritabanı seçimi tasarımınızda nihayetinde etkiler.</span><span class="sxs-lookup"><span data-stu-id="682ef-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="682ef-108">Bir belge yönelimli veritabanı kullandığınızda, JSON veya başka bir biçimde serileştirilmiş tek bir belge olarak bir toplama uygulayın.</span><span class="sxs-lookup"><span data-stu-id="682ef-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="682ef-109">Ancak, bir etki alanı modeli kod açısından bakıldığında veritabanının kullanılmasını saydamdır.</span><span class="sxs-lookup"><span data-stu-id="682ef-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="682ef-110">Bir NoSQL veritabanı kullanırken, sınıflar ve birleşik kök sınıfları kullanmaya devam ancak EF çekirdek çünkü kullanırken'den daha fazla esneklik Kalıcılık ilişkisel değil.</span><span class="sxs-lookup"><span data-stu-id="682ef-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="682ef-111">Bu modelin nasıl kalıcı olarak farktır.</span><span class="sxs-lookup"><span data-stu-id="682ef-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="682ef-112">POCO varlık sınıflara göre etki alanı modeli uygulanırsa, farklı Kalıcılık altyapısına bile NoSQL ilişkisel taşıma gibi altyapı Kalıcılık belirsiz onu görünebilir.</span><span class="sxs-lookup"><span data-stu-id="682ef-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="682ef-113">Ancak, amacınız olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="682ef-113">However, that should not be your goal.</span></span> <span data-ttu-id="682ef-114">Her zaman kısıtlamaları farklı veritabanlarındaki itme, geri için aynı modeline sahip mümkün olmayacak şekilde ilişkisel veya NoSQL veritabanı.</span><span class="sxs-lookup"><span data-stu-id="682ef-114">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="682ef-115">İşlemler ve sürdürme işlemleri çok farklı olacağından Kalıcılık modelleri değiştirme Önemsiz, olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="682ef-115">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="682ef-116">Örneğin, bir belge yönelimli veritabanında birden çok alt koleksiyon özellikleri bir toplama kökü için sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="682ef-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="682ef-117">Bir birleşim tüm SQL deyimi EF geri alma ilişkisel bir veritabanında birden çok alt koleksiyon özellikleri sorgulama awful, çünkü.</span><span class="sxs-lookup"><span data-stu-id="682ef-117">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="682ef-118">İlişkisel veritabanları veya NoSQL veritabanları için aynı etki alanı modeline sahip basit değildir ve denemek.</span><span class="sxs-lookup"><span data-stu-id="682ef-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="682ef-119">Gerçekten anlayarak, her bir veritabanı içinde kullanılacak verileri nasıl gittiğini modelinizi tasarlamak sahip.</span><span class="sxs-lookup"><span data-stu-id="682ef-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="682ef-120">Bir tablo eşleme ayarlamayın NoSQL veritabanlarını kullanırken bir avantajı varlıkları daha Normalleştirilmemiş olduğundan.</span><span class="sxs-lookup"><span data-stu-id="682ef-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="682ef-121">Etki alanı modeli ilişkisel veritabanı kullanırken daha fazla esnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="682ef-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="682ef-122">Ne zaman için NoSQL taşıma etki alanı modelinizi toplamalarda, tasarım ve tasarım toplamalar benzer olduğundan belge yönelimli veritabanları ilişkisel veritabanı kullanmaktan daha kolay olabilir bir belge yönelimli veritabanı belgelerde seri.</span><span class="sxs-lookup"><span data-stu-id="682ef-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="682ef-123">Ardından bu "paketler" içinde bu toplama için gerekebilecek tüm bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="682ef-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="682ef-124">Örneğin, aşağıdaki JSON kodunu bir örnek bir sipariş toplama belge yönelimli bir veritabanı kullanılırken uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="682ef-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="682ef-125">Biz eShopOnContainers örnekteki ancak EF çekirdek altında kullanmadan uygulandığı sırayı toplama benzer.</span><span class="sxs-lookup"><span data-stu-id="682ef-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="682ef-126">Azure Cosmos DB ve yerel Cosmos DB API giriş</span><span class="sxs-lookup"><span data-stu-id="682ef-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="682ef-127">[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) görev açısından kritik uygulamalar için Microsoft'un Genel dağıtılmış veritabanı hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="682ef-127">[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="682ef-128">Azure Cosmos DB sağlar [anahtar teslim genel dağıtım](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [üretilen iş ve depolama esnek ölçeklendirme](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) 99, dünya çapında, tek basamaklı milisaniyelik gecikme [beş iyi tanımlanmış tutarlılık düzeylerini](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), yüksek oranda kullanılabilirlik, tarafından yedeklenen tüm garanti [endüstri lideri SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="682ef-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="682ef-129">Azure Cosmos DB [verileri otomatik olarak dizinler](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) gerektirmeden şema ve dizin yönetimi ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="682ef-129">Azure Cosmos DB [automatically indexes data](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="682ef-130">Birden çok model ve belge, anahtar-değer, grafik ve sütunlu veri modelleri destekler.</span><span class="sxs-lookup"><span data-stu-id="682ef-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

<span data-ttu-id="682ef-131">![](./media/image19.1.png) Şekil 9-19.</span><span class="sxs-lookup"><span data-stu-id="682ef-131">![](./media/image19.1.png) Figure 9-19.</span></span> <span data-ttu-id="682ef-132">Azure Cosmos DB genel dağıtım</span><span class="sxs-lookup"><span data-stu-id="682ef-132">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="682ef-133">Bir C kullandığınızda\# Azure Cosmos DB API'si tarafından toplama kullanılacak toplama uygulamak için model C benzer olabilir\# EF çekirdek ile kullanılan POCO sınıflar.</span><span class="sxs-lookup"><span data-stu-id="682ef-133">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="682ef-134">Aşağıdaki kod olduğu gibi uygulama ve altyapı katmanlardan kullanılacakları şekilde fark vardır:</span><span class="sxs-lookup"><span data-stu-id="682ef-134">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="682ef-135">Etki alanı modeliyle çalışacak şekilde benzer altyapı EF olduğunda, etki alanı modeli katmanda kullandığınız şekilde olabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="682ef-135">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="682ef-136">Hala tutarlılık, invariants ve toplama içinde doğrulamaları emin olmak için aynı toplama kök yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="682ef-136">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="682ef-137">Ancak, ne zaman, modelinizi NoSQL veritabanı, kod ve önemli ölçüde EF çekirdek kodu karşılaştırıldığında API değişiklik veya ilişkisel veritabanları için ilgili başka bir kod kalıcı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="682ef-137">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="682ef-138">.NET kodu MongoDB ve Azure Cosmos DB hedefleyen uygulama</span><span class="sxs-lookup"><span data-stu-id="682ef-138">Implementing .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="using-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="682ef-139">Azure Cosmos DB'den .NET kapsayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="682ef-139">Using Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="682ef-140">Diğer bir .NET uygulamasından gibi kapsayıcılara çalışan .NET kodundan Azure Cosmos DB veritabanları erişebilir.</span><span class="sxs-lookup"><span data-stu-id="682ef-140">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="682ef-141">Örneğin, Azure Cosmos DB veritabanları tüketebileceği şekilde eShopOnContainers Locations.API ve Marketing.API mikro hizmetler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="682ef-141">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="682ef-142">Ancak, açısından bir Docker geliştirme ortamı Azure Cosmos veritabanı bir sınırlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="682ef-142">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="682ef-143">Bir şirket içi olduğunda bile [Azure Cosmos DB öykünücüsü](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) kullanabilirsiniz (örneğin, bir bilgisayar) yerel geliştirme makinede çalıştırmak, geç 2017 yalnızca Windows, Linux değil destekliyorsa.</span><span class="sxs-lookup"><span data-stu-id="682ef-143">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="682ef-144">Ayrıca bu öykünücüsü Docker, ancak yalnızca Windows kapsayıcıları çalıştırmak için olasılığı vardır, not ile Linux kapsayıcıları.</span><span class="sxs-lookup"><span data-stu-id="682ef-144">There is also the possibility to run this emulator on Docker, but just on Windows Containers with the , not Linux Containers.</span></span> <span data-ttu-id="682ef-145">Uygulamanızı Linux kapsayıcılar olarak bu yana, şu anda dağıtılırsa, geliştirme ortamı için bir başlangıç handicap, Linux ve Windows kapsayıcıları için Docker Windows'da aynı anda dağıtamazsınız.</span><span class="sxs-lookup"><span data-stu-id="682ef-145">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="682ef-146">Dağıtılan ya da tüm kapsayıcıları Windows veya Linux için olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="682ef-146">Either all containers being deployed have to be for Linux or for Windows.</span></span>  

<span data-ttu-id="682ef-147">İdeal ve daha kolay bir geliştirme ve test çözümü için geliştirme ve test ortamları her zaman tutarlı şekilde veritabanı sistemlerinizi özel kapsayıcılarınızı birlikte kapsayıcı olarak dağıtabilmesi için dağıtımıdır.</span><span class="sxs-lookup"><span data-stu-id="682ef-147">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="682ef-148">Yerel geliştirme ve test Linux/Windows kapsayıcıları artı Azure Cosmos DB için MongoDB API kullanın</span><span class="sxs-lookup"><span data-stu-id="682ef-148">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="682ef-149">Cosmos DB veritabanları yerel MongoDB kablo protokolü yanı sıra .NET API MongoDB destekler.</span><span class="sxs-lookup"><span data-stu-id="682ef-149">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="682ef-150">MongoDB için yazılmış uygulamanızı mevcut sürücüleri kullanarak artık Cosmos DB ile iletişim kurmak ve Cosmos DB veritabanları MongoDB veritabanı yerine, Şekil 9-20'de gösterildiği gibi kullanın. Bu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="682ef-150">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 9-20.</span></span>

<span data-ttu-id="682ef-151">![](./media/image19.2.png) Şekil 9-20.</span><span class="sxs-lookup"><span data-stu-id="682ef-151">![](./media/image19.2.png) Figure 9-20.</span></span> <span data-ttu-id="682ef-152">MongoDB API ve protokolü kullanarak Azure Cosmos DB erişmek için</span><span class="sxs-lookup"><span data-stu-id="682ef-152">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="682ef-153">Bunun nedeni Linux kapsayıcılarla Docker ortamlarda kavramları kanıtı için çok uygun bir yaklaşım, [MongoDB Docker görüntü](https://hub.docker.com/r/_/mongo/) Docker Linux kapsayıcıları ve Docker Windows kapsayıcıları destekler çok yay bir görüntü.</span><span class="sxs-lookup"><span data-stu-id="682ef-153">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="682ef-154">9-21, görüntüde gösterildiği gibi MongoDB API'sini kullanarak eShopOnContainers yerel geliştirme ortamı için MongoDB Linux ve Windows kapsayıcıları destekler, ancak daha sonra bir biçimde ölçeklendirilebilir, taşıyabilirsiniz PaaS çözümü olarak Azure Cosmos DB tarafından yalnızca bulut [değiştirme Azure Cosmos Veritabanına işaret edecek şekilde MongoDB bağlantı dizesi](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="682ef-154">As shown in the image 9-21, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span> 

<span data-ttu-id="682ef-155">![](./media/image20-bis.png) Şekil 9-21.</span><span class="sxs-lookup"><span data-stu-id="682ef-155">![](./media/image20-bis.png) Figure 9-21.</span></span> <span data-ttu-id="682ef-156">eShopOnContainers üretim için geliştirme env ya da Azure Cosmos DB için MongoDB kapsayıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="682ef-156">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="682ef-157">Üretim Azure Cosmos DB Azure'un bulutta bir PaaS ve ölçeklenebilir hizmet olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="682ef-157">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="682ef-158">Özel .NET Core kapsayıcıları (Windows için Docker bir Windows 10 makinede kullanarak) bir yerel geliştirme Docker ana bilgisayarda çalıştırabilir veya Azure AKS veya Azure Service Fabric Kubernetes gibi bir üretim ortamına dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="682ef-158">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="682ef-159">Bu ikinci bir ortamda, yalnızca .NET çekirdeği özel kapsayıcılar ancak MongoDB kapsayıcı Azure Cosmos DB bulutta üretim verileri işlemek için kullanacağınızı beri dağıtımı.</span><span class="sxs-lookup"><span data-stu-id="682ef-159">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="682ef-160">MongoDB API kullanımının Temizle nedenle geçişler farklı ortamlar için kolay olmalıdır, çözümünüzün her iki veritabanı altyapıların, MongoDB ya da Azure Cosmos DB çalıştırabilir avantajdır.</span><span class="sxs-lookup"><span data-stu-id="682ef-160">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="682ef-161">Ancak, bazen onu belirli Veritabanı Altyapısı'nın özelliklerinden tam anlamıyla yararlanabilmek için (yani yerel Cosmos DB API) yerel bir API kullanmak için faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="682ef-161">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="682ef-162">Yalnızca bulutta MongoDB Cosmos DB karşı kullanarak arasında daha fazla karşılaştırma için bkz [bu sayfada Azure Cosmos DB kullanmanın yararları](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="682ef-162">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span></span> 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="682ef-163">Üretim uygulamaları için durum yaklaşımınızı analiz: MongoDB API vs. Cosmos DB API</span><span class="sxs-lookup"><span data-stu-id="682ef-163">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="682ef-164">Bizim öncelik Azure Cosmos DB ile de işe yarayabilir bir NoSQL veritabanı kullanarak tutarlı geliştirme ve test ortamı için temelde olduğundan eShopOnContainers biz MongoDB API kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="682ef-164">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="682ef-165">Ancak, üretim uygulamaları için Azure Cosmos Azure DB'de erişmek için MongoDB API kullanmak planlama, özellikleri ve performansı farklılıkları yerel kullanmaya kıyasla Azure Cosmos DB veritabanlarına erişim için MongoDB API'si kullanılırken çözümlemeniz gerekir, Azure Cosmos DB API.</span><span class="sxs-lookup"><span data-stu-id="682ef-165">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="682ef-166">Benzer ise MongoDB API'sini kullanabilirsiniz ve aynı anda iki NoSQL veritabanı altyapıları destekleme yararı alın.</span><span class="sxs-lookup"><span data-stu-id="682ef-166">If it is similar you can use MongoDB API, and you get the benefit of supporting two NoSQL database engines at the same time.</span></span> 

<span data-ttu-id="682ef-167">Azure'nın bulutta üretim veritabanı olarak Mongodb'yi kümeleri kullanabilirsiniz çok, ile [MongoDB Azure hizmet](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="682ef-167">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="682ef-168">Ancak, Microsoft tarafından sağlanan bir PaaS hizmeti değil.</span><span class="sxs-lookup"><span data-stu-id="682ef-168">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="682ef-169">Bu durumda, Azure adresinden gelen bu çözüm yalnızca barındırıyor.</span><span class="sxs-lookup"><span data-stu-id="682ef-169">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="682ef-170">Temel olarak, yalnızca Linux kapsayıcıları için kullanışlı bir seçim olduğundan içinde eShopOnContainers yaptığımız gibi Azure Cosmos DB karşı API MongoDB her zaman kullanmamanız belirten bir bildirim budur.</span><span class="sxs-lookup"><span data-stu-id="682ef-170">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="682ef-171">Karar belirli gereksinimleri ve üretim uygulamanız için gerçekleştirmeniz gereken testleri dayanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="682ef-171">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a><span data-ttu-id="682ef-172">Kod: MongoDB API .NET Core uygulamalarında kullanma</span><span class="sxs-lookup"><span data-stu-id="682ef-172">The code: Using MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="682ef-173">.NET için API MongoDB Şekil 9-22'de gösterilen Locations.API gibi projelerinizi eklemeniz gerekir NuGet paketlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="682ef-173">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like the Locations.API shown in Figure 9-22.</span></span>

<span data-ttu-id="682ef-174">![](./media/image21-bis.png) Şekil 9-22.</span><span class="sxs-lookup"><span data-stu-id="682ef-174">![](./media/image21-bis.png) Figure 9-22.</span></span> <span data-ttu-id="682ef-175">.NET Core projede başvuruları MongoDB API NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="682ef-175">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="682ef-176">Şimdi aşağıdaki bölümlerde kodda araştırın.</span><span class="sxs-lookup"><span data-stu-id="682ef-176">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="682ef-177">MongoDB API tarafından kullanılan bir modeli</span><span class="sxs-lookup"><span data-stu-id="682ef-177">A Model used by MongoDB API</span></span>

<span data-ttu-id="682ef-178">İlk olarak, uygulamanızın bellek alanı veritabanından gelen veriler tutacak bir model tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="682ef-178">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="682ef-179">EShopOnContainers konumları için kullanılan modelle bir örneği burada verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="682ef-179">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="682ef-180">Birkaç öznitelikleri ve MongoDB NuGet paketleri gelen türleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="682ef-180">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="682ef-181">NoSQL veritabanları genellikle ilişkisel olmayan hiyerarşik verilerle çalışmak için oldukça uygundur.</span><span class="sxs-lookup"><span data-stu-id="682ef-181">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="682ef-182">Bu örnekte, MongoDB türleri expecially gibi coğrafi konumları için yapılan kullanıyoruz `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="682ef-182">In this example, we are using MongoDB types expecially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="682ef-183">Veritabanı ve koleksiyonu alma</span><span class="sxs-lookup"><span data-stu-id="682ef-183">Retrieve the database and the collection</span></span>

<span data-ttu-id="682ef-184">Burada biz veritabanı ve aşağıdaki kodu olduğu gibi MongoCollections almak için kodu uygulayan bir özel veritabanı bağlamı eShopOnContainers içinde oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="682ef-184">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="682ef-185">Veri alma</span><span class="sxs-lookup"><span data-stu-id="682ef-185">Retrieve the data</span></span>

<span data-ttu-id="682ef-186">C# kod, Web API denetleyicilerinin veya özel depoları uygulama gibi benzer bir kod şu şekilde MongoDB API aracılığıyla sorgulanırken yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="682ef-186">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="682ef-187">Unutmayın `_context` nesnesidir önceki örneği `LocationsContext` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="682ef-187">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="682ef-188">MongoDB bağlantı dizesi için docker compose.override.yml dosyasında env var kullanın</span><span class="sxs-lookup"><span data-stu-id="682ef-188">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="682ef-189">MongoClient nesnesi oluşturulurken, tam olarak olan temel bir parametre gereken `ConnectionString` sağ veritabanına işaret eden parametresi.</span><span class="sxs-lookup"><span data-stu-id="682ef-189">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="682ef-190">EShopOnContainers söz konusu olduğunda bağlantı dizesi yerel MongoDB Docker kapsayıcısı veya "üretim" Azure Cosmos DB veritabanına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="682ef-190">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="682ef-191">Tanımlanan ortam değişkenleri bağlantı dizesini geldiği `docker-compose.override.yml` docker-compose ya da Visual Studio ile olduğu gibi aşağıdaki yml kod dağıtırken kullanılan dosyaları.</span><span class="sxs-lookup"><span data-stu-id="682ef-191">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="682ef-192">`ConnectionString` Ortam değişkeni bu şekilde çözümlendi: varsa `ESHOP_AZURE_COSMOSDB` genel değişkeni tanımlanmış `.env` dosya Azure Cosmos DB bağlantı dizesi ile onu bulutta Azure Cosmos DB veritabanına erişmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="682ef-192">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> 

<span data-ttu-id="682ef-193">Aşağıdaki kodda gösterildiği `.env` eShopOnContainers içinde uygulandığı şekilde Azure Cosmos DB bağlantı dizesi genel ortam değişkeni'ile dosya:</span><span class="sxs-lookup"><span data-stu-id="682ef-193">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="682ef-194">İçinde Azure portalından alınan Azure Cosmos DB bağlantı dizesi ile açıklanan güncelleştirmeyi ve ESHOP_AZURE_COSMOSDB satırı açıklamadan kaldırmasına [Azure Cosmos DB MongoDB uygulamaya bağlama](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="682ef-194">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="682ef-195">Varsa `ESHOP_AZURE_COSMOSDB` genel değişkeni, out olarak geçersiz kılınan, yani boş olduğundan, `.env` kapsayıcı adlandırılaneShopOnContainersdağıtılanyerelMongoDBkapsayıcıişaretedenbirvarsayılanMongoDBbağlantıdizesikullanıyorsa,dosya`nosql.data`aşağıdaki .yml kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="682ef-195">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data`, as shown in the following .yml code.</span></span> 

#### <a name="additional-resources"></a><span data-ttu-id="682ef-196">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="682ef-196">Additional resources</span></span>

-   <span data-ttu-id="682ef-197">**Belge verileri NoSQL veritabanları için modelleme**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span><span class="sxs-lookup"><span data-stu-id="682ef-197">**Modeling document data for NoSQL databases**
[*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span></span>

-   <span data-ttu-id="682ef-198">**Vaughn Vernon. Ideal etki alanı tabanlı tasarım toplama deposu?**
    [*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="682ef-198">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="682ef-199">**Azure Cosmos DB giriş: API MongoDB için** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span><span class="sxs-lookup"><span data-stu-id="682ef-199">**Introduction to Azure Cosmos DB: API for MongoDB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span></span>

-   <span data-ttu-id="682ef-200">**Azure Cosmos DB: .NET ve Azure portal ile bir MongoDB API web uygulaması oluşturma** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span><span class="sxs-lookup"><span data-stu-id="682ef-200">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span></span>

-   <span data-ttu-id="682ef-201">**Yerel geliştirme ve sınama için Azure Cosmos DB öykünücüsünü kullanma** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span><span class="sxs-lookup"><span data-stu-id="682ef-201">**Use the Azure Cosmos DB Emulator for local development and testing** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span></span>

-   <span data-ttu-id="682ef-202">**Azure Cosmos DB MongoDB uygulamaya bağlama** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span><span class="sxs-lookup"><span data-stu-id="682ef-202">**Connect a MongoDB application to Azure Cosmos DB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span></span>

-   <span data-ttu-id="682ef-203">**Cosmos DB öykünücüsü Docker görüntünün (Windows kapsayıcısı)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span><span class="sxs-lookup"><span data-stu-id="682ef-203">**The Cosmos DB Emulator Docker image (Windows Container)** 
[*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span></span>

-   <span data-ttu-id="682ef-204">**MongoDB Docker görüntünün (Linux ve Windows kapsayıcı)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span><span class="sxs-lookup"><span data-stu-id="682ef-204">**The MongoDB Docker image (Linux and Windows Container)** 
[*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span></span>

-   <span data-ttu-id="682ef-205">**Bir Azure Cosmos DB ile MongoChef (Studio 3T) kullanın: API MongoDB hesabı** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span><span class="sxs-lookup"><span data-stu-id="682ef-205">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="682ef-206">[Önceki](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[sonraki](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="682ef-206">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>

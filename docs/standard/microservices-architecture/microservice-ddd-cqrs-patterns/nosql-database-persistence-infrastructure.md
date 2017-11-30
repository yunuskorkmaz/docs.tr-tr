---
title: "NoSQL veritabanı olarak Kalıcılık altyapısı kullanma"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | NoSQL veritabanı olarak Kalıcılık altyapısı kullanma"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e4b63511069b89cc5761ce7ed64f09e9035a56a3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="1f7bc-104">NoSQL veritabanı olarak Kalıcılık altyapısı kullanma</span><span class="sxs-lookup"><span data-stu-id="1f7bc-104">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="1f7bc-105">NoSQL veritabanları için altyapı veri katmanını kullandığınızda, Entity Framework Çekirdek gibi bir ORM genellikle kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-105">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="1f7bc-106">Bunun yerine Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB veya Azure depolama tabloları gibi NoSQL altyapısı tarafından sağlanan API kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-106">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="1f7bc-107">Özellikle bir belge yönelimli veritabanı Azure Cosmos DB, CouchDB veya RavenDB, gibi bir NoSQL veritabanı kullandığınızda ancak modelinizi DDD toplamalar tasarlayın nasıl EF çekirdek gelince tanımlaması için bunu yapabilirsiniz için kısmen benzer yoludur Birleşik kökleri, alt sınıflar ve değer nesne sınıfları.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-107">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="1f7bc-108">Ancak, veritabanı seçimi tasarımınızda nihayetinde etkiler.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-108">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="1f7bc-109">Bir belge yönelimli veritabanı kullandığınızda, JSON veya başka bir biçimde serileştirilmiş tek bir belge olarak bir toplama uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-109">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="1f7bc-110">Ancak, bir etki alanı modeli kod açısından bakıldığında veritabanının kullanılmasını saydamdır.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-110">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="1f7bc-111">Bir NoSQL veritabanı kullanırken, sınıflar ve birleşik kök sınıfları kullanmaya devam ancak EF çekirdek çünkü kullanırken'den daha fazla esneklik Kalıcılık ilişkisel değil.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-111">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="1f7bc-112">Bu modelin nasıl kalıcı olarak farktır.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-112">The difference is in how you persist that model.</span></span> <span data-ttu-id="1f7bc-113">POCO varlık sınıflara göre etki alanı modeli uygulanırsa, farklı Kalıcılık altyapısına bile NoSQL ilişkisel taşıma gibi altyapı Kalıcılık belirsiz onu görünebilir.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-113">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="1f7bc-114">Ancak, amacınız olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-114">However, that should not be your goal.</span></span> <span data-ttu-id="1f7bc-115">Her zaman kısıtlamaları farklı veritabanlarındaki itme, geri için aynı modeline sahip mümkün olmayacak şekilde ilişkisel veya NoSQL veritabanı.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-115">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="1f7bc-116">İşlemler ve sürdürme işlemleri çok farklı olacağından Kalıcılık modelleri değiştirme Önemsiz, olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-116">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="1f7bc-117">Örneğin, bir belge yönelimli veritabanında birden çok alt koleksiyon özellikleri bir toplama kökü için sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-117">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="1f7bc-118">Bir birleşim tüm SQL deyimi EF geri alma ilişkisel bir veritabanında birden çok alt koleksiyon özellikleri sorgulama awful, çünkü.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-118">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="1f7bc-119">İlişkisel veritabanları veya NoSQL veritabanları için aynı etki alanı modeline sahip basit değildir ve denemek.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-119">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="1f7bc-120">Gerçekten anlayarak, her bir veritabanı içinde kullanılacak verileri nasıl gittiğini modelinizi tasarlamak sahip.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-120">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="1f7bc-121">Bir tablo eşleme ayarlamayın NoSQL veritabanlarını kullanırken bir avantajı varlıkları daha Normalleştirilmemiş olduğundan.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-121">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="1f7bc-122">Etki alanı modeli ilişkisel veritabanı kullanırken daha fazla esnek olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-122">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="1f7bc-123">Ne zaman için NoSQL taşıma etki alanı modelinizi toplamalarda, tasarım ve tasarım toplamalar benzer olduğundan belge yönelimli veritabanları ilişkisel veritabanı kullanmaktan daha kolay olabilir bir belge yönelimli veritabanı belgelerde seri.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-123">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="1f7bc-124">Ardından bu "paketler" içinde bu toplama için gerekebilecek tüm bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-124">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="1f7bc-125">Örneğin, aşağıdaki JSON kodunu bir örnek bir sipariş toplama belge yönelimli bir veritabanı kullanılırken uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-125">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="1f7bc-126">Biz eShopOnContainers örnekteki ancak EF çekirdek altında kullanmadan uygulandığı sırayı toplama benzer.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-126">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

<span data-ttu-id="1f7bc-127">Bir C kullandığınızda\# C için Azure Cosmos DB SDK toplama gibi bir şey tarafından kullanılmak üzere toplama uygulamak için model benzer\# EF çekirdek ile kullanılan POCO sınıflar.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-127">When you use a C\# model to implement the aggregate to be used by something like the Azure Cosmos DB SDK, the aggregate is similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="1f7bc-128">Aşağıdaki kod olduğu gibi uygulama ve altyapı katmanlardan kullanılacakları şekilde fark vardır:</span><span class="sxs-lookup"><span data-stu-id="1f7bc-128">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH DOCUMENTDB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).
// This can be saved as JSON as is without converting into rows/columns.
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

OrderItem orderItem2 = new OrderItem
{
    Id = 20170012,
    ProductId = "123457",
    ProductName = ".NET Mug",
    UnitPrice = 15,
    Units = 1,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);

// *** End of Domain Model Code ***
//...
// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, order);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="1f7bc-129">Etki alanı modeliyle çalışacak şekilde benzer altyapı EF olduğunda, etki alanı modeli katmanda kullandığınız şekilde olabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-129">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="1f7bc-130">Hala tutarlılık, invariants ve toplama içinde doğrulamaları emin olmak için aynı toplama kök yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-130">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="1f7bc-131">Ancak, ne zaman, modelinizi NoSQL veritabanı, kod ve önemli ölçüde EF çekirdek kodu karşılaştırıldığında API değişiklik veya ilişkisel veritabanları için ilgili başka bir kod kalıcı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-131">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1f7bc-132">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1f7bc-132">Additional resources</span></span>

-   <span data-ttu-id="1f7bc-133">**Modelleme verileri documentdb'de**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span><span class="sxs-lookup"><span data-stu-id="1f7bc-133">**Modeling data in DocumentDB**
[*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span></span>

-   <span data-ttu-id="1f7bc-134">**Vaughn Vernon. Ideal etki alanı tabanlı tasarım toplama deposu? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="1f7bc-134">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="1f7bc-135">**Kalıcılık belirsiz .NET için olay deposu.**</span><span class="sxs-lookup"><span data-stu-id="1f7bc-135">**A persistence agnostic Event Store for .NET.**</span></span> <span data-ttu-id="1f7bc-136">GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="1f7bc-136">GitHub repo.</span></span>
    [<span data-ttu-id="1f7bc-137">*https://github.com/NEventStore/NEventStore*</span><span class="sxs-lookup"><span data-stu-id="1f7bc-137">*https://github.com/NEventStore/NEventStore*</span></span>](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
<span data-ttu-id="1f7bc-138">[Önceki] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [sonraki] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="1f7bc-138">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>

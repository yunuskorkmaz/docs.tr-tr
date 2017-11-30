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

Bir C kullandığınızda\# C için Azure Cosmos DB SDK toplama gibi bir şey tarafından kullanılmak üzere toplama uygulamak için model benzer\# EF çekirdek ile kullanılan POCO sınıflar. Aşağıdaki kod olduğu gibi uygulama ve altyapı katmanlardan kullanılacakları şekilde fark vardır:

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

Etki alanı modeliyle çalışacak şekilde benzer altyapı EF olduğunda, etki alanı modeli katmanda kullandığınız şekilde olabileceğini görebilirsiniz. Hala tutarlılık, invariants ve toplama içinde doğrulamaları emin olmak için aynı toplama kök yöntemlerini kullanın.

Ancak, ne zaman, modelinizi NoSQL veritabanı, kod ve önemli ölçüde EF çekirdek kodu karşılaştırıldığında API değişiklik veya ilişkisel veritabanları için ilgili başka bir kod kalıcı olmasını sağlar.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Modelleme verileri documentdb'de**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)

-   **Vaughn Vernon. Ideal etki alanı tabanlı tasarım toplama deposu? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Kalıcılık belirsiz .NET için olay deposu.** GitHub depo.
    [*https://github.com/NEventStore/NEventStore*](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
[Önceki] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [sonraki] (microservice-application-layer-web-api-design.md)

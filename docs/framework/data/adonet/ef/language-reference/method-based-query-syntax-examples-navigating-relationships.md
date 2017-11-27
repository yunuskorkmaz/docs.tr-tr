---
title: "Yöntem temelli sorgu sözdizimi örnekler: İlişkilerinde gezinme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c7c5e1c17fbb0758cc395b6a76b7c0d1065be04a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="81e8f-102">Yöntem temelli sorgu sözdizimi örnekler: İlişkilerinde gezinme</span><span class="sxs-lookup"><span data-stu-id="81e8f-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="81e8f-103">Gezinti özelliklerinde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ilişkilendirme ucunun varlıkları bulmak için kullanılan kısayol özellik.</span><span class="sxs-lookup"><span data-stu-id="81e8f-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="81e8f-104">Gezinti özellikleri bir kullanıcının başka bir varlıktan gidin veya bir ilişki ile ilgili varlıklar için bir varlık kümesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="81e8f-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="81e8f-105">Bu konu, gezinti özellikleri sayesinde ilişkilerini gitmek nasıl yöntemi tabanlı sorgu sözdiziminde örnekleri sağlar [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="81e8f-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="81e8f-106">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="81e8f-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="81e8f-107">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="81e8f-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="81e8f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="81e8f-108">Example</span></span>  
 <span data-ttu-id="81e8f-109">Yöntem temelli sorgu sözdizimini kullanır aşağıdaki örnekte <xref:System.Linq.Queryable.SelectMany%2A> Soyadı kişilerin tüm siparişleri almak için yöntemi olduğu "Zhou".</span><span class="sxs-lookup"><span data-stu-id="81e8f-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="81e8f-110">`Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için.</span><span class="sxs-lookup"><span data-stu-id="81e8f-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="81e8f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="81e8f-111">Example</span></span>  
 <span data-ttu-id="81e8f-112">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte kullanır <xref:System.Linq.Queryable.Select%2A> tüm kişi kimliklerini almak için yöntemi ve her kişi için Soyadı toplam süre "Zhou" toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="81e8f-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="81e8f-113">`Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için.</span><span class="sxs-lookup"><span data-stu-id="81e8f-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="81e8f-114">`Sum` Yöntemi kullanan `Contact.SalesOrderHeader` toplam toplanacak gezinti özelliği her kişi için tüm sipariş sonu.</span><span class="sxs-lookup"><span data-stu-id="81e8f-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="81e8f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="81e8f-115">Example</span></span>  
 <span data-ttu-id="81e8f-116">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte "Zhou" Soyadı olan kişileri tüm siparişleri alır.</span><span class="sxs-lookup"><span data-stu-id="81e8f-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="81e8f-117">`Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için.</span><span class="sxs-lookup"><span data-stu-id="81e8f-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="81e8f-118">Kişinin adı ve siparişleri anonim bir tür döndürür.</span><span class="sxs-lookup"><span data-stu-id="81e8f-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="81e8f-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="81e8f-119">Example</span></span>  
 <span data-ttu-id="81e8f-120">Aşağıdaki örnek kullanır `SalesOrderHeader.Address` ve `SalesOrderHeader.Contact` Gezinti özellikleri koleksiyonunu alma `Address` ve `Contact` nesneleri her sipariş ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="81e8f-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="81e8f-121">Her biri Şehir Seattle siparişe döndürülür için anonim bir tür Soyadı ilgili kişi, adres sayısı ve toplam süre satış siparişi.</span><span class="sxs-lookup"><span data-stu-id="81e8f-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="81e8f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="81e8f-122">Example</span></span>  
 <span data-ttu-id="81e8f-123">Aşağıdaki örnek kullanır `Where` 1 Aralık 2003'ten sonra yapılan siparişleri bulmak için yöntem ve kullandığı `order.SalesOrderDetail` her sipariş için ayrıntıları almak için gezinme özelliği.</span><span class="sxs-lookup"><span data-stu-id="81e8f-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="81e8f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81e8f-124">See Also</span></span>  
 [<span data-ttu-id="81e8f-125">Gezinti özellikleri</span><span class="sxs-lookup"><span data-stu-id="81e8f-125">Navigation Properties</span></span>](http://msdn.microsoft.com/en-us/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
 [<span data-ttu-id="81e8f-126">LINQ to Entities sorguları</span><span class="sxs-lookup"><span data-stu-id="81e8f-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

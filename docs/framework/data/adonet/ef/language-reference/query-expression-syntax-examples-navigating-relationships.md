---
title: "Sorgu ifade sözdizimi örnekleri: İlişkilerinde gezinme"
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
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c029ce130e0bc8a6f959c6c27d863422794c22e5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="65acb-102">Sorgu ifade sözdizimi örnekleri: İlişkilerinde gezinme</span><span class="sxs-lookup"><span data-stu-id="65acb-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="65acb-103">Gezinti özelliklerinde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ilişkilendirme ucunun varlıkları bulmak için kullanılan kısayol özellik.</span><span class="sxs-lookup"><span data-stu-id="65acb-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="65acb-104">Gezinti özellikleri bir kullanıcının başka bir varlıktan gidin veya bir ilişki ile ilgili varlıklar için bir varlık kümesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="65acb-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="65acb-105">Bu konu, gezinti özellikleri sayesinde ilişkilerini gitmek nasıl sorgu ifade sözdizimi örnekleri sağlar [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="65acb-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="65acb-106">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="65acb-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="65acb-107">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="65acb-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="65acb-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="65acb-108">Example</span></span>  
 <span data-ttu-id="65acb-109">Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.Select%2A> tüm kişi kimliklerini almak için yöntemi ve her kişi için Soyadı toplam süre "Zhou" toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="65acb-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="65acb-110">`Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için.</span><span class="sxs-lookup"><span data-stu-id="65acb-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="65acb-111">`Sum` Yöntemi kullanan `Contact.SalesOrderHeader` toplam toplanacak gezinti özelliği her kişi için tüm sipariş sonu.</span><span class="sxs-lookup"><span data-stu-id="65acb-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="65acb-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="65acb-112">Example</span></span>  
 <span data-ttu-id="65acb-113">Aşağıdaki örnekte "Zhou" Soyadı olan kişileri tüm siparişleri alır.</span><span class="sxs-lookup"><span data-stu-id="65acb-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="65acb-114">`Contact.SalesOrderHeader` Gezinti özelliği koleksiyonunu alma için kullanılan `SalesOrderHeader` nesneler her kişi için.</span><span class="sxs-lookup"><span data-stu-id="65acb-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="65acb-115">Kişinin adı ve siparişleri anonim bir tür döndürür.</span><span class="sxs-lookup"><span data-stu-id="65acb-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="65acb-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="65acb-116">Example</span></span>  
 <span data-ttu-id="65acb-117">Aşağıdaki örnek kullanır `SalesOrderHeader.Address` ve `SalesOrderHeader.Contact` Gezinti özellikleri koleksiyonunu alma `Address` ve `Contact` nesneleri her sipariş ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="65acb-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="65acb-118">Her biri Şehir Seattle siparişe döndürülür için anonim bir tür Soyadı ilgili kişi, adres sayısı ve toplam süre satış siparişi.</span><span class="sxs-lookup"><span data-stu-id="65acb-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="65acb-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="65acb-119">Example</span></span>  
 <span data-ttu-id="65acb-120">Aşağıdaki örnek kullanır `Where` 1 Aralık 2003'ten sonra yapılan siparişleri bulmak için yöntem ve kullandığı `order.SalesOrderDetail` her sipariş için ayrıntıları almak için gezinme özelliği.</span><span class="sxs-lookup"><span data-stu-id="65acb-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="65acb-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65acb-121">See Also</span></span>  
 [<span data-ttu-id="65acb-122">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="65acb-122">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

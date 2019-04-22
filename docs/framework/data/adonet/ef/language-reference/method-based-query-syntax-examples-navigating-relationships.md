---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: İlişkilerde Geziniliyor'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 87f8132fc8bc9d64fb02a78bc38d1261db032b5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138809"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="8af11-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: İlişkilerde Geziniliyor</span><span class="sxs-lookup"><span data-stu-id="8af11-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="8af11-103">Gezinti özellikleri [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ilişkilendirme ucunda varlıkları bulmak için kullanılan kısayol özellik.</span><span class="sxs-lookup"><span data-stu-id="8af11-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="8af11-104">Bir varlıktan diğerine giderler veya ilgili varlıkları ilişkilendirme aracılığıyla tek bir varlık kümesi bir kullanıcı Gezinti özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8af11-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="8af11-105">Metot tabanlı sorgu söz dizimi örnekleri Gezinti özellikleri ile ilişkilerde gezinme konusunda bu konuda sunmaktadır [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="8af11-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="8af11-106">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8af11-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8af11-107">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="8af11-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="8af11-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af11-108">Example</span></span>  
 <span data-ttu-id="8af11-109">Metot tabanlı sorgu söz dizimi kullanan aşağıdaki örnekte <xref:System.Linq.Queryable.SelectMany%2A> Soyadı tüm siparişleri kişileri almak için yöntemi olan "Zhou".</span><span class="sxs-lookup"><span data-stu-id="8af11-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="8af11-110">`Contact.SalesOrderHeader` Koleksiyonu almak için kullanılan gezinme özelliği `SalesOrderHeader` her kişi için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8af11-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="8af11-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af11-111">Example</span></span>  
 <span data-ttu-id="8af11-112">Metot tabanlı sorgu söz dizimi aşağıdaki örnekte kullanan <xref:System.Linq.Queryable.Select%2A> tüm kişi kimliklerini almak için yöntemi ve Soyadı her kişi için toplam süre "Zhou" toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="8af11-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="8af11-113">`Contact.SalesOrderHeader` Koleksiyonu almak için kullanılan gezinme özelliği `SalesOrderHeader` her kişi için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8af11-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="8af11-114">`Sum` Yöntemi kullanan `Contact.SalesOrderHeader` toplam toplamak için gezinme özelliği her kişi için tüm siparişleri son.</span><span class="sxs-lookup"><span data-stu-id="8af11-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="8af11-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af11-115">Example</span></span>  
 <span data-ttu-id="8af11-116">Metot tabanlı sorgu söz dizimi aşağıdaki örnekte, "Zhou" Soyadı olan kişileri tüm siparişleri alır.</span><span class="sxs-lookup"><span data-stu-id="8af11-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="8af11-117">`Contact.SalesOrderHeader` Koleksiyonu almak için kullanılan gezinme özelliği `SalesOrderHeader` her kişi için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8af11-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="8af11-118">Kişinin adı ve sipariş anonim bir tür döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8af11-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="8af11-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af11-119">Example</span></span>  
 <span data-ttu-id="8af11-120">Aşağıdaki örnekte `SalesOrderHeader.Address` ve `SalesOrderHeader.Contact` koleksiyonu almak için Gezinti özellikleri `Address` ve `Contact` her siparişle ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8af11-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="8af11-121">Her bir siparişe şehri Seattle döndürülür için anonim bir tür içinde olan sokak adresi kişinin soyadı sayısı ve toplam süre satış siparişi.</span><span class="sxs-lookup"><span data-stu-id="8af11-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="8af11-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="8af11-122">Example</span></span>  
 <span data-ttu-id="8af11-123">Aşağıdaki örnekte `Where` 1 Aralık 2003 sonra yapıldığı siparişleri bulmak için yöntem ve kullandığı `order.SalesOrderDetail` her siparişi için ayrıntıları almak için gezinme özelliği.</span><span class="sxs-lookup"><span data-stu-id="8af11-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="8af11-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8af11-124">See also</span></span>

- [<span data-ttu-id="8af11-125">İlişkiler, gezinti özellikleri ve yabancı anahtarlar</span><span class="sxs-lookup"><span data-stu-id="8af11-125">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="8af11-126">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="8af11-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

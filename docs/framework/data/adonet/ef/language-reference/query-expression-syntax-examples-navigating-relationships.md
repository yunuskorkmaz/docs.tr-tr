---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Geziniliyor'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: 2133ae7902cc4746e00be75e7a801296073041e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614290"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="4b741-102">Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Geziniliyor</span><span class="sxs-lookup"><span data-stu-id="4b741-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="4b741-103">Gezinti özellikleri [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ilişkilendirme ucunda varlıkları bulmak için kullanılan kısayol özellik.</span><span class="sxs-lookup"><span data-stu-id="4b741-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="4b741-104">Bir varlıktan diğerine giderler veya ilgili varlıkları ilişkilendirme aracılığıyla tek bir varlık kümesi bir kullanıcı Gezinti özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b741-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="4b741-105">Bu konuda sorgu ifadesi söz dizimi örnekleri Gezinti özellikleri ile ilişkilerde gezinme konusunda sunmaktadır [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="4b741-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="4b741-106">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4b741-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4b741-107">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="4b741-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="4b741-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b741-108">Example</span></span>  
 <span data-ttu-id="4b741-109">Aşağıdaki örnekte <xref:System.Linq.Queryable.Select%2A> tüm kişi kimliklerini almak için yöntemi ve Soyadı her kişi için toplam süre "Zhou" toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="4b741-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="4b741-110">`Contact.SalesOrderHeader` Koleksiyonu almak için kullanılan gezinme özelliği `SalesOrderHeader` her kişi için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4b741-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="4b741-111">`Sum` Yöntemi kullanan `Contact.SalesOrderHeader` toplam toplamak için gezinme özelliği her kişi için tüm siparişleri son.</span><span class="sxs-lookup"><span data-stu-id="4b741-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="4b741-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b741-112">Example</span></span>  
 <span data-ttu-id="4b741-113">Aşağıdaki örnek, "Zhou" Soyadı olan kişileri tüm siparişleri alır.</span><span class="sxs-lookup"><span data-stu-id="4b741-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="4b741-114">`Contact.SalesOrderHeader` Koleksiyonu almak için kullanılan gezinme özelliği `SalesOrderHeader` her kişi için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4b741-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="4b741-115">Kişinin adı ve sipariş anonim bir tür döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4b741-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="4b741-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b741-116">Example</span></span>  
 <span data-ttu-id="4b741-117">Aşağıdaki örnekte `SalesOrderHeader.Address` ve `SalesOrderHeader.Contact` Gezinti özelliklerini alma koleksiyonu `Address` ve `Contact` her siparişle ilişkili nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4b741-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="4b741-118">Her bir siparişe şehri Seattle döndürülür için anonim bir tür içinde olan sokak adresi kişinin soyadı sayısı ve toplam süre satış siparişi.</span><span class="sxs-lookup"><span data-stu-id="4b741-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="4b741-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b741-119">Example</span></span>  
 <span data-ttu-id="4b741-120">Aşağıdaki örnekte `Where` 1 Aralık 2003 sonra yapıldığı siparişleri bulmak için yöntem ve kullandığı `order.SalesOrderDetail` her siparişi için ayrıntıları almak için gezinme özelliği.</span><span class="sxs-lookup"><span data-stu-id="4b741-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="4b741-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b741-121">See also</span></span>

- [<span data-ttu-id="4b741-122">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="4b741-122">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Gezinme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: c09a0458f5b0b7d313da3379b5dda9b969eaf7e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156803"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="9e935-102">Sorgu İfadesi Söz Dizimi Örnekleri: İlişkilerde Gezinme</span><span class="sxs-lookup"><span data-stu-id="9e935-102">Query Expression Syntax Examples: Navigating Relationships</span></span>

<span data-ttu-id="9e935-103">Entity Framework gezinti özellikleri, varlıkların sonunda varlıkların yerini bulmak için kullanılan kısayol özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="9e935-103">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="9e935-104">Gezinti özellikleri, bir kullanıcının bir varlıktan diğerine veya bir varlıktan bir ilişki kümesi aracılığıyla ilgili varlıklara dolaşmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e935-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="9e935-105">Bu konuda, LINQ to Entities sorgularda gezinti özellikleri aracılığıyla ilişkilerde nasıl geziniminin sorgu ifadesi sözdiziminde örnekler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e935-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="9e935-106">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9e935-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9e935-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="9e935-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="9e935-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e935-108">Example</span></span>  

 <span data-ttu-id="9e935-109">Aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> son adı "Zhou" olan her kişi için tüm Iletişim kimliklerini ve toplam toplamını almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e935-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="9e935-110">`Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="9e935-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="9e935-111">`Sum`Yöntemi, her bir `Contact.SalesOrderHeader` kişi için tüm siparişlerin ödenmesi gereken toplam miktarı toplamak için gezinti özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e935-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="9e935-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e935-112">Example</span></span>  

 <span data-ttu-id="9e935-113">Aşağıdaki örnek, son adı "Zhou" olan kişilerin tüm emirlerini alır.</span><span class="sxs-lookup"><span data-stu-id="9e935-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="9e935-114">`Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="9e935-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="9e935-115">Kişinin adı ve siparişleri anonim bir türde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9e935-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="9e935-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e935-116">Example</span></span>  

 <span data-ttu-id="9e935-117">Aşağıdaki örnek, `SalesOrderHeader.Address` ve ' `SalesOrderHeader.Contact` nin `Address` her bir `Contact` siparişle ilişkili nesneleri ve koleksiyonunu al ve gezinti özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e935-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="9e935-118">Kişinin Soyadı, sokak adresi, satış siparişi numarası ve Seattle şehrine yönelik her bir sipariş için bir anonim türde döndürülen toplam ad.</span><span class="sxs-lookup"><span data-stu-id="9e935-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="9e935-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e935-119">Example</span></span>  

 <span data-ttu-id="9e935-120">Aşağıdaki örnek, `Where` 1 aralık 2003 ' den sonra yapılan siparişleri bulmak için yöntemini kullanır ve ardından `order.SalesOrderDetail` her bir siparişin ayrıntılarını almak için gezinti özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e935-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="9e935-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e935-121">See also</span></span>

- [<span data-ttu-id="9e935-122">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="9e935-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

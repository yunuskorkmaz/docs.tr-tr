---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: İlişkilerde Gezinme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: bb40d10165592b25cc6afc1eac799a05b4504e8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191976"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="269cd-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: İlişkilerde Gezinme</span><span class="sxs-lookup"><span data-stu-id="269cd-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>

<span data-ttu-id="269cd-103">Entity Framework gezinti özellikleri, varlıkların sonunda varlıkların yerini bulmak için kullanılan kısayol özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="269cd-103">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="269cd-104">Gezinti özellikleri, bir kullanıcının bir varlıktan diğerine veya bir varlıktan bir ilişki kümesi aracılığıyla ilgili varlıklara dolaşmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="269cd-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="269cd-105">Bu konu, LINQ to Entities sorgularda gezinti özellikleri aracılığıyla ilişkilerde nasıl geziniminin Yöntem tabanlı sorgu söz dizimine örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="269cd-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="269cd-106">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="269cd-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="269cd-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="269cd-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="269cd-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="269cd-108">Example</span></span>  

 <span data-ttu-id="269cd-109">Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, <xref:System.Linq.Queryable.SelectMany%2A> son adı "Zhou" olan kişilerin tüm emirlerini almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="269cd-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="269cd-110">`Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="269cd-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="269cd-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="269cd-111">Example</span></span>  

 <span data-ttu-id="269cd-112">Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> son adı "Zhou" olan her kişi için tüm Iletişim kimliklerini ve toplam toplamı almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="269cd-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="269cd-113">`Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="269cd-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="269cd-114">`Sum`Yöntemi, her bir `Contact.SalesOrderHeader` kişi için tüm siparişlerin ödenmesi gereken toplam miktarı toplamak için gezinti özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="269cd-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="269cd-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="269cd-115">Example</span></span>  

 <span data-ttu-id="269cd-116">Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, son adı "Zhou" olan kişilerin tüm emirlerini alır.</span><span class="sxs-lookup"><span data-stu-id="269cd-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="269cd-117">`Contact.SalesOrderHeader`Gezinti özelliği, her bir kişinin nesne koleksiyonunu almak için kullanılır `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="269cd-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="269cd-118">Kişinin adı ve siparişleri anonim bir türde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="269cd-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="269cd-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="269cd-119">Example</span></span>  

 <span data-ttu-id="269cd-120">Aşağıdaki örnek, ve ' `SalesOrderHeader.Address` `SalesOrderHeader.Contact` nin `Address` `Contact` her bir siparişle ilişkili nesneleri ve koleksiyonunu almak için ve gezinti özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="269cd-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="269cd-121">Kişinin Soyadı, sokak adresi, satış siparişi numarası ve Seattle şehrine yönelik her bir sipariş için bir anonim türde döndürülen toplam ad.</span><span class="sxs-lookup"><span data-stu-id="269cd-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="269cd-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="269cd-122">Example</span></span>  

 <span data-ttu-id="269cd-123">Aşağıdaki örnek, `Where` 1 aralık 2003 ' den sonra yapılan siparişleri bulmak için yöntemini kullanır ve ardından `order.SalesOrderDetail` her bir siparişin ayrıntılarını almak için gezinti özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="269cd-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="269cd-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="269cd-124">See also</span></span>

- [<span data-ttu-id="269cd-125">İlişkiler, gezinti özellikleri ve yabancı anahtarlar</span><span class="sxs-lookup"><span data-stu-id="269cd-125">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="269cd-126">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="269cd-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

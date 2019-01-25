---
title: 'Sorgu ifadesi söz dizimi örnekleri: Projeksiyon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: c12fdd70b7174d6e6fbae10d5132c9e3e2a7eb87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733382"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="88929-102">Sorgu ifadesi söz dizimi örnekleri: Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="88929-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="88929-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `Select` yöntemi ve `From … From …` sorgu anahtar sözcükleri [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="88929-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="88929-104">`From … From …` eşdeğerdir sorgu tabanlı, `SelectMany` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="88929-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="88929-105">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="88929-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="88929-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="88929-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="88929-107">Seçim</span><span class="sxs-lookup"><span data-stu-id="88929-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="88929-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="88929-108">Example</span></span>  
 <span data-ttu-id="88929-109">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek yöntemi `Product` tablo ve ürün adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88929-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="88929-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="88929-110">Example</span></span>  
 <span data-ttu-id="88929-111">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adlarını bir dizisini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="88929-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="88929-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="88929-112">Example</span></span>  
 <span data-ttu-id="88929-113">Aşağıdaki örnekte <xref:System.Linq.Queryable.Select%2A> projesine yöntemi `Product.Name` ve `Product.ProductID` anonim türler dizisini özellikleri.</span><span class="sxs-lookup"><span data-stu-id="88929-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="88929-114">Kaynak...</span><span class="sxs-lookup"><span data-stu-id="88929-114">From …</span></span> <span data-ttu-id="88929-115">Kaynak...</span><span class="sxs-lookup"><span data-stu-id="88929-115">From …</span></span> <span data-ttu-id="88929-116">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="88929-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="88929-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="88929-117">Example</span></span>  
 <span data-ttu-id="88929-118">Aşağıdaki örnekte `From … From …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) tümünü seçmek için nereye siparişleri `TotalDue` kısa da 500,00 olduğu.</span><span class="sxs-lookup"><span data-stu-id="88929-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="88929-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="88929-119">Example</span></span>  
 <span data-ttu-id="88929-120">Aşağıdaki örnekte `From … From …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) burada sırasını yapıldı 1 Ekim 2002 veya daha sonra tüm siparişleri seçin.</span><span class="sxs-lookup"><span data-stu-id="88929-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="88929-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="88929-121">Example</span></span>  
 <span data-ttu-id="88929-122">Aşağıdaki örnekte bir `From … From …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) tüm siparişleri sipariş toplam olduğu 10000.00 kullanan'dan büyük ve seçmek için `From` toplam iki kez isteyen önlemek için atama.</span><span class="sxs-lookup"><span data-stu-id="88929-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="88929-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88929-123">See also</span></span>
- [<span data-ttu-id="88929-124">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="88929-124">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

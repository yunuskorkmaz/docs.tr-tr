---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: 82395b79cb5b2834a79356cbdfb1087603a9ae77
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175583"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="3a3b7-102">Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="3a3b7-102">Query Expression Syntax Examples: Projection</span></span>

<span data-ttu-id="3a3b7-103">Bu konudaki örneklerde, `Select` `From … From …` sorgu ifadesi söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin ve anahtar sözcüklerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a3b7-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="3a3b7-104">`From … From …` , yönteminin sorgu tabanlı eşdeğeri olur `SelectMany` .</span><span class="sxs-lookup"><span data-stu-id="3a3b7-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="3a3b7-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="3a3b7-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3a3b7-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="3a3b7-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="3a3b7-107">Şunu seçin:</span><span class="sxs-lookup"><span data-stu-id="3a3b7-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="3a3b7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a3b7-108">Example</span></span>  

 <span data-ttu-id="3a3b7-109">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Select%2A> tablodaki tüm satırları döndürmek `Product` ve ürün adlarını göstermek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a3b7-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="3a3b7-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a3b7-110">Example</span></span>  

 <span data-ttu-id="3a3b7-111">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adlarından oluşan bir dizi döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a3b7-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="3a3b7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a3b7-112">Example</span></span>  

 <span data-ttu-id="3a3b7-113">Aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> `Product.Name` ve `Product.ProductID` özelliklerini bir anonim türler dizisi halinde proje yapmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a3b7-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="3a3b7-114">Kaynak...</span><span class="sxs-lookup"><span data-stu-id="3a3b7-114">From …</span></span> <span data-ttu-id="3a3b7-115">Kaynak...</span><span class="sxs-lookup"><span data-stu-id="3a3b7-115">From …</span></span> <span data-ttu-id="3a3b7-116">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="3a3b7-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="3a3b7-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a3b7-117">Example</span></span>  

 <span data-ttu-id="3a3b7-118">Aşağıdaki örnek, `From … From …` <xref:System.Linq.Enumerable.SelectMany%2A> 500,00 ' den küçük olan tüm siparişleri seçmek için (yönteminin eşdeğeri) kullanır `TotalDue` .</span><span class="sxs-lookup"><span data-stu-id="3a3b7-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="3a3b7-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a3b7-119">Example</span></span>  

 <span data-ttu-id="3a3b7-120">Aşağıdaki örnek, `From … From …` <xref:System.Linq.Enumerable.SelectMany%2A> 1 Ekim 2002 veya sonraki bir sürümde siparişin yapıldığı tüm siparişleri seçmek için (yönteminin eşdeğeri) kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a3b7-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="3a3b7-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a3b7-121">Example</span></span>  

 <span data-ttu-id="3a3b7-122">Aşağıdaki örnek, `From … From …` <xref:System.Linq.Enumerable.SelectMany%2A> siparişin toplamının 10000,00 ' den büyük olduğu tüm siparişleri seçmek ve `From` toplamı iki kez istememek için atamayı kullanması için bir (yönteminin eşdeğeri) kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a3b7-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="3a3b7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a3b7-123">See also</span></span>

- [<span data-ttu-id="3a3b7-124">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="3a3b7-124">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

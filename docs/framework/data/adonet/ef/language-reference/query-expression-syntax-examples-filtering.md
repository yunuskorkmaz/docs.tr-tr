---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: 84de36b79ed646d73a8f2d8e00c26d8dcf6de4b7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249513"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="ca55c-102">Sorgu İfadesi Söz Dizimi Örnekleri: Filtreleme</span><span class="sxs-lookup"><span data-stu-id="ca55c-102">Query Expression Syntax Examples: Filtering</span></span>
<span data-ttu-id="ca55c-103">Bu konudaki örneklerde, sorgu ifadesi sözdizimini kullanarak `Where` [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples) sorgulamak için ve `Where…Contains` yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ca55c-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="ca55c-104">Note, burada...`Contains`</span><span class="sxs-lookup"><span data-stu-id="ca55c-104">Note, Where…`Contains`</span></span> <span data-ttu-id="ca55c-105">, [derlenmiş bir sorgunun](compiled-queries-linq-to-entities.md)parçası olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ca55c-105">cannot be used as a part of a [compiled query](compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="ca55c-106">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ca55c-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ca55c-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="ca55c-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="ca55c-108">Where</span><span class="sxs-lookup"><span data-stu-id="ca55c-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="ca55c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca55c-109">Example</span></span>  
 <span data-ttu-id="ca55c-110">Aşağıdaki örnek tüm çevrimiçi siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca55c-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="ca55c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca55c-111">Example</span></span>  
 <span data-ttu-id="ca55c-112">Aşağıdaki örnek, sipariş miktarının 2 ' den büyük ve 6 ' dan küçük olduğu siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca55c-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="ca55c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca55c-113">Example</span></span>  
 <span data-ttu-id="ca55c-114">Aşağıdaki örnek, tüm kırmızı renkli ürünleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca55c-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="ca55c-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca55c-115">Example</span></span>  
 <span data-ttu-id="ca55c-116">Aşağıdaki örnek, 1 Aralık `Where` 2003 ' den sonra yapılan siparişleri bulmak için yöntemini kullanır ve ardından her bir siparişin ayrıntılarını almak `order.SalesOrderDetail` için gezinti özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ca55c-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="ca55c-117">Where... Vardır</span><span class="sxs-lookup"><span data-stu-id="ca55c-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="ca55c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca55c-118">Example</span></span>  
 <span data-ttu-id="ca55c-119">Aşağıdaki örnek dizideki bir değerle eşleşen tüm ürünleri `Where…Contains` `ProductModelID` bulmak için yan tümcesinin bir parçası olarak bir diziyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ca55c-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="ca55c-120">Bir `Where…Contains` yan tümcedeki koşulun bir parçası olarak, bir, veya <xref:System.Collections.Generic.IEnumerable%601> arabirimini <xref:System.Array>uygulayan herhangi <xref:System.Collections.Generic.List%601>bir türün koleksiyonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca55c-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="ca55c-121">Ayrıca, bir LINQ to Entities sorgusu içinde bir koleksiyonu bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca55c-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="ca55c-122">Daha fazla bilgi için bkz. sonraki örnek.</span><span class="sxs-lookup"><span data-stu-id="ca55c-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ca55c-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca55c-123">Example</span></span>  
 <span data-ttu-id="ca55c-124">Aşağıdaki örnek, dizilerdeki değerlerle eşleşen tüm ürünleri `Where…Contains` `ProductModelID` `Size` bulmak için bir yan tümcedeki dizileri bildirir ve başlatır.</span><span class="sxs-lookup"><span data-stu-id="ca55c-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ca55c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca55c-125">See also</span></span>

- [<span data-ttu-id="ca55c-126">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="ca55c-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

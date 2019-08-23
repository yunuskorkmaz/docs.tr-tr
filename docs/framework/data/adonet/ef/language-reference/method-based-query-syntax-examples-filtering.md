---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: 0795784f4090fca02c89cdfb396d217620b1ba68
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948230"
---
# <a name="method-based-query-syntax-examples-filtering"></a><span data-ttu-id="64dd1-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Filtreleme</span><span class="sxs-lookup"><span data-stu-id="64dd1-102">Method-Based Query Syntax Examples: Filtering</span></span>
<span data-ttu-id="64dd1-103">Bu konudaki örneklerde, `Where` ve `Where…Contains` yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="64dd1-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="64dd1-104">Note, burada...`Contains`</span><span class="sxs-lookup"><span data-stu-id="64dd1-104">Note, Where…`Contains`</span></span> <span data-ttu-id="64dd1-105">, [derlenmiş bir sorgunun](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)parçası olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="64dd1-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="64dd1-106">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="64dd1-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="64dd1-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="64dd1-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="64dd1-108">Where</span><span class="sxs-lookup"><span data-stu-id="64dd1-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="64dd1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="64dd1-109">Example</span></span>  
 <span data-ttu-id="64dd1-110">Aşağıdaki örnek tüm çevrimiçi siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="64dd1-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a><span data-ttu-id="64dd1-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="64dd1-111">Example</span></span>  
 <span data-ttu-id="64dd1-112">Aşağıdaki örnek, sipariş miktarının 2 ' den büyük ve 6 ' dan küçük olduğu siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="64dd1-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a><span data-ttu-id="64dd1-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="64dd1-113">Example</span></span>  
 <span data-ttu-id="64dd1-114">Aşağıdaki örnek, tüm kırmızı renkli ürünleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="64dd1-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a><span data-ttu-id="64dd1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="64dd1-115">Example</span></span>  
 <span data-ttu-id="64dd1-116">Aşağıdaki örnek, 1 Aralık `Where` 2003 ' den sonra yapılan siparişleri bulmak için yöntemini kullanır ve ardından her bir siparişin ayrıntılarını `order.SalesOrderDetail` almak için gezinti özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="64dd1-116">The following example uses the `Where` method to find orders that were made after December 1, 2003 and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a><span data-ttu-id="64dd1-117">Where... Vardır</span><span class="sxs-lookup"><span data-stu-id="64dd1-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="64dd1-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="64dd1-118">Example</span></span>  
 <span data-ttu-id="64dd1-119">Aşağıdaki örnek dizideki bir değerle eşleşen tüm ürünleri `Where…Contains` `ProductModelID` bulmak için yan tümcesinin bir parçası olarak bir diziyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="64dd1-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
> <span data-ttu-id="64dd1-120">Bir `Where…Contains` yan tümcedeki koşulun bir parçası olarak, bir, veya <xref:System.Collections.Generic.IEnumerable%601> arabirimini <xref:System.Array>uygulayan herhangi <xref:System.Collections.Generic.List%601>bir türün koleksiyonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64dd1-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="64dd1-121">Ayrıca, bir LINQ to Entities sorgusu içinde bir koleksiyonu bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64dd1-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="64dd1-122">Daha fazla bilgi için bkz. sonraki örnek.</span><span class="sxs-lookup"><span data-stu-id="64dd1-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="64dd1-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="64dd1-123">Example</span></span>  
 <span data-ttu-id="64dd1-124">Aşağıdaki örnek, diziler içindeki bir değerle eşleşen bir `Where…Contains` `ProductModelID` veya `Size` içeren tüm ürünleri bulmak için bir yan tümcedeki dizileri bildirir ve başlatır.</span><span class="sxs-lookup"><span data-stu-id="64dd1-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or a `Size` that matches a value in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="64dd1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64dd1-125">See also</span></span>

- [<span data-ttu-id="64dd1-126">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="64dd1-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

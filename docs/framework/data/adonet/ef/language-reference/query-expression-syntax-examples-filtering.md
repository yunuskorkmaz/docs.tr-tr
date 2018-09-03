---
title: 'Sorgu ifadesi söz dizimi örnekleri: filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: 667c67cea4dfa3f9a63554286d6c137280332c7e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467535"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="30170-102">Sorgu ifadesi söz dizimi örnekleri: filtreleme</span><span class="sxs-lookup"><span data-stu-id="30170-102">Query Expression Syntax Examples: Filtering</span></span>
<span data-ttu-id="30170-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `Where` ve `Where…Contains` sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="30170-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="30170-104">Not, burada...`Contains`</span><span class="sxs-lookup"><span data-stu-id="30170-104">Note, Where…`Contains`</span></span> <span data-ttu-id="30170-105">bir parçası olarak kullanılan bir [sorgu derlenmiş](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="30170-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="30170-106">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="30170-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="30170-107">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="30170-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="30170-108">Where</span><span class="sxs-lookup"><span data-stu-id="30170-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="30170-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="30170-109">Example</span></span>  
 <span data-ttu-id="30170-110">Aşağıdaki örnek, tüm çevrimiçi siparişler döndürür.</span><span class="sxs-lookup"><span data-stu-id="30170-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="30170-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="30170-111">Example</span></span>  
 <span data-ttu-id="30170-112">Aşağıdaki örnek, sipariş miktarı 2. ve 6'değerinden büyük olduğu siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="30170-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="30170-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="30170-113">Example</span></span>  
 <span data-ttu-id="30170-114">Aşağıdaki örnek, tüm kırmızı renkli ürünleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="30170-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="30170-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="30170-115">Example</span></span>  
 <span data-ttu-id="30170-116">Aşağıdaki örnekte `Where` 1 Aralık 2003 sonra yapıldığı siparişleri bulmak için yöntem ve kullandığı `order.SalesOrderDetail` her siparişi için ayrıntıları almak için gezinme özelliği.</span><span class="sxs-lookup"><span data-stu-id="30170-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="30170-117">WHERE... İçerir</span><span class="sxs-lookup"><span data-stu-id="30170-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="30170-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="30170-118">Example</span></span>  
 <span data-ttu-id="30170-119">Aşağıdaki örnek, bir dizinin parçası olarak kullanır. bir `Where…Contains` sahip tüm ürünleri bulmak için yan tümcesi bir `ProductModelID` , bir dizi değeri eşler.</span><span class="sxs-lookup"><span data-stu-id="30170-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="30170-120">Koşulda bir parçası olarak bir `Where…Contains` kullanabileceğiniz yan tümcesi bir <xref:System.Array>, <xref:System.Collections.Generic.List%601>, veya uygulayan herhangi bir türde bir koleksiyonu <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="30170-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="30170-121">Bildirme ve bir LINQ to Entities sorgusunda içinde bir koleksiyonu başlatır.</span><span class="sxs-lookup"><span data-stu-id="30170-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="30170-122">Daha fazla bilgi için sonraki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="30170-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="30170-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="30170-123">Example</span></span>  
 <span data-ttu-id="30170-124">Aşağıdaki örnek bildirir ve dizilerde başlatır bir `Where…Contains` sahip tüm ürünleri bulmak için yan tümcesi bir `ProductModelID` veya `Size` dizilerde değerler eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="30170-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="30170-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30170-125">See Also</span></span>  
 [<span data-ttu-id="30170-126">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="30170-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

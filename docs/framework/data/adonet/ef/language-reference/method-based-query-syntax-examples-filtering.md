---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: 45000713d0151172762fd797bad7d7736c78a620
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464087"
---
# <a name="method-based-query-syntax-examples-filtering"></a><span data-ttu-id="6c237-102">Metot tabanlı sorgu söz dizimi örnekleri: filtreleme</span><span class="sxs-lookup"><span data-stu-id="6c237-102">Method-Based Query Syntax Examples: Filtering</span></span>
<span data-ttu-id="6c237-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `Where` ve `Where…Contains` sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6c237-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="6c237-104">Not, burada...`Contains`</span><span class="sxs-lookup"><span data-stu-id="6c237-104">Note, Where…`Contains`</span></span> <span data-ttu-id="6c237-105">bir parçası olarak kullanılan bir [sorgu derlenmiş](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="6c237-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="6c237-106">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c237-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6c237-107">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="6c237-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="6c237-108">Where</span><span class="sxs-lookup"><span data-stu-id="6c237-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c237-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c237-109">Example</span></span>  
 <span data-ttu-id="6c237-110">Aşağıdaki örnek, tüm çevrimiçi siparişler döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c237-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a><span data-ttu-id="6c237-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c237-111">Example</span></span>  
 <span data-ttu-id="6c237-112">Aşağıdaki örnek, sipariş miktarı 2. ve 6'değerinden büyük olduğu siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c237-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a><span data-ttu-id="6c237-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c237-113">Example</span></span>  
 <span data-ttu-id="6c237-114">Aşağıdaki örnek, tüm kırmızı renkli ürünleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c237-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a><span data-ttu-id="6c237-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c237-115">Example</span></span>  
 <span data-ttu-id="6c237-116">Aşağıdaki örnekte `Where` 1 Aralık 2003 sonra yapıldığı siparişler ve kullandığı bulmak için yöntem `order.SalesOrderDetail` her siparişi için ayrıntıları almak için gezinme özelliği.</span><span class="sxs-lookup"><span data-stu-id="6c237-116">The following example uses the `Where` method to find orders that were made after December 1, 2003 and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a><span data-ttu-id="6c237-117">WHERE... İçerir</span><span class="sxs-lookup"><span data-stu-id="6c237-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c237-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c237-118">Example</span></span>  
 <span data-ttu-id="6c237-119">Aşağıdaki örnek, bir dizinin parçası olarak kullanır. bir `Where…Contains` sahip tüm ürünleri bulmak için yan tümcesi bir `ProductModelID` , bir dizi değeri eşler.</span><span class="sxs-lookup"><span data-stu-id="6c237-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
>  <span data-ttu-id="6c237-120">Koşulda bir parçası olarak bir `Where…Contains` kullanabileceğiniz yan tümcesi bir <xref:System.Array>, <xref:System.Collections.Generic.List%601>, veya uygulayan herhangi bir türde bir koleksiyonu <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6c237-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="6c237-121">Bildirme ve bir LINQ to Entities sorgusunda içinde bir koleksiyonu başlatır.</span><span class="sxs-lookup"><span data-stu-id="6c237-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="6c237-122">Daha fazla bilgi için sonraki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="6c237-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c237-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c237-123">Example</span></span>  
 <span data-ttu-id="6c237-124">Aşağıdaki örnek bildirir ve dizilerde başlatır bir `Where…Contains` yan tümcesi olan tüm ürünleri bulmak için bir `ProductModelID` veya `Size` , dizilerin bir değeri eşler.</span><span class="sxs-lookup"><span data-stu-id="6c237-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or a `Size` that matches a value in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6c237-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c237-125">See Also</span></span>  
 [<span data-ttu-id="6c237-126">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="6c237-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

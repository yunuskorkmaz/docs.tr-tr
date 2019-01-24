---
title: Karşılaştırma ifadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: cca909e67464d08c0bb4ff8a0d0186d9d600ce18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596351"
---
# <a name="comparison-expressions"></a><span data-ttu-id="45bba-102">Karşılaştırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="45bba-102">Comparison Expressions</span></span>
<span data-ttu-id="45bba-103">Bir karşılaştırma ifadesi bir sabit değeri, özellik değeri veya yöntem sonucu eşit, değil eşittir, büyüktür veya başka bir değerden daha az olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="45bba-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="45bba-104">Belirli bir karşılaştırma için geçerli değilse [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="45bba-104">If a particular comparison is not valid for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], an exception will be thrown.</span></span> <span data-ttu-id="45bba-105">Örtük ve açık, tüm karşılaştırmalar, veri kaynağındaki tüm bileşenleri karşılaştırılabilir olmalarını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="45bba-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="45bba-106">Karşılaştırma ifadeleri sık sık kullanılır `Where` sorgu sonuçları kısıtlamak için yan tümceler.</span><span class="sxs-lookup"><span data-stu-id="45bba-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="45bba-107">Sorgu ifadesi söz dizimi aşağıdaki örnekte sipariş numarası "SO43663 için" eşit olduğu sonuçları döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="45bba-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="45bba-108">Metot tabanlı sorgu söz dizimi aşağıdaki örnekte sipariş numarası "SO43663 için" eşit olduğu sonuçları döndüren bir sorguyu gösterir:</span><span class="sxs-lookup"><span data-stu-id="45bba-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="45bba-109">Sorgu ifadesi söz dizimi aşağıdaki örnekte, satış siparişi bilgileri kullanıma sunulduğundan 8 Temmuz 2001 için eşit olduğu döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="45bba-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="45bba-110">Metot tabanlı sorgu söz dizimi aşağıdaki örnekte, satış siparişi bilgileri kullanıma sunulduğundan 8 Temmuz 2001 için eşit olduğu döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="45bba-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="45bba-111">Bir sabit yield deyimleri sunucuda dönüştürülür ve yerel değerlendirmesi yapmak girişimi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="45bba-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="45bba-112">Aşağıdaki örnek, bir ifadede kullanır `Where` sabit verir yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="45bba-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] <span data-ttu-id="45bba-113">Kullanıcı sınıfı bir sabit olarak kullanma desteği olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="45bba-113">does not support using a user class as a constant.</span></span> <span data-ttu-id="45bba-114">Ancak, bir kullanıcı sınıfta bir özellik başvurusu bir sabit olarak kabul edilir ve bir komut ağacı sabit ifade dönüştürülür ve veri kaynağında yürütülen.</span><span class="sxs-lookup"><span data-stu-id="45bba-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="45bba-115">Sabit bir ifade döndüren yöntemler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="45bba-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="45bba-116">Aşağıdaki örnek, bir yöntem içerir `Where` sabit bir değer döndüren yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="45bba-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="45bba-117">Bu örnek, çalışma zamanında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45bba-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="45bba-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45bba-118">See also</span></span>
- [<span data-ttu-id="45bba-119">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="45bba-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

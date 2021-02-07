---
description: 'Daha fazla bilgi edinin: karşılaştırma Ifadeleri'
title: Karşılaştırma İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: 95d93597048b36e48227387e2135afab1486e1ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697003"
---
# <a name="comparison-expressions"></a><span data-ttu-id="79724-103">Karşılaştırma İfadeleri</span><span class="sxs-lookup"><span data-stu-id="79724-103">Comparison Expressions</span></span>

<span data-ttu-id="79724-104">Karşılaştırma ifadesi sabit bir değer, özellik değeri veya yöntem sonucunun eşit, eşit, büyük veya başka bir değerden küçük olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="79724-104">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="79724-105">Belirli bir karşılaştırma LINQ to Entities için geçerli değilse, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="79724-105">If a particular comparison is not valid for LINQ to Entities, an exception will be thrown.</span></span> <span data-ttu-id="79724-106">Örtülü ve açık olan tüm karşılaştırmalar, tüm bileşenlerin veri kaynağında karşılaştırılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="79724-106">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="79724-107">`Where`Sorgu sonuçlarını kısıtlamak için yan tümcelerde Karşılaştırma ifadeleri sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79724-107">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="79724-108">Sorgu ifadesi sözdiziminde aşağıdaki örnek, satış siparişi numarasının "SO43663" değerine eşit olduğu sonuçlara döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="79724-108">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="79724-109">Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, satış siparişi numarasının "SO43663" değerine eşit olduğu sonuçlara döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="79724-109">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="79724-110">Sorgu ifadesi sözdiziminde aşağıdaki örnek, sevk tarihinin 8 Temmuz 2001 ' e eşit olduğu satış siparişi bilgilerini döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="79724-110">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="79724-111">Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, sevk tarihinin 8 Temmuz 2001 ' e eşit olduğu satış siparişi bilgilerini döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="79724-111">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="79724-112">Bir sabit değer veren ifadeler sunucuda dönüştürülür ve yerel değerlendirme yapmaya yönelik bir girişim yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="79724-112">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="79724-113">Aşağıdaki örnek, `Where` bir sabiti veren yan tümcesinde bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="79724-113">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="79724-114">LINQ to Entities, bir Kullanıcı sınıfının sabit olarak kullanılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="79724-114">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="79724-115">Ancak, bir Kullanıcı sınıfındaki özellik başvurusu bir sabit kabul edilir ve bir komut ağacı sabit ifadesine dönüştürülür ve veri kaynağında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="79724-115">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="79724-116">Sabit bir ifade döndüren yöntemler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="79724-116">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="79724-117">Aşağıdaki örnek, `Where` bir sabiti döndüren yan tümcedeki bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="79724-117">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="79724-118">Bu örnek, çalışma zamanında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="79724-118">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="79724-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79724-119">See also</span></span>

- [<span data-ttu-id="79724-120">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="79724-120">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)

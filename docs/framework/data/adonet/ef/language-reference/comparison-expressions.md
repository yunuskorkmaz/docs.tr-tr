---
title: Karşılaştırma ifadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: 5d201d331d766d865d0ee7afb164813084fa3651
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761512"
---
# <a name="comparison-expressions"></a><span data-ttu-id="7ed99-102">Karşılaştırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="7ed99-102">Comparison Expressions</span></span>
<span data-ttu-id="7ed99-103">Bir karşılaştırma ifadesi sabit değer, özellik değeri veya yöntem sonucu eşit değil eşit, daha büyük veya başka bir değerden daha az olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7ed99-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="7ed99-104">Belirli bir karşılaştırma için geçerli değilse [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="7ed99-104">If a particular comparison is not valid for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], an exception will be thrown.</span></span> <span data-ttu-id="7ed99-105">Örtük ve açık, tüm karşılaştırmaları veri kaynağındaki tüm bileşenleri karşılaştırılabilir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7ed99-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="7ed99-106">Karşılaştırma ifadeleri sık kullanıldığı `Where` sorgu sonuçlarını kısıtlamak yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="7ed99-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="7ed99-107">Sorgu ifade sözdizimi aşağıdaki örnekte, sipariş numarası "SO43663" eşit olduğu sonuçları döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="7ed99-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="7ed99-108">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte, sipariş numarası "SO43663" eşit olduğu sonuçları döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="7ed99-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="7ed99-109">Sorgu ifade sözdizimi aşağıdaki örnekte sunulduğundan 8 Temmuz 2001 için eşit olduğu Satış siparişi bilgileri döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="7ed99-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="7ed99-110">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte sunulduğundan 8 Temmuz 2001 için eşit olduğu Satış siparişi bilgileri döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="7ed99-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="7ed99-111">Sunucuda, bir sabit sonucu veren ifadeler dönüştürülür ve yerel değerlendirme yapmak için herhangi bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="7ed99-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="7ed99-112">Aşağıdaki örnek, bir ifade kullanır `Where` bir sabit verir yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7ed99-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="7ed99-113"> bir kullanıcı sınıfı bir sabit değer olarak kullanılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7ed99-113"> does not support using a user class as a constant.</span></span> <span data-ttu-id="7ed99-114">Ancak, bir özellik referansı bir kullanıcı sınıfını bir sabit olarak kabul edilir ve komut ağacı sabit bir ifade için dönüştürülür ve veri kaynağı üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7ed99-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="7ed99-115">Bir sabit ifadesine döndüren yöntemler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7ed99-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="7ed99-116">Aşağıdaki örnek, bir yöntem içerir `Where` sabit bir değer döndürür yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7ed99-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="7ed99-117">Bu örnek, çalışma zamanında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ed99-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="7ed99-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ed99-118">See Also</span></span>  
 [<span data-ttu-id="7ed99-119">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7ed99-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

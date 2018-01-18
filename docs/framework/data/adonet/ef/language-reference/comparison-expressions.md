---
title: "Karşılaştırma ifadeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e6865da677645a404e2116d1e7777106ed55223d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="comparison-expressions"></a><span data-ttu-id="1b011-102">Karşılaştırma ifadeleri</span><span class="sxs-lookup"><span data-stu-id="1b011-102">Comparison Expressions</span></span>
<span data-ttu-id="1b011-103">Bir karşılaştırma ifadesi sabit değer, özellik değeri veya yöntem sonucu eşit değil eşit, daha büyük veya başka bir değerden daha az olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1b011-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="1b011-104">Belirli bir karşılaştırma için geçerli değilse [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="1b011-104">If a particular comparison is not valid for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], an exception will be thrown.</span></span> <span data-ttu-id="1b011-105">Örtük ve açık, tüm karşılaştırmaları veri kaynağındaki tüm bileşenleri karşılaştırılabilir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1b011-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="1b011-106">Karşılaştırma ifadeleri sık kullanıldığı `Where` sorgu sonuçlarını kısıtlamak yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="1b011-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="1b011-107">Sorgu ifade sözdizimi aşağıdaki örnekte, sipariş numarası "SO43663" eşit olduğu sonuçları döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="1b011-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="1b011-108">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte, sipariş numarası "SO43663" eşit olduğu sonuçları döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="1b011-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="1b011-109">Sorgu ifade sözdizimi aşağıdaki örnekte sunulduğundan 8 Temmuz 2001 için eşit olduğu Satış siparişi bilgileri döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="1b011-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="1b011-110">Yöntem temelli sorgu söz dizimi aşağıdaki örnekte sunulduğundan 8 Temmuz 2001 için eşit olduğu Satış siparişi bilgileri döndüren bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="1b011-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="1b011-111">Sunucuda, bir sabit sonucu veren ifadeler dönüştürülür ve yerel değerlendirme yapmak için herhangi bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="1b011-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="1b011-112">Aşağıdaki örnek, bir ifade kullanır `Where` bir sabit verir yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1b011-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="1b011-113">bir kullanıcı sınıfı bir sabit değer olarak kullanılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1b011-113"> does not support using a user class as a constant.</span></span> <span data-ttu-id="1b011-114">Ancak, bir özellik referansı bir kullanıcı sınıfını bir sabit olarak kabul edilir ve komut ağacı sabit bir ifade için dönüştürülür ve veri kaynağı üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="1b011-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="1b011-115">Bir sabit ifadesine döndüren yöntemler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1b011-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="1b011-116">Aşağıdaki örnek, bir yöntem içerir `Where` sabit bir değer döndürür yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1b011-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="1b011-117">Bu örnek, çalışma zamanında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b011-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="1b011-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b011-118">See Also</span></span>  
 [<span data-ttu-id="1b011-119">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="1b011-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

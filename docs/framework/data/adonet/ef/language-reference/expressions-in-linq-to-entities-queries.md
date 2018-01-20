---
title: LINQ to Entities sorgu ifadeleri
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
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f429a354c4042f0e85b9ef078bbc57ebe510d0d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="02286-102">LINQ to Entities sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="02286-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="02286-103">Tek değer, nesne, yöntemi veya ad alanı için değerlendirilen kodunun bir parçası olan bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="02286-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="02286-104">İfade, bir hazır değer, bir yöntem çağrısı, bir işleç ve işlenenleri veya basit bir ad içerebilir.</span><span class="sxs-lookup"><span data-stu-id="02286-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="02286-105">Basit adları bir değişken, türü üyesinin, yöntem parametresi, ad alanı veya türü adı olabilir.</span><span class="sxs-lookup"><span data-stu-id="02286-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="02286-106">İfadeler sırayla diğer ifadeleri parametreleri veya yöntem çağrılarını sırayla diğer yöntem çağrıları, parametreleridir olarak kullanma işleçleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02286-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="02286-107">Bu nedenle, ifadeler basitten için çok karmaşık aralığında değişebilir.</span><span class="sxs-lookup"><span data-stu-id="02286-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="02286-108">İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorguları, ifadeleri içerebilir içinde türlerden tarafından izin verilen herhangi bir şey <xref:System.Linq.Expressions> lambda ifadeleri de dahil olmak üzere ad alanı.</span><span class="sxs-lookup"><span data-stu-id="02286-108">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="02286-109">Kullanılabilir ifadeleri [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorguları kullanılabilir ifadeler bir alt kümesi olan sorguya [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02286-109">The expressions that can be used in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="02286-110">Sorguları parçası olan bir ifade [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] tarafından desteklenen işlemler sınırlıdır `ObjectQuery<T>` ve temel alınan veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="02286-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="02286-111">Aşağıdaki örnekte, buna karşılık `Where` yan tümcesi olan bir ifade:</span><span class="sxs-lookup"><span data-stu-id="02286-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="02286-112">Belirli bir dil yapıları, C# gibi `unchecked`, hiçbir anlamı sahip [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02286-112">Specific language constructs, such as C# `unchecked`, have no meaning in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="02286-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="02286-113">In This Section</span></span>  
 [<span data-ttu-id="02286-114">Sabit İfadeler</span><span class="sxs-lookup"><span data-stu-id="02286-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="02286-115">Karşılaştırma İfadeleri</span><span class="sxs-lookup"><span data-stu-id="02286-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="02286-116">Null Karşılaştırmalar</span><span class="sxs-lookup"><span data-stu-id="02286-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="02286-117">Başlatma İfadeleri</span><span class="sxs-lookup"><span data-stu-id="02286-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="02286-118">Gezinti özellikleri</span><span class="sxs-lookup"><span data-stu-id="02286-118">Navigation Properties</span></span>](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a><span data-ttu-id="02286-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02286-119">See Also</span></span>  
 [<span data-ttu-id="02286-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="02286-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)

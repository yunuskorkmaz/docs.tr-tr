---
title: LINQ to Entities Sorgu İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250979"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="86344-102">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="86344-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="86344-103">Bir ifade, tek bir değer, nesne, yöntem veya ad alanı olarak değerlendirilebilen kodun bir parçadır.</span><span class="sxs-lookup"><span data-stu-id="86344-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="86344-104">İfadeler bir değişmez değer, bir yöntem çağrısı, bir işleç ve işlenenleri veya basit bir ad içerebilir.</span><span class="sxs-lookup"><span data-stu-id="86344-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="86344-105">Basit adlar bir değişkenin adı, tür üyesi, yöntem parametresi, ad alanı veya tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="86344-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="86344-106">İfadeler, diğer ifadeleri parametre olarak kullanan işleçler veya parametreleri diğer Yöntem çağrılarını aç içinde olan Yöntem çağrıları ' nı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="86344-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="86344-107">Bu nedenle, ifadeler basit ve çok karmaşık olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="86344-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="86344-108">LINQ to Entities sorgularda, ifadeler, lambda ifadeleri dahil olmak üzere <xref:System.Linq.Expressions> ad alanı içindeki türlerin izin verdiği her şeyi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="86344-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="86344-109">LINQ to Entities sorgularında kullanılabilecek ifadeler, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]sorgulamak için kullanılabilen ifadelerin bir üst kümesidir.</span><span class="sxs-lookup"><span data-stu-id="86344-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="86344-110">Üzerinde sorguların parçası olan ifadeler, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] tarafından `ObjectQuery<T>` desteklenen işlemlerle ve temel alınan veri kaynağıyla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="86344-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="86344-111">Aşağıdaki örnekte, `Where` yan tümcesindeki karşılaştırma bir ifadedir:</span><span class="sxs-lookup"><span data-stu-id="86344-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="86344-112">Gibi belirli dil yapıları C# `unchecked`LINQ to Entities bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="86344-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86344-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="86344-113">In This Section</span></span>  
 [<span data-ttu-id="86344-114">Sabit İfadeler</span><span class="sxs-lookup"><span data-stu-id="86344-114">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="86344-115">Karşılaştırma İfadeleri</span><span class="sxs-lookup"><span data-stu-id="86344-115">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="86344-116">Null Karşılaştırmalar</span><span class="sxs-lookup"><span data-stu-id="86344-116">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="86344-117">Başlatma İfadeleri</span><span class="sxs-lookup"><span data-stu-id="86344-117">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="86344-118">İlişkiler, gezinti özellikleri ve yabancı anahtarlar</span><span class="sxs-lookup"><span data-stu-id="86344-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="86344-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86344-119">See also</span></span>

- [<span data-ttu-id="86344-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="86344-120">ADO.NET Entity Framework</span></span>](../index.md)

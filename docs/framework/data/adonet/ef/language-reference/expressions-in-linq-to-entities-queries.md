---
title: LINQ to Entities Sorgu İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: f65759d37661271588d56965eadcccbe997623f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166657"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="2e059-102">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="2e059-102">Expressions in LINQ to Entities Queries</span></span>

<span data-ttu-id="2e059-103">Bir ifade, tek bir değer, nesne, yöntem veya ad alanı olarak değerlendirilebilen kodun bir parçadır.</span><span class="sxs-lookup"><span data-stu-id="2e059-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="2e059-104">İfadeler bir değişmez değer, bir yöntem çağrısı, bir işleç ve işlenenleri veya basit bir ad içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2e059-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="2e059-105">Basit adlar bir değişkenin adı, tür üyesi, yöntem parametresi, ad alanı veya tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e059-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="2e059-106">İfadeler, diğer ifadeleri parametre olarak kullanan işleçler veya parametreleri diğer Yöntem çağrılarını aç içinde olan Yöntem çağrıları ' nı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2e059-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="2e059-107">Bu nedenle, ifadeler basit ve çok karmaşık olarak değişebilir.</span><span class="sxs-lookup"><span data-stu-id="2e059-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="2e059-108">LINQ to Entities sorgularda, ifadeler, <xref:System.Linq.Expressions> lambda ifadeleri dahil olmak üzere ad alanı içindeki türlerin izin verdiği her şeyi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2e059-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="2e059-109">LINQ to Entities sorgularda kullanılabilecek ifadeler, Entity Framework sorgulamak için kullanılabilecek ifadelerin bir üst kümesidir. Entity Framework göre sorguların parçası olan Ifadeler, tarafından desteklenen işlemlerle `ObjectQuery<T>` ve temel alınan veri kaynağıyla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e059-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the Entity Framework.Expressions that are part of queries against the Entity Framework are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="2e059-110">Aşağıdaki örnekte, `Where` yan tümcesindeki karşılaştırma bir ifadedir:</span><span class="sxs-lookup"><span data-stu-id="2e059-110">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="2e059-111">C# gibi belirli dil yapıları LINQ to Entities bir `unchecked` anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="2e059-111">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e059-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2e059-112">In This Section</span></span>  

 [<span data-ttu-id="2e059-113">Sabit Ifadeler</span><span class="sxs-lookup"><span data-stu-id="2e059-113">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="2e059-114">Karşılaştırma Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2e059-114">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="2e059-115">Null Karşılaştırmalar</span><span class="sxs-lookup"><span data-stu-id="2e059-115">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="2e059-116">Başlatma İfadeleri</span><span class="sxs-lookup"><span data-stu-id="2e059-116">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="2e059-117">İlişkiler, gezinti özellikleri ve yabancı anahtarlar</span><span class="sxs-lookup"><span data-stu-id="2e059-117">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="2e059-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e059-118">See also</span></span>

- [<span data-ttu-id="2e059-119">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2e059-119">ADO.NET Entity Framework</span></span>](../index.md)

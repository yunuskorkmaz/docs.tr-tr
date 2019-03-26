---
title: Niceleyici işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: c358c3181ecbefeedcbe22e6f3c877d2924c66b3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409516"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="d86a9-102">Niceleyici işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d86a9-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="d86a9-103">Niceleyici işlemleri dönüş bir <xref:System.Boolean> bazılarını veya tümünü bir dizideki öğelerin bir koşulu karşılayan olup olmadığını gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="d86a9-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="d86a9-104">Aşağıdaki çizimde, iki farklı kaynak diziler üzerinde iki farklı niceleyici işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d86a9-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="d86a9-105">İlk işlem bir veya daha fazla öğe olan karakter 'A' ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="d86a9-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="d86a9-106">İkinci işlem tüm öğeleri karakter 'A' olan ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="d86a9-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ Niceleyici işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="d86a9-108">Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="d86a9-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d86a9-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d86a9-109">Methods</span></span>  
  
|<span data-ttu-id="d86a9-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="d86a9-110">Method Name</span></span>|<span data-ttu-id="d86a9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d86a9-111">Description</span></span>|<span data-ttu-id="d86a9-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d86a9-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="d86a9-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="d86a9-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="d86a9-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="d86a9-114">All</span></span>|<span data-ttu-id="d86a9-115">Bir dizideki tüm öğeler bir koşulu karşılayan olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d86a9-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d86a9-116">Tüm</span><span class="sxs-lookup"><span data-stu-id="d86a9-116">Any</span></span>|<span data-ttu-id="d86a9-117">Bir dizideki herhangi bir öğe bir koşulu karşılayan olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d86a9-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d86a9-118">İçerir</span><span class="sxs-lookup"><span data-stu-id="d86a9-118">Contains</span></span>|<span data-ttu-id="d86a9-119">Bir dizi belirtilen öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="d86a9-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="d86a9-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d86a9-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d86a9-121">Sorgu ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="d86a9-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="d86a9-122">Bu örneklerde `Aggregate` Visual Basic'te LINQ sorgusundaki filtre koşulu bir parçası olarak yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d86a9-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="d86a9-123">Aşağıdaki örnekte `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.All%2A> genişletme yöntemi bu kişilere, Evcil Hayvanlar belirtilen yaşından tüm eski bir koleksiyondan döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="d86a9-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="d86a9-124">Sonraki örnekte `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.Any%2A> en az bir sahip bu kişileri hayvan koleksiyondan döndürmek için genişletme yöntemi belirtilen bir geçerlilik süresi eski.</span><span class="sxs-lookup"><span data-stu-id="d86a9-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d86a9-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d86a9-125">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="d86a9-126">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d86a9-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d86a9-127">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d86a9-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="d86a9-128">Nasıl yapılır: Belirli bir sözcükler (LINQ) (Visual Basic) kümesini içeren cümleleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="d86a9-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

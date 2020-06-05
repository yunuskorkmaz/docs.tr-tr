---
title: Niceleyici İşlemleri
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 9a2e35e0511915cb17b99550a8bf382bd9d46526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396317"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="9bba3-102">Nicelik belirteci Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bba3-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="9bba3-103">Nicelik belirteci işlemleri bir <xref:System.Boolean> dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="9bba3-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="9bba3-104">Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9bba3-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="9bba3-105">İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç olur `true` .</span><span class="sxs-lookup"><span data-stu-id="9bba3-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="9bba3-106">İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını ve sonucun olduğunu sorar `true` .</span><span class="sxs-lookup"><span data-stu-id="9bba3-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="9bba3-108">Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9bba3-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9bba3-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9bba3-109">Methods</span></span>  
  
|<span data-ttu-id="9bba3-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="9bba3-110">Method Name</span></span>|<span data-ttu-id="9bba3-111">Description</span><span class="sxs-lookup"><span data-stu-id="9bba3-111">Description</span></span>|<span data-ttu-id="9bba3-112">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bba3-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="9bba3-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="9bba3-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="9bba3-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="9bba3-114">All</span></span>|<span data-ttu-id="9bba3-115">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9bba3-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9bba3-116">Herhangi biri</span><span class="sxs-lookup"><span data-stu-id="9bba3-116">Any</span></span>|<span data-ttu-id="9bba3-117">Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9bba3-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9bba3-118">Contains</span><span class="sxs-lookup"><span data-stu-id="9bba3-118">Contains</span></span>|<span data-ttu-id="9bba3-119">Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="9bba3-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="9bba3-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="9bba3-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="9bba3-121">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="9bba3-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="9bba3-122">Bu örnekler, `Aggregate` BIR LINQ sorgusunda filtreleme koşulunun bir parçası olarak Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bba3-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="9bba3-123">Aşağıdaki örnek, `Aggregate` <xref:System.Linq.Enumerable.All%2A> pelleri belirtilen bir Age den daha eski olan kişilerden gelen bir koleksiyondan geri dönmek için yan tümcesini ve genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bba3-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="9bba3-124">Sonraki örnekte, belirli bir `Aggregate` <xref:System.Linq.Enumerable.Any%2A> yaşından daha eski olan en az bir evcil hayvan olan kişilerden gelen bir koleksiyondan geri dönmek için yan tümce ve genişletme yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9bba3-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9bba3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bba3-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9bba3-126">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bba3-126">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="9bba3-127">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="9bba3-127">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="9bba3-128">Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bba3-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

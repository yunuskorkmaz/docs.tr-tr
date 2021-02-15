---
description: 'Hakkında daha fazla bilgi edinin: nicelik Işlemleri (Visual Basic)'
title: Niceleyici İşlemleri
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 7cbd8a9cf18a0ad8b70ada58d7fa6602dce4bd1b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430098"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="fc8bd-103">Nicelik belirteci Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc8bd-103">Quantifier Operations (Visual Basic)</span></span>

<span data-ttu-id="fc8bd-104">Nicelik belirteci işlemleri bir <xref:System.Boolean> dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-104">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="fc8bd-105">Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-105">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="fc8bd-106">İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç olur `true` .</span><span class="sxs-lookup"><span data-stu-id="fc8bd-106">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="fc8bd-107">İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını ve sonucun olduğunu sorar `true` .</span><span class="sxs-lookup"><span data-stu-id="fc8bd-107">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="fc8bd-109">Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-109">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc8bd-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fc8bd-110">Methods</span></span>  
  
|<span data-ttu-id="fc8bd-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="fc8bd-111">Method Name</span></span>|<span data-ttu-id="fc8bd-112">Description</span><span class="sxs-lookup"><span data-stu-id="fc8bd-112">Description</span></span>|<span data-ttu-id="fc8bd-113">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fc8bd-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="fc8bd-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="fc8bd-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="fc8bd-115">Tümü</span><span class="sxs-lookup"><span data-stu-id="fc8bd-115">All</span></span>|<span data-ttu-id="fc8bd-116">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-116">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fc8bd-117">Herhangi bir</span><span class="sxs-lookup"><span data-stu-id="fc8bd-117">Any</span></span>|<span data-ttu-id="fc8bd-118">Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fc8bd-119">Contains</span><span class="sxs-lookup"><span data-stu-id="fc8bd-119">Contains</span></span>|<span data-ttu-id="fc8bd-120">Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-120">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="fc8bd-121">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="fc8bd-122">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="fc8bd-122">Query Expression Syntax Examples</span></span>  

 <span data-ttu-id="fc8bd-123">Bu örnekler, `Aggregate` BIR LINQ sorgusunda filtreleme koşulunun bir parçası olarak Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-123">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="fc8bd-124">Aşağıdaki örnek, `Aggregate` <xref:System.Linq.Enumerable.All%2A> pelleri belirtilen bir Age den daha eski olan kişilerden gelen bir koleksiyondan geri dönmek için yan tümcesini ve genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-124">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="fc8bd-125">Sonraki örnekte, belirli bir `Aggregate` <xref:System.Linq.Enumerable.Any%2A> yaşından daha eski olan en az bir evcil hayvan olan kişilerden gelen bir koleksiyondan geri dönmek için yan tümce ve genişletme yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-125">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fc8bd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc8bd-126">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fc8bd-127">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc8bd-127">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="fc8bd-128">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="fc8bd-128">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="fc8bd-129">Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc8bd-129">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

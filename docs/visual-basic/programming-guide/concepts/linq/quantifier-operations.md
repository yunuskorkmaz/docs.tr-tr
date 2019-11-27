---
title: Niceleyici İşlemleri
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: f5b98ec09405ca4b8c715dc7da342e66a5d434d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346591"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="31442-102">Nicelik belirteci Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31442-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="31442-103">Nicelik belirteci işlemleri bir dizideki öğelerin bazılarının veya tümünün bir koşulu karşılayıp karşılamadığını belirten <xref:System.Boolean> bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="31442-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="31442-104">Aşağıdaki çizimde iki farklı kaynak dizisi üzerinde iki farklı belirleyici işlem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31442-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="31442-105">İlk işlem, bir veya daha fazla öğenin ' A ' karakteri olup olmadığını sorar ve sonuç `true`.</span><span class="sxs-lookup"><span data-stu-id="31442-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="31442-106">İkinci işlem, tüm öğelerin ' A ' karakteri olup olmadığını sorar ve sonuç `true`.</span><span class="sxs-lookup"><span data-stu-id="31442-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ nicelik belirteci Işlemleri](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="31442-108">Belirleyici işlemler gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="31442-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31442-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="31442-109">Methods</span></span>  
  
|<span data-ttu-id="31442-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="31442-110">Method Name</span></span>|<span data-ttu-id="31442-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31442-111">Description</span></span>|<span data-ttu-id="31442-112">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31442-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="31442-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="31442-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="31442-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="31442-114">All</span></span>|<span data-ttu-id="31442-115">Bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="31442-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31442-116">Tümü</span><span class="sxs-lookup"><span data-stu-id="31442-116">Any</span></span>|<span data-ttu-id="31442-117">Bir dizideki herhangi bir öğenin bir koşulu karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="31442-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31442-118">İçerir</span><span class="sxs-lookup"><span data-stu-id="31442-118">Contains</span></span>|<span data-ttu-id="31442-119">Bir sıranın belirtilen bir öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="31442-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="31442-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="31442-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="31442-121">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="31442-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="31442-122">Bu örnekler, bir LINQ sorgusunda filtreleme koşulunun bir parçası olarak Visual Basic `Aggregate` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="31442-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="31442-123">Aşağıdaki örnek, pelleri belirtilen bir Age den daha eski olan kişilerden gelen bir koleksiyondan geri dönmek için `Aggregate` yan tümcesini ve <xref:System.Linq.Enumerable.All%2A> genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="31442-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="31442-124">Sonraki örnekte, belirli bir yaşından daha eski olan en az bir evcil hayvan olan kişilerden gelen bir koleksiyondan geri dönmek için `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.Any%2A> genişletme yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31442-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="31442-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31442-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="31442-126">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31442-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="31442-127">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="31442-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="31442-128">Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31442-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

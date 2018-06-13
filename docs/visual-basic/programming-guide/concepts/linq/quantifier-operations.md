---
title: Niceleyici işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0a0a5fae35a14ab6451f2f56fb2eedd92ac437e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645840"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="2d3ac-102">Niceleyici işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d3ac-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="2d3ac-103">Niceleyici işlemleri dönüş bir <xref:System.Boolean> bazı veya tüm öğeleri bir sırada bir koşulu karşılıyor olup olmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="2d3ac-104">Aşağıdaki çizimde, iki farklı kaynak sıraları üzerinde iki farklı niceleyici işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="2d3ac-105">İlk işlemi bir veya daha fazla öğe karakter 'A' olan ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="2d3ac-106">İkinci bir işlem tüm öğeleri karakter 'A' olan ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="2d3ac-107">![LINQ Niceleyici işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="2d3ac-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="2d3ac-108">Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d3ac-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2d3ac-109">Methods</span></span>  
  
|<span data-ttu-id="2d3ac-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="2d3ac-110">Method Name</span></span>|<span data-ttu-id="2d3ac-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d3ac-111">Description</span></span>|<span data-ttu-id="2d3ac-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d3ac-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="2d3ac-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="2d3ac-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="2d3ac-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="2d3ac-114">All</span></span>|<span data-ttu-id="2d3ac-115">Bir dizi tüm öğeler bir koşulu karşılıyor olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2d3ac-116">tüm</span><span class="sxs-lookup"><span data-stu-id="2d3ac-116">Any</span></span>|<span data-ttu-id="2d3ac-117">Bir dizisinde herhangi bir öğenin bir koşulu karşılıyor olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2d3ac-118">İçerir</span><span class="sxs-lookup"><span data-stu-id="2d3ac-118">Contains</span></span>|<span data-ttu-id="2d3ac-119">Bir dizi belirtilen öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="2d3ac-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="2d3ac-121">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="2d3ac-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="2d3ac-122">Bu örneklerde `Aggregate` yan tümcesi Visual Basic'te LINQ Sorgu filtre koşulu bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="2d3ac-123">Aşağıdaki örnek kullanır `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.All%2A> genişletme yöntemi, Evcil Hayvanlar belirtilen yaşından tüm eski kişilerle koleksiyondan döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 <span data-ttu-id="2d3ac-124">Sonraki örnek kullanır `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.Any%2A> en az bir tane bu kişilerin pet koleksiyondan dönmek için genişletme yöntemi belirtilen bir geçerlilik süresi eski.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2d3ac-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d3ac-125">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="2d3ac-126">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d3ac-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="2d3ac-127">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="2d3ac-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="2d3ac-128">Nasıl yapılır: sözcükleri (LINQ) (Visual Basic) belirtilen bir kümesini içeren cümleleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="2d3ac-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

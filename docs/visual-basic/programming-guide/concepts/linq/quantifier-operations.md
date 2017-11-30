---
title: "Niceleyici işlemleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9bc48c69179b1f8876efaa465295e94a9a0e0fb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="ccab3-102">Niceleyici işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccab3-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="ccab3-103">Niceleyici işlemleri dönüş bir <xref:System.Boolean> bazı veya tüm öğeleri bir sırada bir koşulu karşılıyor olup olmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="ccab3-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="ccab3-104">Aşağıdaki çizimde, iki farklı kaynak sıraları üzerinde iki farklı niceleyici işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ccab3-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="ccab3-105">İlk işlemi bir veya daha fazla öğe karakter 'A' olan ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="ccab3-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="ccab3-106">İkinci bir işlem tüm öğeleri karakter 'A' olan ve sonucu olup olmadığını soran `true`.</span><span class="sxs-lookup"><span data-stu-id="ccab3-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="ccab3-107">![LINQ Niceleyici işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="ccab3-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="ccab3-108">Niceleyici işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ccab3-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccab3-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ccab3-109">Methods</span></span>  
  
|<span data-ttu-id="ccab3-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="ccab3-110">Method Name</span></span>|<span data-ttu-id="ccab3-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccab3-111">Description</span></span>|<span data-ttu-id="ccab3-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccab3-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ccab3-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="ccab3-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="ccab3-114">Tümü</span><span class="sxs-lookup"><span data-stu-id="ccab3-114">All</span></span>|<span data-ttu-id="ccab3-115">Bir dizi tüm öğeler bir koşulu karşılıyor olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ccab3-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ccab3-116">tüm</span><span class="sxs-lookup"><span data-stu-id="ccab3-116">Any</span></span>|<span data-ttu-id="ccab3-117">Bir dizisinde herhangi bir öğenin bir koşulu karşılıyor olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ccab3-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ccab3-118">İçerir</span><span class="sxs-lookup"><span data-stu-id="ccab3-118">Contains</span></span>|<span data-ttu-id="ccab3-119">Bir dizi belirtilen öğeyi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="ccab3-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="ccab3-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="ccab3-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ccab3-121">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="ccab3-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="ccab3-122">Bu örneklerde `Aggregate` yan tümcesi Visual Basic'te LINQ Sorgu filtre koşulu bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="ccab3-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="ccab3-123">Aşağıdaki örnek kullanır `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.All%2A> genişletme yöntemi, Evcil Hayvanlar belirtilen yaşından tüm eski kişilerle koleksiyondan döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="ccab3-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 <span data-ttu-id="ccab3-124">Sonraki örnek kullanır `Aggregate` yan tümcesi ve <xref:System.Linq.Enumerable.Any%2A> en az bir tane bu kişilerin pet koleksiyondan dönmek için genişletme yöntemi belirtilen bir geçerlilik süresi eski.</span><span class="sxs-lookup"><span data-stu-id="ccab3-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ccab3-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccab3-125">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="ccab3-126">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccab3-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="ccab3-127">AGGREGATE tümcesi</span><span class="sxs-lookup"><span data-stu-id="ccab3-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="ccab3-128">Nasıl yapılır: sözcükleri (LINQ) (Visual Basic) belirtilen bir kümesini içeren cümleleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="ccab3-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

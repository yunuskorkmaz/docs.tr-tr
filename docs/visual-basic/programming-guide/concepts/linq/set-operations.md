---
title: "Ayarlama işlemleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e30c521635326afeea4aad9ce932d5206d06c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="38cc9-102">Ayarlama işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38cc9-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="38cc9-103">Ayarlama işlemleri LINQ varlığının veya yokluğunun aynı ya da ayrı koleksiyonlar (veya içindeki ayarlar) eşdeğer öğelerinin temel alan bir sonuç kümesi oluşturan sorgu işlemlerini bakın.</span><span class="sxs-lookup"><span data-stu-id="38cc9-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="38cc9-104">Ayarlama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="38cc9-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38cc9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38cc9-105">Methods</span></span>  
  
|<span data-ttu-id="38cc9-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="38cc9-106">Method Name</span></span>|<span data-ttu-id="38cc9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38cc9-107">Description</span></span>|<span data-ttu-id="38cc9-108">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38cc9-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="38cc9-109">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="38cc9-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="38cc9-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="38cc9-110">Distinct</span></span>|<span data-ttu-id="38cc9-111">Yinelenen değerleri koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38cc9-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="38cc9-112">Dışlama</span><span class="sxs-lookup"><span data-stu-id="38cc9-112">Except</span></span>|<span data-ttu-id="38cc9-113">İkinci bir koleksiyonda görünmez bir koleksiyonun öğelerini anlamına gelir ayarlanmış farkı döndürür.</span><span class="sxs-lookup"><span data-stu-id="38cc9-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="38cc9-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="38cc9-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="38cc9-115">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="38cc9-115">Intersect</span></span>|<span data-ttu-id="38cc9-116">Her iki koleksiyon görünen öğelerin anlamına gelir kümesi kümenin kesişimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="38cc9-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="38cc9-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="38cc9-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="38cc9-118">UNION</span><span class="sxs-lookup"><span data-stu-id="38cc9-118">Union</span></span>|<span data-ttu-id="38cc9-119">İki koleksiyon birini görünen benzersiz öğelerin anlamına gelir kümesi UNION döndürür.</span><span class="sxs-lookup"><span data-stu-id="38cc9-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="38cc9-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="38cc9-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="38cc9-121">Ayarlama işlemleri karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="38cc9-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="38cc9-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="38cc9-122">Distinct</span></span>  
 <span data-ttu-id="38cc9-123">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yöntemi bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="38cc9-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="38cc9-124">Döndürülen dizi giriş sırası benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="38cc9-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="38cc9-125">![DISTINCT &#40; &#41;davranışını gösteren grafik;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Ayrı")</span><span class="sxs-lookup"><span data-stu-id="38cc9-125">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="38cc9-126">Dışlama</span><span class="sxs-lookup"><span data-stu-id="38cc9-126">Except</span></span>  
 <span data-ttu-id="38cc9-127">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38cc9-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="38cc9-128">Döndürülen dizi ikinci giriş sırayla olmayan yalnızca öğeleri ilk giriş dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="38cc9-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="38cc9-129">![Eylemini gösteren grafik dışında &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "Dışında")</span><span class="sxs-lookup"><span data-stu-id="38cc9-129">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="38cc9-130">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="38cc9-130">Intersect</span></span>  
 <span data-ttu-id="38cc9-131">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38cc9-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="38cc9-132">Döndürülen dizi hem giriş dizilerini için ortak olan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="38cc9-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="38cc9-133">![İki dizinin kesişimini gösteren grafik. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Kesiştiği")</span><span class="sxs-lookup"><span data-stu-id="38cc9-133">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="38cc9-134">UNION</span><span class="sxs-lookup"><span data-stu-id="38cc9-134">Union</span></span>  
 <span data-ttu-id="38cc9-135">Aşağıdaki çizimde iki sıraları karakterden oluşan bir bileşim işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38cc9-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="38cc9-136">Döndürülen dizi hem giriş dizilerini benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="38cc9-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="38cc9-137">![İki sıraları birleşimi gösteren grafik. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Birleşim")</span><span class="sxs-lookup"><span data-stu-id="38cc9-137">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="38cc9-138">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="38cc9-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="38cc9-139">Aşağıdaki örnek kullanır `Distinct` benzersiz numaraları tamsayılar listesinden döndürmek için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="38cc9-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="38cc9-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38cc9-140">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="38cc9-141">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38cc9-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="38cc9-142">Distinct tümcesi</span><span class="sxs-lookup"><span data-stu-id="38cc9-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="38cc9-143">Nasıl yapılır: dize koleksiyonlarını (LINQ) (Visual Basic) birleştirme ve karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="38cc9-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="38cc9-144">Nasıl yapılır: iki liste (LINQ) (Visual Basic) arasında ayarlanmış farkı bulma</span><span class="sxs-lookup"><span data-stu-id="38cc9-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

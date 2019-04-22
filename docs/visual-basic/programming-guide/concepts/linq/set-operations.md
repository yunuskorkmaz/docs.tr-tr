---
title: Ayarlama işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 59ab09607462c762758e6a246ec218a92e01f5de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825790"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="7ea6a-102">Ayarlama işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea6a-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="7ea6a-103">LINQ ayarlama işlemleri varlığı veya yokluğu, eşdeğer öğelerin aynı veya farklı koleksiyonlar (veya kümeleri) temel alan bir sonuç kümesi oluşturan sorgu işlemleri bakın.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="7ea6a-104">Ayarlama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ea6a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ea6a-105">Methods</span></span>  
  
|<span data-ttu-id="7ea6a-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="7ea6a-106">Method Name</span></span>|<span data-ttu-id="7ea6a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ea6a-107">Description</span></span>|<span data-ttu-id="7ea6a-108">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ea6a-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="7ea6a-109">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="7ea6a-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="7ea6a-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="7ea6a-110">Distinct</span></span>|<span data-ttu-id="7ea6a-111">Yinelenen değerleri bir koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7ea6a-112">Dışlama</span><span class="sxs-lookup"><span data-stu-id="7ea6a-112">Except</span></span>|<span data-ttu-id="7ea6a-113">İkinci bir koleksiyon içinde görünmeyen bir koleksiyon öğelerini anlamına gelir ayarlanmış farkı döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="7ea6a-114">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7ea6a-115">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="7ea6a-115">Intersect</span></span>|<span data-ttu-id="7ea6a-116">Her iki koleksiyon içinde görünen öğelerin anlamına gelir küme kesişimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="7ea6a-117">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7ea6a-118">UNION</span><span class="sxs-lookup"><span data-stu-id="7ea6a-118">Union</span></span>|<span data-ttu-id="7ea6a-119">İki koleksiyon birini görünen benzersiz öğeleri anlamına gelir küme birleşimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="7ea6a-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="7ea6a-121">Ayarlama işlemleri karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="7ea6a-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="7ea6a-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="7ea6a-122">Distinct</span></span>  
 <span data-ttu-id="7ea6a-123">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yöntemi bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="7ea6a-124">Döndürülen dizi Giriş dizisinin benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![DISTINCT davranışını gösteren grafik&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="7ea6a-126">Dışlama</span><span class="sxs-lookup"><span data-stu-id="7ea6a-126">Except</span></span>  
 <span data-ttu-id="7ea6a-127">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ea6a-128">Döndürülen dizinin ikinci giriş dizisi içinde olmayan yalnızca öğeleri ilk giriş dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="7ea6a-129">![Eylemi gösteren grafik dışında&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Davranışını gösteren dışında.")</span><span class="sxs-lookup"><span data-stu-id="7ea6a-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="7ea6a-130">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="7ea6a-130">Intersect</span></span>  
 <span data-ttu-id="7ea6a-131">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ea6a-132">Döndürülen dizi hem giriş dizilerini için ortak olan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![İki dizinin kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)    
### <a name="union"></a><span data-ttu-id="7ea6a-134">UNION</span><span class="sxs-lookup"><span data-stu-id="7ea6a-134">Union</span></span>  
 <span data-ttu-id="7ea6a-135">Aşağıdaki çizimde, iki sıranın karakterlerin bir birleşim işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="7ea6a-136">Döndürülen dizinin iki giriş dizilerini benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![İki dizinin birleşimi gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)    
## <a name="query-expression-syntax-example"></a><span data-ttu-id="7ea6a-138">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="7ea6a-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="7ea6a-139">Aşağıdaki örnekte `Distinct` benzersiz sayı tamsayılar listesinden döndürmek için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7ea6a-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ea6a-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7ea6a-141">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea6a-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7ea6a-142">Distinct Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="7ea6a-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="7ea6a-143">Nasıl yapılır: Birleştirme ve karşılaştırma (LINQ) (Visual Basic) dize koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="7ea6a-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="7ea6a-144">Nasıl yapılır: (LINQ) (Visual Basic) iki liste arasında ayarlanmış farkı bulma</span><span class="sxs-lookup"><span data-stu-id="7ea6a-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

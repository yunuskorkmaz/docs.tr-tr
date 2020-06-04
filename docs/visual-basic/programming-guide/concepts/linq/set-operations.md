---
title: Ayarlama İşlemleri
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: b6ff14794343ae7623ee38894cef02cfc0a2a597
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406826"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="8861d-102">Işlemleri ayarlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8861d-102">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="8861d-103">LINQ 'teki işlemleri, aynı veya ayrı Koleksiyonlar (veya kümeler) içindeki eşdeğer öğelerin varlığına veya yokluğuna dayalı bir sonuç kümesi üreten sorgu işlemlerine yönelik olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8861d-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="8861d-104">Ayarlanan işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8861d-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="8861d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8861d-105">Methods</span></span>

|<span data-ttu-id="8861d-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="8861d-106">Method Name</span></span>|<span data-ttu-id="8861d-107">Description</span><span class="sxs-lookup"><span data-stu-id="8861d-107">Description</span></span>|<span data-ttu-id="8861d-108">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8861d-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8861d-109">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="8861d-109">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="8861d-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="8861d-110">Distinct</span></span>|<span data-ttu-id="8861d-111">Yinelenen değerleri bir koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8861d-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8861d-112">Dışlama</span><span class="sxs-lookup"><span data-stu-id="8861d-112">Except</span></span>|<span data-ttu-id="8861d-113">İkinci bir koleksiyonda görünmeyen bir koleksiyonun öğelerinin anlamı olan küme farkını döndürür.</span><span class="sxs-lookup"><span data-stu-id="8861d-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="8861d-114">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8861d-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8861d-115">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="8861d-115">Intersect</span></span>|<span data-ttu-id="8861d-116">Küme kesişimini döndürür, bu iki koleksiyonun her birinde görüntülenen öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8861d-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="8861d-117">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8861d-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8861d-118">Birleşim</span><span class="sxs-lookup"><span data-stu-id="8861d-118">Union</span></span>|<span data-ttu-id="8861d-119">İki koleksiyonda de görünen benzersiz öğeler anlamına gelen set birleşimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8861d-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="8861d-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8861d-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="8861d-121">Ayarlama Işlemlerinin karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="8861d-121">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="8861d-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="8861d-122">Distinct</span></span>

<span data-ttu-id="8861d-123">Aşağıdaki çizim, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> bir karakter dizisi üzerinde yönteminin davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8861d-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="8861d-124">Döndürülen dizi, Giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8861d-124">The returned sequence contains the unique elements from the input sequence.</span></span>

![Ayrı&#40;&#41; davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="8861d-126">Dışlama</span><span class="sxs-lookup"><span data-stu-id="8861d-126">Except</span></span>

<span data-ttu-id="8861d-127">Aşağıdaki çizimde davranışını gösterilmektedir <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8861d-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8861d-128">Döndürülen dizi yalnızca ilk giriş dizisinin ikinci giriş dizisinde olmayan öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8861d-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="8861d-129">![&#40;&#41; hariç eylemi gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Haricinde davranışını gösterir.")</span><span class="sxs-lookup"><span data-stu-id="8861d-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="8861d-130">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="8861d-130">Intersect</span></span>

<span data-ttu-id="8861d-131">Aşağıdaki çizimde davranışını gösterilmektedir <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8861d-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8861d-132">Döndürülen dizi, her iki giriş dizisinde da ortak olan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8861d-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![İki sıranın kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="8861d-134">Birleşim</span><span class="sxs-lookup"><span data-stu-id="8861d-134">Union</span></span>

<span data-ttu-id="8861d-135">Aşağıdaki çizimde iki karakter dizisi üzerinde bir bileşim işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8861d-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="8861d-136">Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8861d-136">The returned sequence contains the unique elements from both input sequences.</span></span>

![İki sıranın birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="8861d-138">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="8861d-138">Query Expression Syntax Example</span></span>

<span data-ttu-id="8861d-139">Aşağıdaki örnek, `Distinct` bir tamsayı listesinden benzersiz sayıları döndürmek için BIR LINQ sorgusunda yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8861d-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="8861d-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8861d-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8861d-141">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8861d-141">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="8861d-142">Distinct Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="8861d-142">Distinct Clause</span></span>](../../../language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="8861d-143">Nasıl yapılır: dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8861d-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="8861d-144">Nasıl yapılır: Iki liste arasındaki küme farkını bulma (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8861d-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

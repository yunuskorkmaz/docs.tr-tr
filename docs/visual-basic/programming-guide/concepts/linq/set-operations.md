---
description: 'Daha fazla bilgi edinin: ayarlama Işlemleri (Visual Basic)'
title: Ayarlama İşlemleri
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 9c75c9e029ba260917f59c7d2ea0341c157bf406
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471675"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="fbf7b-103">Işlemleri ayarlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbf7b-103">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="fbf7b-104">LINQ 'teki işlemleri, aynı veya ayrı Koleksiyonlar (veya kümeler) içindeki eşdeğer öğelerin varlığına veya yokluğuna dayalı bir sonuç kümesi üreten sorgu işlemlerine yönelik olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="fbf7b-105">Ayarlanan işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="fbf7b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fbf7b-106">Methods</span></span>

|<span data-ttu-id="fbf7b-107">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="fbf7b-107">Method Name</span></span>|<span data-ttu-id="fbf7b-108">Description</span><span class="sxs-lookup"><span data-stu-id="fbf7b-108">Description</span></span>|<span data-ttu-id="fbf7b-109">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbf7b-109">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="fbf7b-110">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="fbf7b-110">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="fbf7b-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="fbf7b-111">Distinct</span></span>|<span data-ttu-id="fbf7b-112">Yinelenen değerleri bir koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-112">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="fbf7b-113">Dışlama</span><span class="sxs-lookup"><span data-stu-id="fbf7b-113">Except</span></span>|<span data-ttu-id="fbf7b-114">İkinci bir koleksiyonda görünmeyen bir koleksiyonun öğelerinin anlamı olan küme farkını döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="fbf7b-115">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="fbf7b-116">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="fbf7b-116">Intersect</span></span>|<span data-ttu-id="fbf7b-117">Küme kesişimini döndürür, bu iki koleksiyonun her birinde görüntülenen öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="fbf7b-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="fbf7b-119">Birleşim</span><span class="sxs-lookup"><span data-stu-id="fbf7b-119">Union</span></span>|<span data-ttu-id="fbf7b-120">İki koleksiyonda de görünen benzersiz öğeler anlamına gelen set birleşimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="fbf7b-121">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="fbf7b-122">Ayarlama Işlemlerinin karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="fbf7b-122">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="fbf7b-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="fbf7b-123">Distinct</span></span>

<span data-ttu-id="fbf7b-124">Aşağıdaki çizim, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> bir karakter dizisi üzerinde yönteminin davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="fbf7b-125">Döndürülen dizi, Giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-125">The returned sequence contains the unique elements from the input sequence.</span></span>

![Ayrı&#40;&#41; davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="fbf7b-127">Dışlama</span><span class="sxs-lookup"><span data-stu-id="fbf7b-127">Except</span></span>

<span data-ttu-id="fbf7b-128">Aşağıdaki çizimde davranışını gösterilmektedir <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fbf7b-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fbf7b-129">Döndürülen dizi yalnızca ilk giriş dizisinin ikinci giriş dizisinde olmayan öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="fbf7b-130">![&#40;&#41; hariç eylemi gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Haricinde davranışını gösterir.")</span><span class="sxs-lookup"><span data-stu-id="fbf7b-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="fbf7b-131">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="fbf7b-131">Intersect</span></span>

<span data-ttu-id="fbf7b-132">Aşağıdaki çizimde davranışını gösterilmektedir <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fbf7b-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fbf7b-133">Döndürülen dizi, her iki giriş dizisinde da ortak olan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![İki sıranın kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="fbf7b-135">Birleşim</span><span class="sxs-lookup"><span data-stu-id="fbf7b-135">Union</span></span>

<span data-ttu-id="fbf7b-136">Aşağıdaki çizimde iki karakter dizisi üzerinde bir bileşim işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="fbf7b-137">Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-137">The returned sequence contains the unique elements from both input sequences.</span></span>

![İki sıranın birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="fbf7b-139">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="fbf7b-139">Query Expression Syntax Example</span></span>

<span data-ttu-id="fbf7b-140">Aşağıdaki örnek, `Distinct` bir tamsayı listesinden benzersiz sayıları döndürmek için BIR LINQ sorgusunda yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-140">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="fbf7b-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbf7b-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fbf7b-142">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbf7b-142">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="fbf7b-143">Distinct Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="fbf7b-143">Distinct Clause</span></span>](../../../language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="fbf7b-144">Nasıl yapılır: dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbf7b-144">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="fbf7b-145">Nasıl yapılır: Iki liste arasındaki küme farkını bulma (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbf7b-145">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

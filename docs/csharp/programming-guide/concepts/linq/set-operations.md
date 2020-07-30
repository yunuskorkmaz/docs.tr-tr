---
title: Ayarlama Işlemleri (C#)
description: C# ' de LINQ içinde ayarlanan işlemleri gerçekleştiren ayarlama işlemleri ve standart sorgu işleci yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: ab2608b267113ad5d47a33e64cd9a5e21496f668
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302379"
---
# <a name="set-operations-c"></a><span data-ttu-id="46cc2-103">Ayarlama Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="46cc2-103">Set Operations (C#)</span></span>
<span data-ttu-id="46cc2-104">LINQ 'teki işlemleri, aynı veya ayrı Koleksiyonlar (veya kümeler) içindeki eşdeğer öğelerin varlığına veya yokluğuna dayalı bir sonuç kümesi üreten sorgu işlemlerine yönelik olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="46cc2-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="46cc2-105">Ayarlanan işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46cc2-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="46cc2-106">Methods</span></span>  
  
|<span data-ttu-id="46cc2-107">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="46cc2-107">Method Name</span></span>|<span data-ttu-id="46cc2-108">Description</span><span class="sxs-lookup"><span data-stu-id="46cc2-108">Description</span></span>|<span data-ttu-id="46cc2-109">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46cc2-109">C# Query Expression Syntax</span></span>|<span data-ttu-id="46cc2-110">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="46cc2-110">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="46cc2-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="46cc2-111">Distinct</span></span>|<span data-ttu-id="46cc2-112">Yinelenen değerleri bir koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="46cc2-112">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="46cc2-113">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-113">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="46cc2-114">Dışlama</span><span class="sxs-lookup"><span data-stu-id="46cc2-114">Except</span></span>|<span data-ttu-id="46cc2-115">İkinci bir koleksiyonda görünmeyen bir koleksiyonun öğelerinin anlamı olan küme farkını döndürür.</span><span class="sxs-lookup"><span data-stu-id="46cc2-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="46cc2-116">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="46cc2-117">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="46cc2-117">Intersect</span></span>|<span data-ttu-id="46cc2-118">Küme kesişimini döndürür, bu iki koleksiyonun her birinde görüntülenen öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-118">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="46cc2-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="46cc2-120">Birleşim</span><span class="sxs-lookup"><span data-stu-id="46cc2-120">Union</span></span>|<span data-ttu-id="46cc2-121">İki koleksiyonda de görünen benzersiz öğeler anlamına gelen set birleşimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="46cc2-121">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="46cc2-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="46cc2-123">Ayarlama Işlemlerinin karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="46cc2-123">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="46cc2-124">Distinct</span><span class="sxs-lookup"><span data-stu-id="46cc2-124">Distinct</span></span>  
 <span data-ttu-id="46cc2-125">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> bir karakter dizisi üzerinde yönteminin davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-125">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="46cc2-126">Döndürülen dizi, Giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-126">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Ayrı&#40;&#41; davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="46cc2-128">Dışlama</span><span class="sxs-lookup"><span data-stu-id="46cc2-128">Except</span></span>  
 <span data-ttu-id="46cc2-129">Aşağıdaki örnek, davranışını gösterir <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="46cc2-129">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="46cc2-130">Döndürülen dizi yalnızca ilk giriş dizisinin ikinci giriş dizisinde olmayan öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-130">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="46cc2-131">![&#40;&#41; hariç eylemi gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Haricinde davranışını gösterir.")</span><span class="sxs-lookup"><span data-stu-id="46cc2-131">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="46cc2-132">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="46cc2-132">Intersect</span></span>  
 <span data-ttu-id="46cc2-133">Aşağıdaki örnek, davranışını gösterir <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="46cc2-133">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="46cc2-134">Döndürülen dizi, her iki giriş dizisinde da ortak olan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-134">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![İki sıranın kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="46cc2-136">Birleşim</span><span class="sxs-lookup"><span data-stu-id="46cc2-136">Union</span></span>  
 <span data-ttu-id="46cc2-137">Aşağıdaki örnek iki karakter dizisi üzerinde bir bileşim işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-137">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="46cc2-138">Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="46cc2-138">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![İki sıranın birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="46cc2-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46cc2-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="46cc2-141">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="46cc2-141">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="46cc2-142">Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="46cc2-142">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="46cc2-143">İki liste arasındaki küme farkını bulma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="46cc2-143">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

---
title: Işlemleri ayarla (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 22079b1d41533803f694af210f98bc9fb8a5b322
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711876"
---
# <a name="set-operations-c"></a><span data-ttu-id="b90a5-102">Işlemleri ayarla (C#)</span><span class="sxs-lookup"><span data-stu-id="b90a5-102">Set Operations (C#)</span></span>
<span data-ttu-id="b90a5-103">LINQ 'teki işlemleri, aynı veya ayrı Koleksiyonlar (veya kümeler) içindeki eşdeğer öğelerin varlığına veya yokluğuna dayalı bir sonuç kümesi üreten sorgu işlemlerine yönelik olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b90a5-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="b90a5-104">Ayarlanan işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b90a5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b90a5-105">Methods</span></span>  
  
|<span data-ttu-id="b90a5-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="b90a5-106">Method Name</span></span>|<span data-ttu-id="b90a5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b90a5-107">Description</span></span>|<span data-ttu-id="b90a5-108">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b90a5-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="b90a5-109">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="b90a5-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b90a5-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="b90a5-110">Distinct</span></span>|<span data-ttu-id="b90a5-111">Yinelenen değerleri bir koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b90a5-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="b90a5-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="b90a5-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b90a5-113">Dışlama</span><span class="sxs-lookup"><span data-stu-id="b90a5-113">Except</span></span>|<span data-ttu-id="b90a5-114">İkinci bir koleksiyonda görünmeyen bir koleksiyonun öğelerinin anlamı olan küme farkını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b90a5-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="b90a5-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="b90a5-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b90a5-116">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="b90a5-116">Intersect</span></span>|<span data-ttu-id="b90a5-117">Küme kesişimini döndürür, bu iki koleksiyonun her birinde görüntülenen öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="b90a5-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="b90a5-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b90a5-119">UNION</span><span class="sxs-lookup"><span data-stu-id="b90a5-119">Union</span></span>|<span data-ttu-id="b90a5-120">İki koleksiyonda de görünen benzersiz öğeler anlamına gelen set birleşimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b90a5-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="b90a5-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="b90a5-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="b90a5-122">Ayarlama Işlemlerinin karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="b90a5-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="b90a5-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="b90a5-123">Distinct</span></span>  
 <span data-ttu-id="b90a5-124">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yönteminin bir karakter dizisinde davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-124">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="b90a5-125">Döndürülen dizi, Giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![DISTINCT&#40;&#41;davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)  
 
 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="b90a5-127">Dışlama</span><span class="sxs-lookup"><span data-stu-id="b90a5-127">Except</span></span>  
 <span data-ttu-id="b90a5-128">Aşağıdaki örnek <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-128">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b90a5-129">Döndürülen dizi yalnızca ilk giriş dizisinin ikinci giriş dizisinde olmayan öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="b90a5-130">![Haricinde&#40;&#41;eylemini gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Haricinde davranışını gösterir.")</span><span class="sxs-lookup"><span data-stu-id="b90a5-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="b90a5-131">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="b90a5-131">Intersect</span></span>  
 <span data-ttu-id="b90a5-132">Aşağıdaki örnek <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-132">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b90a5-133">Döndürülen dizi, her iki giriş dizisinde da ortak olan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![İki sıranın kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)  
 
[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="b90a5-135">UNION</span><span class="sxs-lookup"><span data-stu-id="b90a5-135">Union</span></span>  
 <span data-ttu-id="b90a5-136">Aşağıdaki örnek iki karakter dizisi üzerinde bir bileşim işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-136">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="b90a5-137">Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b90a5-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![İki sıranın birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]
 
## <a name="see-also"></a><span data-ttu-id="b90a5-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b90a5-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b90a5-140">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="b90a5-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="b90a5-141">Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b90a5-141">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="b90a5-142">Nasıl yapılır: Iki liste arasında küme farkını bulma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b90a5-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

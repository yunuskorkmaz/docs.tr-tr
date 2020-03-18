---
title: İşlemleri Ayarla (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 44a145a625b5e2e16d2469b20f8cfda1858560a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167939"
---
# <a name="set-operations-c"></a><span data-ttu-id="cd810-102">İşlemleri Ayarla (C#)</span><span class="sxs-lookup"><span data-stu-id="cd810-102">Set Operations (C#)</span></span>
<span data-ttu-id="cd810-103">LINQ'daki işlemleri ayarlayın, aynı veya ayrı koleksiyonlarda (veya kümelerde) eşdeğer öğelerin varlığına veya yokluğuna dayanan bir sonuç kümesi oluşturan sorgu işlemlerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="cd810-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="cd810-104">Set işlemlerini gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.</span><span class="sxs-lookup"><span data-stu-id="cd810-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd810-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cd810-105">Methods</span></span>  
  
|<span data-ttu-id="cd810-106">Yöntem Adı</span><span class="sxs-lookup"><span data-stu-id="cd810-106">Method Name</span></span>|<span data-ttu-id="cd810-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd810-107">Description</span></span>|<span data-ttu-id="cd810-108">C# Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd810-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="cd810-109">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="cd810-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="cd810-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="cd810-110">Distinct</span></span>|<span data-ttu-id="cd810-111">Yinelenen değerleri koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cd810-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="cd810-112">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="cd810-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cd810-113">Dışlama</span><span class="sxs-lookup"><span data-stu-id="cd810-113">Except</span></span>|<span data-ttu-id="cd810-114">Küme farkını döndürür, bu da ikinci bir koleksiyonda görünmeyen bir koleksiyonun öğeleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cd810-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="cd810-115">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="cd810-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cd810-116">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="cd810-116">Intersect</span></span>|<span data-ttu-id="cd810-117">İki koleksiyonun her birinde görünen öğeler anlamına gelen ayarlı kesişimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd810-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="cd810-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="cd810-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cd810-119">Birleşim</span><span class="sxs-lookup"><span data-stu-id="cd810-119">Union</span></span>|<span data-ttu-id="cd810-120">İki koleksiyondan birinde görünen benzersiz öğeler anlamına gelen küme birliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd810-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="cd810-121">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="cd810-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="cd810-122">Set İşlemlerinin Karşılaştırılması</span><span class="sxs-lookup"><span data-stu-id="cd810-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="cd810-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="cd810-123">Distinct</span></span>  
 <span data-ttu-id="cd810-124">Aşağıdaki örnekte, <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yöntemin bir karakter dizisi üzerindeki davranışı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cd810-124">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="cd810-125">Döndürülen dizi, giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cd810-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Distinct&#40;&#41; davranışını gösteren grafik.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="cd810-127">Dışlama</span><span class="sxs-lookup"><span data-stu-id="cd810-127">Except</span></span>  
 <span data-ttu-id="cd810-128">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd810-128">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd810-129">Döndürülen dizi yalnızca ikinci giriş dizisinde olmayan ilk giriş dizisinden öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="cd810-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="cd810-130">![&#40;&#41; Hariç'in eylemini gösteren grafik.](./media/set-operations/except-behavior-graphic.png "Except'Un davranışını gösterir.")</span><span class="sxs-lookup"><span data-stu-id="cd810-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="cd810-131">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="cd810-131">Intersect</span></span>  
 <span data-ttu-id="cd810-132">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd810-132">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd810-133">Döndürülen dizi, her iki giriş dizisinde de ortak olan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cd810-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![İki dizinin kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="cd810-135">Birleşim</span><span class="sxs-lookup"><span data-stu-id="cd810-135">Union</span></span>  
 <span data-ttu-id="cd810-136">Aşağıdaki örnek, iki karakter dizisi üzerinde birleşim işlemi dir.</span><span class="sxs-lookup"><span data-stu-id="cd810-136">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="cd810-137">Döndürülen dizi, her iki giriş dizisinden benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cd810-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![İki dizinin birleşimini gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="cd810-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd810-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="cd810-140">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="cd810-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="cd810-141">Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cd810-141">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="cd810-142">İki liste (LINQ) (C#) arasındaki küme farkı nasıl bulabilirim?</span><span class="sxs-lookup"><span data-stu-id="cd810-142">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

---
title: Ayarlama işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 9e507bbaa39bf040a8ce1564630fb5fbb8c0dbe4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712219"
---
# <a name="set-operations-c"></a><span data-ttu-id="f9cc6-102">Ayarlama işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f9cc6-102">Set Operations (C#)</span></span>
<span data-ttu-id="f9cc6-103">LINQ ayarlama işlemleri varlığı veya yokluğu, eşdeğer öğelerin aynı veya farklı koleksiyonlar (veya kümeleri) temel alan bir sonuç kümesi oluşturan sorgu işlemleri bakın.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="f9cc6-104">Ayarlama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9cc6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f9cc6-105">Methods</span></span>  
  
|<span data-ttu-id="f9cc6-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="f9cc6-106">Method Name</span></span>|<span data-ttu-id="f9cc6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9cc6-107">Description</span></span>|<span data-ttu-id="f9cc6-108">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9cc6-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="f9cc6-109">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="f9cc6-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="f9cc6-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="f9cc6-110">Distinct</span></span>|<span data-ttu-id="f9cc6-111">Yinelenen değerleri bir koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="f9cc6-112">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f9cc6-113">Dışlama</span><span class="sxs-lookup"><span data-stu-id="f9cc6-113">Except</span></span>|<span data-ttu-id="f9cc6-114">İkinci bir koleksiyon içinde görünmeyen bir koleksiyon öğelerini anlamına gelir ayarlanmış farkı döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="f9cc6-115">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f9cc6-116">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="f9cc6-116">Intersect</span></span>|<span data-ttu-id="f9cc6-117">Her iki koleksiyon içinde görünen öğelerin anlamına gelir küme kesişimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="f9cc6-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f9cc6-119">UNION</span><span class="sxs-lookup"><span data-stu-id="f9cc6-119">Union</span></span>|<span data-ttu-id="f9cc6-120">İki koleksiyon birini görünen benzersiz öğeleri anlamına gelir küme birleşimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="f9cc6-121">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="f9cc6-122">Ayarlama işlemleri karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="f9cc6-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="f9cc6-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="f9cc6-123">Distinct</span></span>  
 <span data-ttu-id="f9cc6-124">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> yöntemi bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="f9cc6-125">Döndürülen dizi Giriş dizisinin benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![DISTINCT davranışını gösteren grafik&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="f9cc6-127">Dışlama</span><span class="sxs-lookup"><span data-stu-id="f9cc6-127">Except</span></span>  
 <span data-ttu-id="f9cc6-128">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9cc6-129">Döndürülen dizinin ikinci giriş dizisi içinde olmayan yalnızca öğeleri ilk giriş dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="f9cc6-130">![Eylemi gösteren grafik dışında&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Davranışını gösteren dışında.")</span><span class="sxs-lookup"><span data-stu-id="f9cc6-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="f9cc6-131">Kesiştir</span><span class="sxs-lookup"><span data-stu-id="f9cc6-131">Intersect</span></span>  
 <span data-ttu-id="f9cc6-132">Aşağıdaki çizimde gösterilmektedir davranışını <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9cc6-133">Döndürülen dizi hem giriş dizilerini için ortak olan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![İki dizinin kesişimini gösteren grafik.](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a><span data-ttu-id="f9cc6-135">UNION</span><span class="sxs-lookup"><span data-stu-id="f9cc6-135">Union</span></span>  
 <span data-ttu-id="f9cc6-136">Aşağıdaki çizimde, iki sıranın karakterlerin bir birleşim işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="f9cc6-137">Döndürülen dizinin iki giriş dizilerini benzersiz öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![İki dizinin birleşimi gösteren grafik.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a><span data-ttu-id="f9cc6-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9cc6-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f9cc6-140">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f9cc6-140">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f9cc6-141">Nasıl yapılır: (LINQ) dize koleksiyonlarını birleştirme ve karşılaştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="f9cc6-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="f9cc6-142">Nasıl yapılır: (LINQ) iki liste arasında ayarlanmış farkı bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="f9cc6-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

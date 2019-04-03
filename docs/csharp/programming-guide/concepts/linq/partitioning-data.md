---
title: Veri bölümleme (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: b857c8c6e6b56a7263e6725a747e98ccfe4ff4fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832469"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="68558-102">Veri bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="68558-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="68558-103">LINQ to bölümleme öğelerini yeniden düzenleme ve bölümden birini döndüren bir giriş sırası iki bölümlere ayırma işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="68558-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="68558-104">Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="68558-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="68558-105">İlk işlem, dizideki ilk üç öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="68558-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="68558-106">İkinci işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="68558-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="68558-107">Üçüncü işlemi dizideki ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="68558-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Çizim üç LINQ bölümleme işlemi gösterilmektedir.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="68558-109">Dizileri bölüm standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="68558-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="68558-110">İşleçler</span><span class="sxs-lookup"><span data-stu-id="68558-110">Operators</span></span>  
  
|<span data-ttu-id="68558-111">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="68558-111">Operator Name</span></span>|<span data-ttu-id="68558-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68558-112">Description</span></span>|<span data-ttu-id="68558-113">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68558-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="68558-114">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="68558-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="68558-115">Atla</span><span class="sxs-lookup"><span data-stu-id="68558-115">Skip</span></span>|<span data-ttu-id="68558-116">Bir dizideki belirtilen konuma kadar olan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="68558-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="68558-117">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="68558-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="68558-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="68558-118">SkipWhile</span></span>|<span data-ttu-id="68558-119">Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="68558-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="68558-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="68558-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="68558-121">Take</span><span class="sxs-lookup"><span data-stu-id="68558-121">Take</span></span>|<span data-ttu-id="68558-122">Öğelerin bir dizisi içinde belirtilen konuma kadar sürer.</span><span class="sxs-lookup"><span data-stu-id="68558-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="68558-123">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="68558-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="68558-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="68558-124">TakeWhile</span></span>|<span data-ttu-id="68558-125">Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="68558-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="68558-126">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="68558-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="68558-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68558-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="68558-128">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="68558-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

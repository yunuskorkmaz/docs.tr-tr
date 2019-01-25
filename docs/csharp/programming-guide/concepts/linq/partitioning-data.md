---
title: Veri bölümleme (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 184d9d34e087a06ca3fad9b0a8dad571253b225d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702372"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="a0bcd-102">Veri bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="a0bcd-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="a0bcd-103">LINQ to bölümleme öğelerini yeniden düzenleme ve bölümden birini döndüren bir giriş sırası iki bölümlere ayırma işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="a0bcd-104">Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="a0bcd-105">İlk işlem, dizideki ilk üç öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="a0bcd-106">İkinci işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="a0bcd-107">Üçüncü işlemi dizideki ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="a0bcd-108">![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="a0bcd-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="a0bcd-109">Dizileri bölüm standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="a0bcd-110">İşleçler</span><span class="sxs-lookup"><span data-stu-id="a0bcd-110">Operators</span></span>  
  
|<span data-ttu-id="a0bcd-111">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="a0bcd-111">Operator Name</span></span>|<span data-ttu-id="a0bcd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0bcd-112">Description</span></span>|<span data-ttu-id="a0bcd-113">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0bcd-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="a0bcd-114">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="a0bcd-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="a0bcd-115">Atla</span><span class="sxs-lookup"><span data-stu-id="a0bcd-115">Skip</span></span>|<span data-ttu-id="a0bcd-116">Bir dizideki belirtilen konuma kadar olan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="a0bcd-117">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a0bcd-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="a0bcd-118">SkipWhile</span></span>|<span data-ttu-id="a0bcd-119">Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="a0bcd-120">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a0bcd-121">Take</span><span class="sxs-lookup"><span data-stu-id="a0bcd-121">Take</span></span>|<span data-ttu-id="a0bcd-122">Öğelerin bir dizisi içinde belirtilen konuma kadar sürer.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="a0bcd-123">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a0bcd-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="a0bcd-124">TakeWhile</span></span>|<span data-ttu-id="a0bcd-125">Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="a0bcd-126">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="a0bcd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0bcd-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a0bcd-128">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="a0bcd-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

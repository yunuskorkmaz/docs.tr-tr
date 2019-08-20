---
title: Verileri bölümleme (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591581"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="639a4-102">Verileri bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="639a4-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="639a4-103">LINQ içinde bölümlendirme, bir giriş dizisini, öğeleri yeniden düzenleme ve sonra bölümlerden birini döndürmeden iki bölüme bölme işlemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="639a4-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="639a4-104">Aşağıdaki çizimde, bir karakter dizisi üzerinde üç farklı bölümlendirme işlemi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="639a4-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="639a4-105">İlk işlem dizideki ilk üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="639a4-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="639a4-106">İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="639a4-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="639a4-107">Üçüncü işlem dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="639a4-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Üç LINQ bölümleme işlemini gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="639a4-109">Bölüm dizilerinin aşağıdaki bölümde listelendiği standart sorgu işleci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="639a4-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="639a4-110">İşleçler</span><span class="sxs-lookup"><span data-stu-id="639a4-110">Operators</span></span>  
  
|<span data-ttu-id="639a4-111">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="639a4-111">Operator Name</span></span>|<span data-ttu-id="639a4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="639a4-112">Description</span></span>|<span data-ttu-id="639a4-113">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="639a4-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="639a4-114">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="639a4-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="639a4-115">Atla</span><span class="sxs-lookup"><span data-stu-id="639a4-115">Skip</span></span>|<span data-ttu-id="639a4-116">Bir dizide belirtilen konuma kadar olan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="639a4-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="639a4-117">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="639a4-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="639a4-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="639a4-118">SkipWhile</span></span>|<span data-ttu-id="639a4-119">Bir öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="639a4-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="639a4-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="639a4-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="639a4-121">Take</span><span class="sxs-lookup"><span data-stu-id="639a4-121">Take</span></span>|<span data-ttu-id="639a4-122">Öğeleri bir dizide belirtilen konuma kadar alır.</span><span class="sxs-lookup"><span data-stu-id="639a4-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="639a4-123">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="639a4-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="639a4-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="639a4-124">TakeWhile</span></span>|<span data-ttu-id="639a4-125">Öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="639a4-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="639a4-126">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="639a4-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="639a4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="639a4-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="639a4-128">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="639a4-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)

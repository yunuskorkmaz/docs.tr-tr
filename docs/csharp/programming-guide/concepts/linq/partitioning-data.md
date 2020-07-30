---
title: Verileri bölümleme (C#)
description: LINQ içindeki verileri nasıl bölümleyeceğinizi öğrenin. Bölümleme işlemlerinin sonuçlarını gösteren bir çizim görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 3c85eaec2dc01b683234a27714750354982be440
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302613"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="7f1a6-104">Verileri bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="7f1a6-104">Partitioning Data (C#)</span></span>
<span data-ttu-id="7f1a6-105">LINQ içinde bölümlendirme, bir giriş dizisini, öğeleri yeniden düzenleme ve sonra bölümlerden birini döndürmeden iki bölüme bölme işlemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-105">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="7f1a6-106">Aşağıdaki çizimde, bir karakter dizisi üzerinde üç farklı bölümlendirme işlemi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-106">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="7f1a6-107">İlk işlem dizideki ilk üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-107">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="7f1a6-108">İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-108">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="7f1a6-109">Üçüncü işlem dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-109">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Üç LINQ bölümleme işlemini gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="7f1a6-111">Bölüm dizilerinin aşağıdaki bölümde listelendiği standart sorgu işleci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-111">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="7f1a6-112">İşleçler</span><span class="sxs-lookup"><span data-stu-id="7f1a6-112">Operators</span></span>  
  
|<span data-ttu-id="7f1a6-113">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="7f1a6-113">Operator Name</span></span>|<span data-ttu-id="7f1a6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f1a6-114">Description</span></span>|<span data-ttu-id="7f1a6-115">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f1a6-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="7f1a6-116">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="7f1a6-116">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="7f1a6-117">Atla</span><span class="sxs-lookup"><span data-stu-id="7f1a6-117">Skip</span></span>|<span data-ttu-id="7f1a6-118">Bir dizide belirtilen konuma kadar olan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-118">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="7f1a6-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7f1a6-120">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="7f1a6-120">SkipWhile</span></span>|<span data-ttu-id="7f1a6-121">Bir öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-121">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="7f1a6-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7f1a6-123">Take</span><span class="sxs-lookup"><span data-stu-id="7f1a6-123">Take</span></span>|<span data-ttu-id="7f1a6-124">Öğeleri bir dizide belirtilen konuma kadar alır.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-124">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="7f1a6-125">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7f1a6-126">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="7f1a6-126">TakeWhile</span></span>|<span data-ttu-id="7f1a6-127">Öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-127">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="7f1a6-128">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="7f1a6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f1a6-129">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7f1a6-130">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="7f1a6-130">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)

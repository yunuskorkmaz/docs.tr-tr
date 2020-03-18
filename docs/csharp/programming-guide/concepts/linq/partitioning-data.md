---
title: Veri Bölümleme (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591581"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="ba104-102">Veri Bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="ba104-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="ba104-103">LINQ'da bölümleme, öğeleri yeniden düzenlemeden ve bölümlerden birini döndürmeden bir giriş dizisini iki bölüme bölme işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="ba104-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="ba104-104">Aşağıdaki resimde, bir karakter dizisi üzerinde üç farklı bölümleme işleminin sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ba104-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="ba104-105">İlk işlem, dizideki ilk üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba104-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="ba104-106">İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba104-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="ba104-107">Üçüncü işlem, dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba104-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Üç LINQ bölümleme işlemi gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="ba104-109">Bölüm dizilerinin aşağıdaki bölümde listelendirilen standart sorgu işleci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ba104-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="ba104-110">İşleçler</span><span class="sxs-lookup"><span data-stu-id="ba104-110">Operators</span></span>  
  
|<span data-ttu-id="ba104-111">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="ba104-111">Operator Name</span></span>|<span data-ttu-id="ba104-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba104-112">Description</span></span>|<span data-ttu-id="ba104-113">C# Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba104-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="ba104-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="ba104-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ba104-115">Atla</span><span class="sxs-lookup"><span data-stu-id="ba104-115">Skip</span></span>|<span data-ttu-id="ba104-116">Öğeleri bir sırada belirli bir konuma atlar.</span><span class="sxs-lookup"><span data-stu-id="ba104-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="ba104-117">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ba104-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ba104-118">Skipwhile</span><span class="sxs-lookup"><span data-stu-id="ba104-118">SkipWhile</span></span>|<span data-ttu-id="ba104-119">Bir öğe durumu karşılamayana kadar yüklem işlevini temel alan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="ba104-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="ba104-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ba104-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ba104-121">Take</span><span class="sxs-lookup"><span data-stu-id="ba104-121">Take</span></span>|<span data-ttu-id="ba104-122">Öğeleri bir sırada belirli bir konuma alır.</span><span class="sxs-lookup"><span data-stu-id="ba104-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="ba104-123">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ba104-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ba104-124">Takewhile</span><span class="sxs-lookup"><span data-stu-id="ba104-124">TakeWhile</span></span>|<span data-ttu-id="ba104-125">Bir öğe koşulu karşılamayana kadar bir yüklem işlevine dayalı öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="ba104-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="ba104-126">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ba104-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="ba104-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba104-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ba104-128">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="ba104-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)

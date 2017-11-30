---
title: "Bölümleme verileri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32b95887e05767513dd818743dd1726149503b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-c"></a><span data-ttu-id="96d3a-102">Bölümleme verileri (C#)</span><span class="sxs-lookup"><span data-stu-id="96d3a-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="96d3a-103">LINQ bölümlendirme öğeleri yeniden düzenleme ve bölümlerden biri döndürme olmadan bir giriş sırası iki bölümlere ayırma işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="96d3a-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="96d3a-104">Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96d3a-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="96d3a-105">İlk işlemi ilk üç öğeleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="96d3a-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="96d3a-106">İkinci bir işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="96d3a-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="96d3a-107">Üçüncü işlem sırası ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="96d3a-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="96d3a-108">![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="96d3a-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="96d3a-109">Dizileri bölüm standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="96d3a-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="96d3a-110">İşleçler</span><span class="sxs-lookup"><span data-stu-id="96d3a-110">Operators</span></span>  
  
|<span data-ttu-id="96d3a-111">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="96d3a-111">Operator Name</span></span>|<span data-ttu-id="96d3a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96d3a-112">Description</span></span>|<span data-ttu-id="96d3a-113">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96d3a-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="96d3a-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="96d3a-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="96d3a-115">Atla</span><span class="sxs-lookup"><span data-stu-id="96d3a-115">Skip</span></span>|<span data-ttu-id="96d3a-116">Öğeleri bir sırada belirtilen konum kadar atlar.</span><span class="sxs-lookup"><span data-stu-id="96d3a-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="96d3a-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="96d3a-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="96d3a-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="96d3a-118">SkipWhile</span></span>|<span data-ttu-id="96d3a-119">Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="96d3a-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="96d3a-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="96d3a-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="96d3a-121">Take</span><span class="sxs-lookup"><span data-stu-id="96d3a-121">Take</span></span>|<span data-ttu-id="96d3a-122">Öğeleri bir sırada belirtilen konum kadar sürer.</span><span class="sxs-lookup"><span data-stu-id="96d3a-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="96d3a-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="96d3a-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="96d3a-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="96d3a-124">TakeWhile</span></span>|<span data-ttu-id="96d3a-125">Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="96d3a-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="96d3a-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="96d3a-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="96d3a-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96d3a-127">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="96d3a-128">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="96d3a-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

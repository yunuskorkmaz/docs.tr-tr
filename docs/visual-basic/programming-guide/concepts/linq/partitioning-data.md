---
description: 'Hakkında daha fazla bilgi edinin: veri bölümlendirme (Visual Basic)'
title: Veri Bölümlendirme
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 264a81d1217c7f5034058761033171b9c232fae2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465619"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="3fa58-103">Verileri bölümlendirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fa58-103">Partitioning Data (Visual Basic)</span></span>

<span data-ttu-id="3fa58-104">LINQ içinde bölümlendirme, bir giriş dizisini, öğeleri yeniden düzenleme ve sonra bölümlerden birini döndürmeden iki bölüme bölme işlemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="3fa58-104">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="3fa58-105">Aşağıdaki çizimde, bir karakter dizisi üzerinde üç farklı bölümlendirme işlemi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3fa58-105">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="3fa58-106">İlk işlem dizideki ilk üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fa58-106">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="3fa58-107">İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fa58-107">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="3fa58-108">Üçüncü işlem dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fa58-108">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Üç LINQ bölümleme işlemini gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="3fa58-110">Bölüm dizilerinin aşağıdaki bölümde listelendiği standart sorgu işleci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3fa58-110">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="3fa58-111">İşleçler</span><span class="sxs-lookup"><span data-stu-id="3fa58-111">Operators</span></span>  
  
|<span data-ttu-id="3fa58-112">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="3fa58-112">Operator Name</span></span>|<span data-ttu-id="3fa58-113">Description</span><span class="sxs-lookup"><span data-stu-id="3fa58-113">Description</span></span>|<span data-ttu-id="3fa58-114">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fa58-114">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="3fa58-115">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="3fa58-115">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="3fa58-116">Atla</span><span class="sxs-lookup"><span data-stu-id="3fa58-116">Skip</span></span>|<span data-ttu-id="3fa58-117">Bir dizide belirtilen konuma kadar olan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="3fa58-117">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3fa58-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="3fa58-118">SkipWhile</span></span>|<span data-ttu-id="3fa58-119">Bir öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="3fa58-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3fa58-120">Take</span><span class="sxs-lookup"><span data-stu-id="3fa58-120">Take</span></span>|<span data-ttu-id="3fa58-121">Öğeleri bir dizide belirtilen konuma kadar alır.</span><span class="sxs-lookup"><span data-stu-id="3fa58-121">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3fa58-122">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="3fa58-122">TakeWhile</span></span>|<span data-ttu-id="3fa58-123">Öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="3fa58-123">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="3fa58-124">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="3fa58-124">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="3fa58-125">Atla</span><span class="sxs-lookup"><span data-stu-id="3fa58-125">Skip</span></span>  

 <span data-ttu-id="3fa58-126">Aşağıdaki kod örneği, `Skip` dizideki kalan dizeleri döndürmeden önce bir dize dizisindeki ilk dört dizeyi atlamak için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fa58-126">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="3fa58-127">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="3fa58-127">SkipWhile</span></span>  

 <span data-ttu-id="3fa58-128">Aşağıdaki kod örneği, `Skip While` dizenin ilk harfi "a" iken bir dizideki dizeleri atlamak için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fa58-128">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="3fa58-129">Dizideki kalan dizeler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3fa58-129">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="3fa58-130">Take</span><span class="sxs-lookup"><span data-stu-id="3fa58-130">Take</span></span>  

 <span data-ttu-id="3fa58-131">Aşağıdaki kod örneği, `Take` dizeler dizisindeki ilk iki dizeyi döndürmek için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fa58-131">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="3fa58-132">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="3fa58-132">TakeWhile</span></span>  

 <span data-ttu-id="3fa58-133">Aşağıdaki kod örneği, `Take While` dizenin uzunluğu beş veya daha az olduğunda bir diziden dizeler döndürmek için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fa58-133">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3fa58-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fa58-134">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="3fa58-135">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fa58-135">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="3fa58-136">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3fa58-136">Skip Clause</span></span>](../../../language-reference/queries/skip-clause.md)
- [<span data-ttu-id="3fa58-137">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3fa58-137">Skip While Clause</span></span>](../../../language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="3fa58-138">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3fa58-138">Take Clause</span></span>](../../../language-reference/queries/take-clause.md)
- [<span data-ttu-id="3fa58-139">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3fa58-139">Take While Clause</span></span>](../../../language-reference/queries/take-while-clause.md)

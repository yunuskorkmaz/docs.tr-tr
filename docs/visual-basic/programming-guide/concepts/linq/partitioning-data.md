---
title: Veri Bölümlendirme
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 07e33c4ce0d062a0f083d8970c0ad01f98923a52
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075323"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="2b086-102">Verileri bölümlendirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b086-102">Partitioning Data (Visual Basic)</span></span>

<span data-ttu-id="2b086-103">LINQ içinde bölümlendirme, bir giriş dizisini, öğeleri yeniden düzenleme ve sonra bölümlerden birini döndürmeden iki bölüme bölme işlemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="2b086-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="2b086-104">Aşağıdaki çizimde, bir karakter dizisi üzerinde üç farklı bölümlendirme işlemi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b086-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="2b086-105">İlk işlem dizideki ilk üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b086-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="2b086-106">İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b086-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="2b086-107">Üçüncü işlem dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b086-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Üç LINQ bölümleme işlemini gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="2b086-109">Bölüm dizilerinin aşağıdaki bölümde listelendiği standart sorgu işleci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2b086-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="2b086-110">İşleçler</span><span class="sxs-lookup"><span data-stu-id="2b086-110">Operators</span></span>  
  
|<span data-ttu-id="2b086-111">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="2b086-111">Operator Name</span></span>|<span data-ttu-id="2b086-112">Description</span><span class="sxs-lookup"><span data-stu-id="2b086-112">Description</span></span>|<span data-ttu-id="2b086-113">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b086-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="2b086-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="2b086-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="2b086-115">Atla</span><span class="sxs-lookup"><span data-stu-id="2b086-115">Skip</span></span>|<span data-ttu-id="2b086-116">Bir dizide belirtilen konuma kadar olan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="2b086-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2b086-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="2b086-117">SkipWhile</span></span>|<span data-ttu-id="2b086-118">Bir öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="2b086-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2b086-119">Take</span><span class="sxs-lookup"><span data-stu-id="2b086-119">Take</span></span>|<span data-ttu-id="2b086-120">Öğeleri bir dizide belirtilen konuma kadar alır.</span><span class="sxs-lookup"><span data-stu-id="2b086-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2b086-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="2b086-121">TakeWhile</span></span>|<span data-ttu-id="2b086-122">Öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="2b086-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="2b086-123">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="2b086-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="2b086-124">Atla</span><span class="sxs-lookup"><span data-stu-id="2b086-124">Skip</span></span>  

 <span data-ttu-id="2b086-125">Aşağıdaki kod örneği, `Skip` dizideki kalan dizeleri döndürmeden önce bir dize dizisindeki ilk dört dizeyi atlamak için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b086-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="2b086-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="2b086-126">SkipWhile</span></span>  

 <span data-ttu-id="2b086-127">Aşağıdaki kod örneği, `Skip While` dizenin ilk harfi "a" iken bir dizideki dizeleri atlamak için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b086-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="2b086-128">Dizideki kalan dizeler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2b086-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="2b086-129">Take</span><span class="sxs-lookup"><span data-stu-id="2b086-129">Take</span></span>  

 <span data-ttu-id="2b086-130">Aşağıdaki kod örneği, `Take` dizeler dizisindeki ilk iki dizeyi döndürmek için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b086-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="2b086-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="2b086-131">TakeWhile</span></span>  

 <span data-ttu-id="2b086-132">Aşağıdaki kod örneği, `Take While` dizenin uzunluğu beş veya daha az olduğunda bir diziden dizeler döndürmek için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b086-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2b086-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b086-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="2b086-134">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b086-134">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="2b086-135">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="2b086-135">Skip Clause</span></span>](../../../language-reference/queries/skip-clause.md)
- [<span data-ttu-id="2b086-136">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="2b086-136">Skip While Clause</span></span>](../../../language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="2b086-137">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="2b086-137">Take Clause</span></span>](../../../language-reference/queries/take-clause.md)
- [<span data-ttu-id="2b086-138">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="2b086-138">Take While Clause</span></span>](../../../language-reference/queries/take-while-clause.md)

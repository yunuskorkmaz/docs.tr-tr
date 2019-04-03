---
title: Bölümleme veri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2da63a1f6b73c8592d6036a90fa374a0d4385f4c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839580"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="c308e-102">Bölümleme veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c308e-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="c308e-103">LINQ to bölümleme öğelerini yeniden düzenleme ve bölümden birini döndüren bir giriş sırası iki bölümlere ayırma işlemi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c308e-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="c308e-104">Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c308e-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="c308e-105">İlk işlem, dizideki ilk üç öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c308e-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="c308e-106">İkinci işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c308e-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="c308e-107">Üçüncü işlemi dizideki ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c308e-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Çizim üç LINQ bölümleme işlemi gösterilmektedir.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="c308e-109">Dizileri bölüm standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="c308e-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="c308e-110">İşleçler</span><span class="sxs-lookup"><span data-stu-id="c308e-110">Operators</span></span>  
  
|<span data-ttu-id="c308e-111">İşleç Adı</span><span class="sxs-lookup"><span data-stu-id="c308e-111">Operator Name</span></span>|<span data-ttu-id="c308e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c308e-112">Description</span></span>|<span data-ttu-id="c308e-113">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c308e-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c308e-114">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="c308e-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="c308e-115">Atla</span><span class="sxs-lookup"><span data-stu-id="c308e-115">Skip</span></span>|<span data-ttu-id="c308e-116">Bir dizideki belirtilen konuma kadar olan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="c308e-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c308e-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="c308e-117">SkipWhile</span></span>|<span data-ttu-id="c308e-118">Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="c308e-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c308e-119">Take</span><span class="sxs-lookup"><span data-stu-id="c308e-119">Take</span></span>|<span data-ttu-id="c308e-120">Öğelerin bir dizisi içinde belirtilen konuma kadar sürer.</span><span class="sxs-lookup"><span data-stu-id="c308e-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c308e-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="c308e-121">TakeWhile</span></span>|<span data-ttu-id="c308e-122">Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="c308e-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c308e-123">Sorgu ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="c308e-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="c308e-124">Atla</span><span class="sxs-lookup"><span data-stu-id="c308e-124">Skip</span></span>  
 <span data-ttu-id="c308e-125">Aşağıdaki kod örneğinde `Skip` yan tümcesi kalan döndürmeden önce ilk dört dizeler dize dizisi üzerinden geçmek için Visual Basic'de dizeleri dizide.</span><span class="sxs-lookup"><span data-stu-id="c308e-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="c308e-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="c308e-126">SkipWhile</span></span>  
 <span data-ttu-id="c308e-127">Aşağıdaki kod örneğinde `Skip While` yan tümcesinde Visual Basic dizeleri bir dizideki dizenin ilk harfi olsa da atlamayı "a".</span><span class="sxs-lookup"><span data-stu-id="c308e-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="c308e-128">Kalan dize dizisinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c308e-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="c308e-129">Take</span><span class="sxs-lookup"><span data-stu-id="c308e-129">Take</span></span>  
 <span data-ttu-id="c308e-130">Aşağıdaki kod örneğinde `Take` yan tümcesinde Visual Basic ilk iki dizenin bir dize dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c308e-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="c308e-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="c308e-131">TakeWhile</span></span>  
 <span data-ttu-id="c308e-132">Aşağıdaki kod örneğinde `Take While` dizenin uzunluğunu beş veya daha az olduğu sürece bir diziden dizeleri döndürmek için Visual Basic'te yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c308e-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c308e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c308e-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c308e-134">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c308e-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="c308e-135">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c308e-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="c308e-136">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c308e-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="c308e-137">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c308e-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="c308e-138">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c308e-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)

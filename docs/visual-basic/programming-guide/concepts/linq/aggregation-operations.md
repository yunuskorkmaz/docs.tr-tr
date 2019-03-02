---
title: Toplama işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: fe39c2efb5d9f24a7d9d5240b20a9ca687ed1aa9
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202190"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="69575-102">Toplama işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69575-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="69575-103">Bir toplama işlemi, değerlerin bir koleksiyonunu tek bir değeri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="69575-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="69575-104">Örnek olarak bir toplama işlemi, bir aya ait günlük sıcaklık değerleri değerinde gelen günlük ortalama sıcaklık hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="69575-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="69575-105">Aşağıdaki çizim, sayı dizisi üzerinde iki farklı toplama işlemlerinin sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="69575-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="69575-106">İlk işlem sayıları toplar.</span><span class="sxs-lookup"><span data-stu-id="69575-106">The first operation sums the numbers.</span></span> <span data-ttu-id="69575-107">İkinci işlem dizideki en büyük değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="69575-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="69575-108">![LINQ Toplama işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="69575-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="69575-109">Toplama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="69575-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69575-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="69575-110">Methods</span></span>  
  
|<span data-ttu-id="69575-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="69575-111">Method Name</span></span>|<span data-ttu-id="69575-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69575-112">Description</span></span>|<span data-ttu-id="69575-113">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69575-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="69575-114">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="69575-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="69575-115">Toplama</span><span class="sxs-lookup"><span data-stu-id="69575-115">Aggregate</span></span>|<span data-ttu-id="69575-116">Değerleri bir koleksiyonun bir özel toplama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="69575-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="69575-117">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="69575-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69575-118">Ortalama</span><span class="sxs-lookup"><span data-stu-id="69575-118">Average</span></span>|<span data-ttu-id="69575-119">Değerler koleksiyonu ortalama değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="69575-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69575-120">Sayı</span><span class="sxs-lookup"><span data-stu-id="69575-120">Count</span></span>|<span data-ttu-id="69575-121">Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeleri bir koleksiyondaki öğeleri sayar.</span><span class="sxs-lookup"><span data-stu-id="69575-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69575-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="69575-122">LongCount</span></span>|<span data-ttu-id="69575-123">Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeleri büyük bir koleksiyondaki öğeleri sayar.</span><span class="sxs-lookup"><span data-stu-id="69575-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69575-124">Maks.</span><span class="sxs-lookup"><span data-stu-id="69575-124">Max</span></span>|<span data-ttu-id="69575-125">Bir koleksiyondaki maksimum değeri belirler.</span><span class="sxs-lookup"><span data-stu-id="69575-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69575-126">Min.</span><span class="sxs-lookup"><span data-stu-id="69575-126">Min</span></span>|<span data-ttu-id="69575-127">Bir koleksiyondaki minimum değeri belirleyen.</span><span class="sxs-lookup"><span data-stu-id="69575-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69575-128">Toplam</span><span class="sxs-lookup"><span data-stu-id="69575-128">Sum</span></span>|<span data-ttu-id="69575-129">Bir koleksiyondaki değerlerin toplamını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="69575-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="69575-130">Sorgu ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="69575-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="69575-131">Ortalama</span><span class="sxs-lookup"><span data-stu-id="69575-131">Average</span></span>  
 <span data-ttu-id="69575-132">Aşağıdaki kod örneğinde `Aggregate Into Average` ortalama sıcaklık Sıcaklıkların temsil eden bir sayıdan oluşan hesaplamak için Visual Basic'te yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69575-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="69575-133">Sayı</span><span class="sxs-lookup"><span data-stu-id="69575-133">Count</span></span>  
 <span data-ttu-id="69575-134">Aşağıdaki kod örneğinde `Aggregate Into Count` büyüktür veya eşittir 80'i dizideki değerleri saymak için Visual Basic'te yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69575-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="69575-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="69575-135">LongCount</span></span>  
 <span data-ttu-id="69575-136">Aşağıdaki kod örneğinde `Aggregate Into LongCount` değerlerini bir dizi sayısını yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69575-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="69575-137">Maks.</span><span class="sxs-lookup"><span data-stu-id="69575-137">Max</span></span>  
 <span data-ttu-id="69575-138">Aşağıdaki kod örneğinde `Aggregate Into Max` Sıcaklıkların temsil eden bir sayı dizisi en fazla sıcaklık hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69575-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="69575-139">Min.</span><span class="sxs-lookup"><span data-stu-id="69575-139">Min</span></span>  
 <span data-ttu-id="69575-140">Aşağıdaki kod örneğinde `Aggregate Into Min` en düşük Sıcaklıkların temsil eden bir sayı dizisi sıcaklık hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69575-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="69575-141">Toplam</span><span class="sxs-lookup"><span data-stu-id="69575-141">Sum</span></span>  
 <span data-ttu-id="69575-142">Aşağıdaki kod örneğinde `Aggregate Into Sum` masrafları temsil eden değerleri bir diziden toplam masraf miktarını hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="69575-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="69575-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69575-143">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="69575-144">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69575-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="69575-145">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="69575-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="69575-146">Nasıl yapılır: İşlem sütun değerleri bir CSV metinde dosyasında (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69575-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="69575-147">Nasıl yapılır: Count, Sum veya Average verisi</span><span class="sxs-lookup"><span data-stu-id="69575-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="69575-148">Nasıl yapılır: Bir sorgu sonucunda en düşük ve en fazla değeri bulma</span><span class="sxs-lookup"><span data-stu-id="69575-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="69575-149">Nasıl yapılır: En büyük dosya veya dizin ağacında (LINQ) (Visual Basic) dosyalar için sorgu</span><span class="sxs-lookup"><span data-stu-id="69575-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="69575-150">Nasıl yapılır: Sorgu (LINQ) (Visual Basic) klasör kümesi bayt toplam sayısı</span><span class="sxs-lookup"><span data-stu-id="69575-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

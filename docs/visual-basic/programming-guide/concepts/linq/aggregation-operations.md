---
title: Toplama işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 7e6f838a340283f6fbcd0db4d7d6a089aae9a5aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644075"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="4be3a-102">Toplama işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4be3a-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="4be3a-103">Bir toplama işlemi, tek bir değer değerler koleksiyonundan hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4be3a-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="4be3a-104">Bir toplama işlemi örneği günlük sıcaklık değerler bir ayın eşitleyeceğini gelen ortalama günlük sıcaklık hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="4be3a-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="4be3a-105">Aşağıdaki çizimde, iki farklı toplama işlemlerde bir dizi sayının sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4be3a-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="4be3a-106">İlk işlemi sayıları toplar.</span><span class="sxs-lookup"><span data-stu-id="4be3a-106">The first operation sums the numbers.</span></span> <span data-ttu-id="4be3a-107">İkinci bir işlem sırasını en büyük değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4be3a-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="4be3a-108">![LINQ Toplama işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="4be3a-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="4be3a-109">Toplama işlemleri standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4be3a-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4be3a-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4be3a-110">Methods</span></span>  
  
|<span data-ttu-id="4be3a-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="4be3a-111">Method Name</span></span>|<span data-ttu-id="4be3a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4be3a-112">Description</span></span>|<span data-ttu-id="4be3a-113">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4be3a-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="4be3a-114">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="4be3a-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="4be3a-115">Toplama</span><span class="sxs-lookup"><span data-stu-id="4be3a-115">Aggregate</span></span>|<span data-ttu-id="4be3a-116">Değerleri bir koleksiyonun bir özel toplama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4be3a-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="4be3a-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="4be3a-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4be3a-118">Ortalama</span><span class="sxs-lookup"><span data-stu-id="4be3a-118">Average</span></span>|<span data-ttu-id="4be3a-119">Değerler koleksiyonu, ortalama değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4be3a-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4be3a-120">Sayısı</span><span class="sxs-lookup"><span data-stu-id="4be3a-120">Count</span></span>|<span data-ttu-id="4be3a-121">Bir koleksiyondaki öğelerin bir koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeler sayar.</span><span class="sxs-lookup"><span data-stu-id="4be3a-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4be3a-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="4be3a-122">LongCount</span></span>|<span data-ttu-id="4be3a-123">Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeler'büyük bir koleksiyondaki öğelerin sayar.</span><span class="sxs-lookup"><span data-stu-id="4be3a-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4be3a-124">Maks.</span><span class="sxs-lookup"><span data-stu-id="4be3a-124">Max</span></span>|<span data-ttu-id="4be3a-125">Bir koleksiyondaki en büyük değeri belirler.</span><span class="sxs-lookup"><span data-stu-id="4be3a-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4be3a-126">Min.</span><span class="sxs-lookup"><span data-stu-id="4be3a-126">Min</span></span>|<span data-ttu-id="4be3a-127">Bir koleksiyon en küçük değerin belirler.</span><span class="sxs-lookup"><span data-stu-id="4be3a-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4be3a-128">TOPLA</span><span class="sxs-lookup"><span data-stu-id="4be3a-128">Sum</span></span>|<span data-ttu-id="4be3a-129">Bir koleksiyondaki değerlerin toplamını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4be3a-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="4be3a-130">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="4be3a-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="4be3a-131">Ortalama</span><span class="sxs-lookup"><span data-stu-id="4be3a-131">Average</span></span>  
 <span data-ttu-id="4be3a-132">Aşağıdaki kod örneğinde `Aggregate Into Average` etme temsil eden sayı dizisi cinsinden ortalama sıcaklığı hesaplamak için Visual Basic'te yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4be3a-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a><span data-ttu-id="4be3a-133">Sayısı</span><span class="sxs-lookup"><span data-stu-id="4be3a-133">Count</span></span>  
 <span data-ttu-id="4be3a-134">Aşağıdaki kod örneğinde `Aggregate Into Count` 80 eşit veya daha büyük bir dizi değerlerde saymak için Visual Basic'te yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4be3a-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a><span data-ttu-id="4be3a-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="4be3a-135">LongCount</span></span>  
 <span data-ttu-id="4be3a-136">Aşağıdaki kod örneğinde `Aggregate Into LongCount` bir dizideki sayısını yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4be3a-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a><span data-ttu-id="4be3a-137">Maks.</span><span class="sxs-lookup"><span data-stu-id="4be3a-137">Max</span></span>  
 <span data-ttu-id="4be3a-138">Aşağıdaki kod örneğinde `Aggregate Into Max` etme temsil eden sayı dizisi cinsinden maksimum sıcaklığı hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4be3a-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a><span data-ttu-id="4be3a-139">Min.</span><span class="sxs-lookup"><span data-stu-id="4be3a-139">Min</span></span>  
 <span data-ttu-id="4be3a-140">Aşağıdaki kod örneğinde `Aggregate Into Min` etme temsil eden sayı dizisi cinsinden minimum sıcaklığı hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4be3a-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a><span data-ttu-id="4be3a-141">TOPLA</span><span class="sxs-lookup"><span data-stu-id="4be3a-141">Sum</span></span>  
 <span data-ttu-id="4be3a-142">Aşağıdaki kod örneğinde `Aggregate Into Sum` giderleri göstermek değerleri bir diziden Toplam gider miktarını hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4be3a-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4be3a-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4be3a-143">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="4be3a-144">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4be3a-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="4be3a-145">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="4be3a-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="4be3a-146">Nasıl yapılır: bir CSV metinde dosyasında (LINQ) (Visual Basic) sütun değerlerini hesaplama</span><span class="sxs-lookup"><span data-stu-id="4be3a-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [<span data-ttu-id="4be3a-147">Nasıl yapılır: Count, Sum veya Average verisi</span><span class="sxs-lookup"><span data-stu-id="4be3a-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [<span data-ttu-id="4be3a-148">Nasıl yapılır: bir sorgu sonucunda en düşük ve en büyük değeri Bul</span><span class="sxs-lookup"><span data-stu-id="4be3a-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [<span data-ttu-id="4be3a-149">Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4be3a-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [<span data-ttu-id="4be3a-150">Nasıl yapılır: sorgu için bir klasör (LINQ) (Visual Basic) kümesi bayt toplam sayısı</span><span class="sxs-lookup"><span data-stu-id="4be3a-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

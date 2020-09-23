---
title: Toplama İşlemleri
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 1cf82d8acfdb1f8b0fc33c324064574b0dd01f4a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078404"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="ddbc6-102">Toplama Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddbc6-102">Aggregation Operations (Visual Basic)</span></span>

<span data-ttu-id="ddbc6-103">Toplama işlemi, bir değerler koleksiyonundan tek bir değeri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="ddbc6-104">Bir toplama işlemine bir örnek, bir aylık günlük sıcaklık değerleri için günlük ortalama sıcaklığın hesaplanmasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="ddbc6-105">Aşağıdaki çizimde, bir dizi sayı üzerinde iki farklı toplama işlemi sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="ddbc6-106">İlk işlem, sayıları toplar.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-106">The first operation sums the numbers.</span></span> <span data-ttu-id="ddbc6-107">İkinci işlem dizideki en büyük değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![LINQ toplama işlemlerini gösteren çizim.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="ddbc6-109">Toplama işlemlerini gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ddbc6-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ddbc6-110">Methods</span></span>  
  
|<span data-ttu-id="ddbc6-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="ddbc6-111">Method Name</span></span>|<span data-ttu-id="ddbc6-112">Description</span><span class="sxs-lookup"><span data-stu-id="ddbc6-112">Description</span></span>|<span data-ttu-id="ddbc6-113">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ddbc6-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ddbc6-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="ddbc6-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="ddbc6-115">Toplama</span><span class="sxs-lookup"><span data-stu-id="ddbc6-115">Aggregate</span></span>|<span data-ttu-id="ddbc6-116">Bir koleksiyonun değerleri üzerinde özel toplama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="ddbc6-117">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ddbc6-118">Ortalama</span><span class="sxs-lookup"><span data-stu-id="ddbc6-118">Average</span></span>|<span data-ttu-id="ddbc6-119">Bir değerler koleksiyonunun ortalama değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ddbc6-120">Count</span><span class="sxs-lookup"><span data-stu-id="ddbc6-120">Count</span></span>|<span data-ttu-id="ddbc6-121">Bir koleksiyondaki öğeleri, isteğe bağlı olarak yalnızca bir koşul işlevini karşılayan öğeleri sayar.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ddbc6-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="ddbc6-122">LongCount</span></span>|<span data-ttu-id="ddbc6-123">Büyük bir koleksiyondaki öğeleri, isteğe bağlı olarak yalnızca bir koşul işlevini karşılayan öğeleri sayar.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ddbc6-124">En yüksek değer</span><span class="sxs-lookup"><span data-stu-id="ddbc6-124">Max</span></span>|<span data-ttu-id="ddbc6-125">Bir koleksiyondaki maksimum değeri belirler.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ddbc6-126">Min</span><span class="sxs-lookup"><span data-stu-id="ddbc6-126">Min</span></span>|<span data-ttu-id="ddbc6-127">Bir koleksiyondaki en küçük değeri belirler.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ddbc6-128">Toplam</span><span class="sxs-lookup"><span data-stu-id="ddbc6-128">Sum</span></span>|<span data-ttu-id="ddbc6-129">Bir koleksiyondaki değerlerin toplamını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ddbc6-130">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="ddbc6-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="ddbc6-131">Ortalama</span><span class="sxs-lookup"><span data-stu-id="ddbc6-131">Average</span></span>  

 <span data-ttu-id="ddbc6-132">Aşağıdaki kod örneği, `Aggregate Into Average` sıcaklığı temsil eden bir sayı dizisindeki ortalama sıcaklığı hesaplamak için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="ddbc6-133">Count</span><span class="sxs-lookup"><span data-stu-id="ddbc6-133">Count</span></span>  

 <span data-ttu-id="ddbc6-134">Aşağıdaki kod örneği, `Aggregate Into Count` 80 değerinden büyük veya buna eşit olan bir dizideki değer sayısını saymak için Visual Basic yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="ddbc6-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="ddbc6-135">LongCount</span></span>  

 <span data-ttu-id="ddbc6-136">Aşağıdaki kod örneği, `Aggregate Into LongCount` bir dizideki değer sayısını saymak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="ddbc6-137">En yüksek değer</span><span class="sxs-lookup"><span data-stu-id="ddbc6-137">Max</span></span>  

 <span data-ttu-id="ddbc6-138">Aşağıdaki kod örneği, `Aggregate Into Max` sıcaklıkları temsil eden bir sayı dizisindeki en fazla sıcaklığı hesaplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="ddbc6-139">Min</span><span class="sxs-lookup"><span data-stu-id="ddbc6-139">Min</span></span>  

 <span data-ttu-id="ddbc6-140">Aşağıdaki kod örneği, `Aggregate Into Min` sıcaklıkları temsil eden bir sayı dizisindeki minimum sıcaklığı hesaplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="ddbc6-141">Toplam</span><span class="sxs-lookup"><span data-stu-id="ddbc6-141">Sum</span></span>  

 <span data-ttu-id="ddbc6-142">Aşağıdaki kod örneği, `Aggregate Into Sum` giderleri temsil eden bir değer dizisinden toplam harcama miktarını hesaplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ddbc6-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddbc6-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ddbc6-144">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddbc6-144">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="ddbc6-145">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ddbc6-145">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="ddbc6-146">Nasıl yapılır: CSV metin dosyasında (LINQ) sütun değerlerini hesaplama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddbc6-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="ddbc6-147">Nasıl yapılır: Count, Sum veya Average Data</span><span class="sxs-lookup"><span data-stu-id="ddbc6-147">How to: Count, Sum, or Average Data</span></span>](../../language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="ddbc6-148">Nasıl yapılır: bir sorgu sonucunda en küçük veya en büyük değeri bulma</span><span class="sxs-lookup"><span data-stu-id="ddbc6-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="ddbc6-149">Nasıl yapılır: bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddbc6-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="ddbc6-150">Nasıl yapılır: bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddbc6-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

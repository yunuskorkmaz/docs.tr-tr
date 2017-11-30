---
title: "Toplama işlemleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d4b07eeb1d09d7db0f75d96629c816f66dbb128
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="91014-102">Toplama işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91014-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="91014-103">Bir toplama işlemi, tek bir değer değerler koleksiyonundan hesaplar.</span><span class="sxs-lookup"><span data-stu-id="91014-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="91014-104">Bir toplama işlemi örneği günlük sıcaklık değerler bir ayın eşitleyeceğini gelen ortalama günlük sıcaklık hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="91014-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="91014-105">Aşağıdaki çizimde, iki farklı toplama işlemlerde bir dizi sayının sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91014-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="91014-106">İlk işlemi sayıları toplar.</span><span class="sxs-lookup"><span data-stu-id="91014-106">The first operation sums the numbers.</span></span> <span data-ttu-id="91014-107">İkinci bir işlem sırasını en büyük değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="91014-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="91014-108">![LINQ Toplama işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="91014-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="91014-109">Toplama işlemleri standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="91014-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91014-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="91014-110">Methods</span></span>  
  
|<span data-ttu-id="91014-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="91014-111">Method Name</span></span>|<span data-ttu-id="91014-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91014-112">Description</span></span>|<span data-ttu-id="91014-113">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91014-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="91014-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="91014-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="91014-115">Toplama</span><span class="sxs-lookup"><span data-stu-id="91014-115">Aggregate</span></span>|<span data-ttu-id="91014-116">Değerleri bir koleksiyonun bir özel toplama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="91014-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="91014-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="91014-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="91014-118">Ortalama</span><span class="sxs-lookup"><span data-stu-id="91014-118">Average</span></span>|<span data-ttu-id="91014-119">Değerler koleksiyonu, ortalama değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="91014-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="91014-120">Sayısı</span><span class="sxs-lookup"><span data-stu-id="91014-120">Count</span></span>|<span data-ttu-id="91014-121">Bir koleksiyondaki öğelerin bir koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeler sayar.</span><span class="sxs-lookup"><span data-stu-id="91014-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="91014-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="91014-122">LongCount</span></span>|<span data-ttu-id="91014-123">Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeler'büyük bir koleksiyondaki öğelerin sayar.</span><span class="sxs-lookup"><span data-stu-id="91014-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="91014-124">Maks.</span><span class="sxs-lookup"><span data-stu-id="91014-124">Max</span></span>|<span data-ttu-id="91014-125">Bir koleksiyondaki en büyük değeri belirler.</span><span class="sxs-lookup"><span data-stu-id="91014-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="91014-126">Min.</span><span class="sxs-lookup"><span data-stu-id="91014-126">Min</span></span>|<span data-ttu-id="91014-127">Bir koleksiyon en küçük değerin belirler.</span><span class="sxs-lookup"><span data-stu-id="91014-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="91014-128">TOPLA</span><span class="sxs-lookup"><span data-stu-id="91014-128">Sum</span></span>|<span data-ttu-id="91014-129">Bir koleksiyondaki değerlerin toplamını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="91014-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="91014-130">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="91014-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="91014-131">Ortalama</span><span class="sxs-lookup"><span data-stu-id="91014-131">Average</span></span>  
 <span data-ttu-id="91014-132">Aşağıdaki kod örneğinde `Aggregate Into Average` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] etme temsil eden sayı dizisi cinsinden ortalama sıcaklığı hesaplamak için.</span><span class="sxs-lookup"><span data-stu-id="91014-132">The following code example uses the `Aggregate Into Average` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a><span data-ttu-id="91014-133">Sayısı</span><span class="sxs-lookup"><span data-stu-id="91014-133">Count</span></span>  
 <span data-ttu-id="91014-134">Aşağıdaki kod örneğinde `Aggregate Into Count` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 80 eşit veya daha büyük bir dizi değerlerde sayısını.</span><span class="sxs-lookup"><span data-stu-id="91014-134">The following code example uses the `Aggregate Into Count` clause in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a><span data-ttu-id="91014-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="91014-135">LongCount</span></span>  
 <span data-ttu-id="91014-136">Aşağıdaki kod örneğinde `Aggregate Into LongCount` bir dizideki sayısını yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="91014-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a><span data-ttu-id="91014-137">Maks.</span><span class="sxs-lookup"><span data-stu-id="91014-137">Max</span></span>  
 <span data-ttu-id="91014-138">Aşağıdaki kod örneğinde `Aggregate Into Max` etme temsil eden sayı dizisi cinsinden maksimum sıcaklığı hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="91014-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a><span data-ttu-id="91014-139">Min.</span><span class="sxs-lookup"><span data-stu-id="91014-139">Min</span></span>  
 <span data-ttu-id="91014-140">Aşağıdaki kod örneğinde `Aggregate Into Min` etme temsil eden sayı dizisi cinsinden minimum sıcaklığı hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="91014-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a><span data-ttu-id="91014-141">TOPLA</span><span class="sxs-lookup"><span data-stu-id="91014-141">Sum</span></span>  
 <span data-ttu-id="91014-142">Aşağıdaki kod örneğinde `Aggregate Into Sum` giderleri göstermek değerleri bir diziden Toplam gider miktarını hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="91014-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="91014-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91014-143">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="91014-144">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91014-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="91014-145">AGGREGATE tümcesi</span><span class="sxs-lookup"><span data-stu-id="91014-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="91014-146">Nasıl yapılır: bir CSV metinde dosyasında (LINQ) (Visual Basic) sütun değerlerini hesaplama</span><span class="sxs-lookup"><span data-stu-id="91014-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [<span data-ttu-id="91014-147">Nasıl yapılır: Count, Sum veya Average verisi</span><span class="sxs-lookup"><span data-stu-id="91014-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [<span data-ttu-id="91014-148">Nasıl yapılır: bir sorgu sonucunda en düşük ve en büyük değeri Bul</span><span class="sxs-lookup"><span data-stu-id="91014-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [<span data-ttu-id="91014-149">Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91014-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [<span data-ttu-id="91014-150">Nasıl yapılır: sorgu için bir klasör (LINQ) (Visual Basic) kümesi bayt toplam sayısı</span><span class="sxs-lookup"><span data-stu-id="91014-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

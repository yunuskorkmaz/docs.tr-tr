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
# <a name="aggregation-operations-visual-basic"></a>Toplama işlemleri (Visual Basic)
Bir toplama işlemi, tek bir değer değerler koleksiyonundan hesaplar. Bir toplama işlemi örneği günlük sıcaklık değerler bir ayın eşitleyeceğini gelen ortalama günlük sıcaklık hesaplıyor.  
  
 Aşağıdaki çizimde, iki farklı toplama işlemlerde bir dizi sayının sonuçlarını gösterir. İlk işlemi sayıları toplar. İkinci bir işlem sırasını en büyük değeri döndürür.  
  
 ![LINQ Toplama işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 Toplama işlemleri standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Toplama|Değerleri bir koleksiyonun bir özel toplama işlemi gerçekleştirir.|Yok.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Ortalama|Değerler koleksiyonu, ortalama değerini hesaplar.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Sayısı|Bir koleksiyondaki öğelerin bir koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeler sayar.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeler'büyük bir koleksiyondaki öğelerin sayar.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks.|Bir koleksiyondaki en büyük değeri belirler.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min.|Bir koleksiyon en küçük değerin belirler.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|TOPLA|Bir koleksiyondaki değerlerin toplamını hesaplar.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri  
  
### <a name="average"></a>Ortalama  
 Aşağıdaki kod örneğinde `Aggregate Into Average` etme temsil eden sayı dizisi cinsinden ortalama sıcaklığı hesaplamak için Visual Basic'te yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a>Sayısı  
 Aşağıdaki kod örneğinde `Aggregate Into Count` 80 eşit veya daha büyük bir dizi değerlerde saymak için Visual Basic'te yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a>LongCount  
 Aşağıdaki kod örneğinde `Aggregate Into LongCount` bir dizideki sayısını yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a>Maks.  
 Aşağıdaki kod örneğinde `Aggregate Into Max` etme temsil eden sayı dizisi cinsinden maksimum sıcaklığı hesaplamak için yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a>Min.  
 Aşağıdaki kod örneğinde `Aggregate Into Min` etme temsil eden sayı dizisi cinsinden minimum sıcaklığı hesaplamak için yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a>TOPLA  
 Aşağıdaki kod örneğinde `Aggregate Into Sum` giderleri göstermek değerleri bir diziden Toplam gider miktarını hesaplamak için yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Aggregate Yan Tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Nasıl yapılır: bir CSV metinde dosyasında (LINQ) (Visual Basic) sütun değerlerini hesaplama](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [Nasıl yapılır: Count, Sum veya Average verisi](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [Nasıl yapılır: bir sorgu sonucunda en düşük ve en büyük değeri Bul](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [Nasıl yapılır: sorgu için bir klasör (LINQ) (Visual Basic) kümesi bayt toplam sayısı](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

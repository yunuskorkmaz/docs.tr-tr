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
# <a name="aggregation-operations-visual-basic"></a>Toplama işlemleri (Visual Basic)
Bir toplama işlemi, değerlerin bir koleksiyonunu tek bir değeri hesaplar. Örnek olarak bir toplama işlemi, bir aya ait günlük sıcaklık değerleri değerinde gelen günlük ortalama sıcaklık hesaplıyor.  
  
 Aşağıdaki çizim, sayı dizisi üzerinde iki farklı toplama işlemlerinin sonuçlarını gösterir. İlk işlem sayıları toplar. İkinci işlem dizideki en büyük değeri döndürür.  
  
 ![LINQ Toplama işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 Toplama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Toplama|Değerleri bir koleksiyonun bir özel toplama işlemi gerçekleştirir.|Uygulanamaz.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Ortalama|Değerler koleksiyonu ortalama değerini hesaplar.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Sayı|Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeleri bir koleksiyondaki öğeleri sayar.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeleri büyük bir koleksiyondaki öğeleri sayar.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks.|Bir koleksiyondaki maksimum değeri belirler.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min.|Bir koleksiyondaki minimum değeri belirleyen.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Toplam|Bir koleksiyondaki değerlerin toplamını hesaplar.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifadesi söz dizimi örnekleri  
  
### <a name="average"></a>Ortalama  
 Aşağıdaki kod örneğinde `Aggregate Into Average` ortalama sıcaklık Sıcaklıkların temsil eden bir sayıdan oluşan hesaplamak için Visual Basic'te yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>Sayı  
 Aşağıdaki kod örneğinde `Aggregate Into Count` büyüktür veya eşittir 80'i dizideki değerleri saymak için Visual Basic'te yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 Aşağıdaki kod örneğinde `Aggregate Into LongCount` değerlerini bir dizi sayısını yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>Maks.  
 Aşağıdaki kod örneğinde `Aggregate Into Max` Sıcaklıkların temsil eden bir sayı dizisi en fazla sıcaklık hesaplamak için yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>Min.  
 Aşağıdaki kod örneğinde `Aggregate Into Min` en düşük Sıcaklıkların temsil eden bir sayı dizisi sıcaklık hesaplamak için yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>Toplam  
 Aşağıdaki kod örneğinde `Aggregate Into Sum` masrafları temsil eden değerleri bir diziden toplam masraf miktarını hesaplamak için yan tümcesi.  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Aggregate Yan Tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Nasıl yapılır: İşlem sütun değerleri bir CSV metinde dosyasında (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Nasıl yapılır: Count, Sum veya Average verisi](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [Nasıl yapılır: Bir sorgu sonucunda en düşük ve en fazla değeri bulma](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [Nasıl yapılır: En büyük dosya veya dizin ağacında (LINQ) (Visual Basic) dosyalar için sorgu](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [Nasıl yapılır: Sorgu (LINQ) (Visual Basic) klasör kümesi bayt toplam sayısı](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

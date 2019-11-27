---
title: Toplama İşlemleri
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 5c7f9344d379af2fed2a8f3d9f7c031c8ca00e8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345786"
---
# <a name="aggregation-operations-visual-basic"></a>Toplama Işlemleri (Visual Basic)
Toplama işlemi, bir değerler koleksiyonundan tek bir değeri hesaplar. Bir toplama işlemine bir örnek, bir aylık günlük sıcaklık değerleri için günlük ortalama sıcaklığın hesaplanmasından oluşur.  
  
 Aşağıdaki çizimde, bir dizi sayı üzerinde iki farklı toplama işlemi sonuçları gösterilmektedir. İlk işlem, sayıları toplar. İkinci işlem dizideki en büyük değeri döndürür.  
  
 ![LINQ toplama işlemlerini gösteren çizim.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Toplama işlemlerini gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Toplama|Bir koleksiyonun değerleri üzerinde özel toplama işlemi gerçekleştirir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Ortalama|Bir değerler koleksiyonunun ortalama değerini hesaplar.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Sayı|Bir koleksiyondaki öğeleri, isteğe bağlı olarak yalnızca bir koşul işlevini karşılayan öğeleri sayar.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Büyük bir koleksiyondaki öğeleri, isteğe bağlı olarak yalnızca bir koşul işlevini karşılayan öğeleri sayar.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks|Bir koleksiyondaki maksimum değeri belirler.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min|Bir koleksiyondaki en küçük değeri belirler.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|TOPLA|Bir koleksiyondaki değerlerin toplamını hesaplar.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri  
  
### <a name="average"></a>Ortalama  
 Aşağıdaki kod örneği, sıcaklıkları temsil eden bir sayı dizisindeki ortalama sıcaklığı hesaplamak için Visual Basic `Aggregate Into Average` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>Sayı  
 Aşağıdaki kod örneği, 80 değerinden büyük veya buna eşit bir dizideki değer sayısını saymak için Visual Basic `Aggregate Into Count` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 Aşağıdaki kod örneği, bir dizideki değer sayısını saymak için `Aggregate Into LongCount` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>Maks  
 Aşağıdaki kod örneği, sıcaklığı temsil eden bir sayı dizisindeki en fazla sıcaklığı hesaplamak için `Aggregate Into Max` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>Min  
 Aşağıdaki kod örneği, sıcaklıkları temsil eden bir sayı dizisindeki minimum sıcaklığı hesaplamak için `Aggregate Into Min` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>TOPLA  
 Aşağıdaki kod örneği, giderleri temsil eden bir değer dizisinden toplam harcama miktarını hesaplamak için `Aggregate Into Sum` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Aggregate Yan Tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Nasıl yapılır: CSV metin dosyasında (LINQ) sütun değerlerini hesaplama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Nasıl yapılır: Count, Sum veya Average Data](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [Nasıl yapılır: bir sorgu sonucunda en küçük veya en büyük değeri bulma](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [Nasıl yapılır: bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [Nasıl yapılır: bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)

---
title: Toplama işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: fd526a971e3d894a1219d06ee66127fddff07025
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692226"
---
# <a name="aggregation-operations-c"></a>Toplama işlemleri (C#)
Bir toplama işlemi, değerlerin bir koleksiyonunu tek bir değeri hesaplar. Örnek olarak bir toplama işlemi, bir aya ait günlük sıcaklık değerleri değerinde gelen günlük ortalama sıcaklık hesaplıyor.  
  
 Aşağıdaki çizim, sayı dizisi üzerinde iki farklı toplama işlemlerinin sonuçlarını gösterir. İlk işlem sayıları toplar. İkinci işlem dizideki en büyük değeri döndürür.  
  
 ![LINQ Toplama işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 Toplama işlemleri gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Toplama|Değerleri bir koleksiyonun bir özel toplama işlemi gerçekleştirir.|Uygulanamaz.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Ortalama|Değerler koleksiyonu ortalama değerini hesaplar.|Uygulanamaz.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Sayı|Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeleri bir koleksiyondaki öğeleri sayar.|Uygulanamaz.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Koşul işlevini karşılayan isteğe bağlı olarak yalnızca bu öğeleri büyük bir koleksiyondaki öğeleri sayar.|Uygulanamaz.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks.|Bir koleksiyondaki maksimum değeri belirler.|Uygulanamaz.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min.|Bir koleksiyondaki minimum değeri belirleyen.|Uygulanamaz.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Toplam|Bir koleksiyondaki değerlerin toplamını hesaplar.|Uygulanamaz.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Nasıl yapılır: Sütun değerleri bir CSV metinde dosyasında (LINQ) işlem (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Nasıl yapılır: En büyük dosya veya dosyalar sorgu (LINQ) bir dizin ağacındaki (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [Nasıl yapılır: Sorgu (LINQ) klasör kümesi bayt toplam sayısı (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)

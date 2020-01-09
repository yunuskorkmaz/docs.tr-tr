---
title: Toplama Işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: ea32becbb7ad0d3944eaea7b1b5448342ed438a5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347554"
---
# <a name="aggregation-operations-c"></a>Toplama Işlemleri (C#)
Toplama işlemi, bir değerler koleksiyonundan tek bir değeri hesaplar. Bir toplama işlemine bir örnek, bir aylık günlük sıcaklık değerleri için günlük ortalama sıcaklığın hesaplanmasından oluşur.  
  
 Aşağıdaki çizimde, bir dizi sayı üzerinde iki farklı toplama işlemi sonuçları gösterilmektedir. İlk işlem, sayıları toplar. İkinci işlem dizideki en büyük değeri döndürür.  
  
 ![LINQ toplama işlemlerini gösteren çizim.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Toplama işlemlerini gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C#Sorgu Ifadesi söz dizimi|Daha fazla bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Toplam|Bir koleksiyonun değerleri üzerinde özel toplama işlemi gerçekleştirir.|Yok.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Ortalama|Bir değerler koleksiyonunun ortalama değerini hesaplar.|Yok.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Count|Bir koleksiyondaki öğeleri, isteğe bağlı olarak yalnızca bir koşul işlevini karşılayan öğeleri sayar.|Yok.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Büyük bir koleksiyondaki öğeleri, isteğe bağlı olarak yalnızca bir koşul işlevini karşılayan öğeleri sayar.|Yok.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks.|Bir koleksiyondaki maksimum değeri belirler.|Yok.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min.|Bir koleksiyondaki en küçük değeri belirler.|Yok.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Toplam|Bir koleksiyondaki değerlerin toplamını hesaplar.|Yok.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genelC#bakış ()](./standard-query-operators-overview.md)
- [CSV metin dosyasında (LINQ) sütun değerlerini hesaplama (LINQ) (C#)](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Bir dizin ağacındaki en büyük dosya veya dosyalar için sorgu (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [Bir klasör kümesindeki toplam bayt sayısını sorgulama (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)

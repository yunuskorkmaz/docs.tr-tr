---
title: Toplama İşlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: ea32becbb7ad0d3944eaea7b1b5448342ed438a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347554"
---
# <a name="aggregation-operations-c"></a>Toplama İşlemleri (C#)
Toplama işlemi, değerler koleksiyonundan tek bir değer hesaplar. Bir toplama işlemine örnek olarak, günlük ortalama sıcaklık bir aylık günlük sıcaklık değerlerinden hesaplanır.  
  
 Aşağıdaki resimde, bir sayı dizisi üzerinde iki farklı toplama işleminin sonuçları gösterilmektedir. İlk işlem sayıları toplamlar. İkinci işlem, dizideki en büyük değeri döndürür.  
  
 ![LINQ toplama işlemlerini gösteren çizim.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Toplama işlemlerini gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Toplama|Koleksiyonun değerleri üzerinde özel bir toplama işlemi gerçekleştirir.|Geçerli değildir.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Ortalama|Değerler koleksiyonunun ortalama değerini hesaplar.|Geçerli değildir.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Sayı|Bir koleksiyondaki öğeleri, isteğe bağlı olarak yalnızca yüklem işlevini karşılayan öğeleri sayar.|Geçerli değildir.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|Longcount|Büyük bir koleksiyondaki öğeleri, isteğe bağlı olarak yalnızca yüklem işlevini karşılayan öğeleri sayar.|Geçerli değildir.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maks|Koleksiyondaki en büyük değeri belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Min|Koleksiyondaki minimum değeri belirler.|Geçerli değildir.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Toplam|Koleksiyondaki değerlerin toplamını hesaplar.|Geçerli değildir.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [CSV metin dosyasındaki sütun değerlerini nasıl hesaplar (LINQ) (C#)](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Dizin ağacındaki (LINQ) (C#) en büyük dosya veya dosyaları sorgulama](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [Klasörler kümesindeki toplam bayt sayısı (LINQ) (C#) için sorgulama](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)

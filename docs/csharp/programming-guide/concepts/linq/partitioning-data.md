---
title: Veri bölümleme (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 184d9d34e087a06ca3fad9b0a8dad571253b225d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702372"
---
# <a name="partitioning-data-c"></a>Veri bölümleme (C#)
LINQ to bölümleme öğelerini yeniden düzenleme ve bölümden birini döndüren bir giriş sırası iki bölümlere ayırma işlemi ifade eder.  
  
 Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçları gösterilmektedir. İlk işlem, dizideki ilk üç öğeleri döndürür. İkinci işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür. Üçüncü işlemi dizideki ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.  
  
 ![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Dizileri bölüm standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Atla|Bir dizideki belirtilen konuma kadar olan öğeleri atlar.|Uygulanamaz.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri atlar.|Uygulanamaz.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğelerin bir dizisi içinde belirtilen konuma kadar sürer.|Uygulanamaz.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri alır.|Uygulanamaz.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

---
title: Veri bölümleme (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 2e719b3a61b7c42d8ec6afe5fffe88a5bf83f82e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523467"
---
# <a name="partitioning-data-c"></a>Veri bölümleme (C#)
LINQ to bölümleme öğelerini yeniden düzenleme ve bölümden birini döndüren bir giriş sırası iki bölümlere ayırma işlemi ifade eder.  
  
 Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçları gösterilmektedir. İlk işlem, dizideki ilk üç öğeleri döndürür. İkinci işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür. Üçüncü işlemi dizideki ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.  
  
 ![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Dizileri bölüm standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Atla|Bir dizideki belirtilen konuma kadar olan öğeleri atlar.|Yok.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri atlar.|Yok.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğelerin bir dizisi içinde belirtilen konuma kadar sürer.|Yok.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri alır.|Yok.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Linq>  
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

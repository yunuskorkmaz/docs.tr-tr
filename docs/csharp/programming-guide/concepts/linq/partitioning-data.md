---
title: Veri bölümleme (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: b857c8c6e6b56a7263e6725a747e98ccfe4ff4fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832469"
---
# <a name="partitioning-data-c"></a>Veri bölümleme (C#)
LINQ to bölümleme öğelerini yeniden düzenleme ve bölümden birini döndüren bir giriş sırası iki bölümlere ayırma işlemi ifade eder.  
  
 Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçları gösterilmektedir. İlk işlem, dizideki ilk üç öğeleri döndürür. İkinci işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür. Üçüncü işlemi dizideki ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.  
  
 ![Çizim üç LINQ bölümleme işlemi gösterilmektedir.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Dizileri bölüm standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|C# sorgu ifade sözdizimi|Daha fazla bilgi|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Atla|Bir dizideki belirtilen konuma kadar olan öğeleri atlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri atlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğelerin bir dizisi içinde belirtilen konuma kadar sürer.|Geçerli değildir.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri alır.|Geçerli değildir.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

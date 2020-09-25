---
title: Verileri bölümleme (C#)
description: LINQ içindeki verileri nasıl bölümleyeceğinizi öğrenin. Bölümleme işlemlerinin sonuçlarını gösteren bir çizim görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 31beacd672addb3eb38ade8f2bf9cfae25f4d27a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176272"
---
# <a name="partitioning-data-c"></a>Verileri bölümleme (C#)

LINQ içinde bölümlendirme, bir giriş dizisini, öğeleri yeniden düzenleme ve sonra bölümlerden birini döndürmeden iki bölüme bölme işlemine başvurur.  
  
 Aşağıdaki çizimde, bir karakter dizisi üzerinde üç farklı bölümlendirme işlemi sonuçları gösterilmektedir. İlk işlem dizideki ilk üç öğeyi döndürür. İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür. Üçüncü işlem dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.  
  
 ![Üç LINQ bölümleme işlemini gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Bölüm dizilerinin aşağıdaki bölümde listelendiği standart sorgu işleci yöntemleri.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|C# sorgu Ifadesi sözdizimi|Daha Fazla Bilgi|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Atla|Bir dizide belirtilen konuma kadar olan öğeleri atlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri atlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğeleri bir dizide belirtilen konuma kadar alır.|Geçerli değildir.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri alır.|Geçerli değildir.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md)

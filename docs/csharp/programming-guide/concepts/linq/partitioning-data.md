---
title: Veri Bölümleme (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591581"
---
# <a name="partitioning-data-c"></a>Veri Bölümleme (C#)
LINQ'da bölümleme, öğeleri yeniden düzenlemeden ve bölümlerden birini döndürmeden bir giriş dizisini iki bölüme bölme işlemini ifade eder.  
  
 Aşağıdaki resimde, bir karakter dizisi üzerinde üç farklı bölümleme işleminin sonuçları gösterilmektedir. İlk işlem, dizideki ilk üç öğeyi döndürür. İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür. Üçüncü işlem, dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.  
  
 ![Üç LINQ bölümleme işlemi gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Bölüm dizilerinin aşağıdaki bölümde listelendirilen standart sorgu işleci yöntemleri.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|C# Sorgu İfade Sözdizimi|Daha Fazla Bilgi|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Atla|Öğeleri bir sırada belirli bir konuma atlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|Skipwhile|Bir öğe durumu karşılamayana kadar yüklem işlevini temel alan öğeleri atlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğeleri bir sırada belirli bir konuma alır.|Geçerli değildir.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|Takewhile|Bir öğe koşulu karşılamayana kadar bir yüklem işlevine dayalı öğeleri alır.|Geçerli değildir.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)

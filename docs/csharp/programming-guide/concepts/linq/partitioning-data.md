---
title: "Bölümleme verileri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32b95887e05767513dd818743dd1726149503b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-c"></a>Bölümleme verileri (C#)
LINQ bölümlendirme öğeleri yeniden düzenleme ve bölümlerden biri döndürme olmadan bir giriş sırası iki bölümlere ayırma işlemi ifade eder.  
  
 Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçlarını gösterir. İlk işlemi ilk üç öğeleri dizisi döndürür. İkinci bir işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür. Üçüncü işlem sırası ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.  
  
 ![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Dizileri bölüm standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|C# sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Atla|Öğeleri bir sırada belirtilen konum kadar atlar.|Yok.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri atlar.|Yok.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğeleri bir sırada belirtilen konum kadar sürer.|Yok.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri alır.|Yok.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

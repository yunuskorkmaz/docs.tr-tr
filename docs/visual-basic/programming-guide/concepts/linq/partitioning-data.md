---
title: Bölümleme veri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 17e929d3c95e079a0a73b8e8cadf51d3ece6f5f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="partitioning-data-visual-basic"></a>Bölümleme veri (Visual Basic)
LINQ bölümlendirme öğeleri yeniden düzenleme ve bölümlerden biri döndürme olmadan bir giriş sırası iki bölümlere ayırma işlemi ifade eder.  
  
 Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçlarını gösterir. İlk işlemi ilk üç öğeleri dizisi döndürür. İkinci bir işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür. Üçüncü işlem sırası ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.  
  
 ![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Dizileri bölüm standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Atla|Öğeleri bir sırada belirtilen konum kadar atlar.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri atlar.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğeleri bir sırada belirtilen konum kadar sürer.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri alır.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri  
  
### <a name="skip"></a>Atla  
 Aşağıdaki kod örneğinde `Skip` yan tümcesi kalan döndürmeden önce bir dizeler dizisi ilk dört dizelerde üzerinden geçmek için Visual Basic'de dizeleri dizideki.  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Aşağıdaki kod örneğinde `Skip While` dizenin ilk harfi olsa da bir dizi dizelerde üzerinden atlamak için Visual Basic'te yan tümcesi "a". Dizi kalan dizelerde döndürülür.  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 Aşağıdaki kod örneğinde `Take` ilk iki dizeyi bir dizeler dizisi dönmek için Visual Basic'te yan tümcesi.  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 Aşağıdaki kod örneğinde `Take While` beş veya daha az dize uzunluğu iken dizeleri dizisinden dönmek için Visual Basic'te yan tümcesi.  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Skip Yan Tümcesi](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Skip While Yan Tümcesi](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take Yan Tümcesi](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [Take While Yan Tümcesi](../../../../visual-basic/language-reference/queries/take-while-clause.md)

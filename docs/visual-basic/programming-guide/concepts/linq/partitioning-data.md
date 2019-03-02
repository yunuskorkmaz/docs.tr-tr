---
title: Bölümleme veri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 06db2ac3e556e647fed576a7fa0c89b881b748c9
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202151"
---
# <a name="partitioning-data-visual-basic"></a>Bölümleme veri (Visual Basic)
LINQ to bölümleme öğelerini yeniden düzenleme ve bölümden birini döndüren bir giriş sırası iki bölümlere ayırma işlemi ifade eder.  
  
 Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçları gösterilmektedir. İlk işlem, dizideki ilk üç öğeleri döndürür. İkinci işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür. Üçüncü işlemi dizideki ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.  
  
 ![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Dizileri bölüm standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Atla|Bir dizideki belirtilen konuma kadar olan öğeleri atlar.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri atlar.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğelerin bir dizisi içinde belirtilen konuma kadar sürer.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Bir öğe koşulu karşılamayan kadar bir koşul işlevini göre öğeleri alır.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifadesi söz dizimi örnekleri  
  
### <a name="skip"></a>Atla  
 Aşağıdaki kod örneğinde `Skip` yan tümcesi kalan döndürmeden önce ilk dört dizeler dize dizisi üzerinden geçmek için Visual Basic'de dizeleri dizide.  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Aşağıdaki kod örneğinde `Skip While` yan tümcesinde Visual Basic dizeleri bir dizideki dizenin ilk harfi olsa da atlamayı "a". Kalan dize dizisinde döndürülür.  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a>Take  
 Aşağıdaki kod örneğinde `Take` yan tümcesinde Visual Basic ilk iki dizenin bir dize dizisi döndürür.  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a>TakeWhile  
 Aşağıdaki kod örneğinde `Take While` dizenin uzunluğunu beş veya daha az olduğu sürece bir diziden dizeleri döndürmek için Visual Basic'te yan tümcesi.  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Skip Yan Tümcesi](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [Skip While Yan Tümcesi](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take Yan Tümcesi](../../../../visual-basic/language-reference/queries/take-clause.md)
- [Take While Yan Tümcesi](../../../../visual-basic/language-reference/queries/take-while-clause.md)

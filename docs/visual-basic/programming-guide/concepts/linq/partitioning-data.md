---
title: Veri Bölümlendirme
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2ab4e27ef6d825b9100fc3c15b7a9554ae49e516
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353147"
---
# <a name="partitioning-data-visual-basic"></a>Verileri bölümlendirme (Visual Basic)
LINQ içinde bölümlendirme, bir giriş dizisini, öğeleri yeniden düzenleme ve sonra bölümlerden birini döndürmeden iki bölüme bölme işlemine başvurur.  
  
 Aşağıdaki çizimde, bir karakter dizisi üzerinde üç farklı bölümlendirme işlemi sonuçları gösterilmektedir. İlk işlem dizideki ilk üç öğeyi döndürür. İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür. Üçüncü işlem dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.  
  
 ![Üç LINQ bölümleme işlemini gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Bölüm dizilerinin aşağıdaki bölümde listelendiği standart sorgu işleci yöntemleri.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Atla|Bir dizide belirtilen konuma kadar olan öğeleri atlar.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri atlar.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğeleri bir dizide belirtilen konuma kadar alır.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri alır.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri  
  
### <a name="skip"></a>Atla  
 Aşağıdaki kod örneği, dizideki kalan dizeleri döndürmeden önce bir dize dizisindeki ilk dört dizeyi atlamak için Visual Basic `Skip` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Aşağıdaki kod örneği, dizenin ilk harfi "a" iken bir dizideki dizeleri atlamak için Visual Basic `Skip While` yan tümcesini kullanır. Dizideki kalan dizeler döndürülür.  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a>Take  
 Aşağıdaki kod örneği, dizeler dizisindeki ilk iki dizeyi döndürmek için Visual Basic `Take` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a>TakeWhile  
 Aşağıdaki kod örneği, dizenin uzunluğu beş veya daha az olduğunda bir diziden dizeler döndürmek için Visual Basic `Take While` yan tümcesini kullanır.  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Skip Yan Tümcesi](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [Skip While Yan Tümcesi](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take Yan Tümcesi](../../../../visual-basic/language-reference/queries/take-clause.md)
- [Take While Yan Tümcesi](../../../../visual-basic/language-reference/queries/take-while-clause.md)

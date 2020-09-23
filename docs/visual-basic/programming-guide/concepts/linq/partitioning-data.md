---
title: Veri Bölümlendirme
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 07e33c4ce0d062a0f083d8970c0ad01f98923a52
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075323"
---
# <a name="partitioning-data-visual-basic"></a>Verileri bölümlendirme (Visual Basic)

LINQ içinde bölümlendirme, bir giriş dizisini, öğeleri yeniden düzenleme ve sonra bölümlerden birini döndürmeden iki bölüme bölme işlemine başvurur.  
  
 Aşağıdaki çizimde, bir karakter dizisi üzerinde üç farklı bölümlendirme işlemi sonuçları gösterilmektedir. İlk işlem dizideki ilk üç öğeyi döndürür. İkinci işlem ilk üç öğeyi atlar ve kalan öğeleri döndürür. Üçüncü işlem dizideki ilk iki öğeyi atlar ve sonraki üç öğeyi döndürür.  
  
 ![Üç LINQ bölümleme işlemini gösteren çizim.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Bölüm dizilerinin aşağıdaki bölümde listelendiği standart sorgu işleci yöntemleri.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Description|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Atla|Bir dizide belirtilen konuma kadar olan öğeleri atlar.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri atlar.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğeleri bir dizide belirtilen konuma kadar alır.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Öğe koşulu sağlamadığında bir koşul işlevine göre öğeleri alır.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri  
  
### <a name="skip"></a>Atla  

 Aşağıdaki kod örneği, `Skip` dizideki kalan dizeleri döndürmeden önce bir dize dizisindeki ilk dört dizeyi atlamak için Visual Basic yan tümcesini kullanır.  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a>SkipWhile  

 Aşağıdaki kod örneği, `Skip While` dizenin ilk harfi "a" iken bir dizideki dizeleri atlamak için Visual Basic yan tümcesini kullanır. Dizideki kalan dizeler döndürülür.  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a>Take  

 Aşağıdaki kod örneği, `Take` dizeler dizisindeki ilk iki dizeyi döndürmek için Visual Basic yan tümcesini kullanır.  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a>TakeWhile  

 Aşağıdaki kod örneği, `Take While` dizenin uzunluğu beş veya daha az olduğunda bir diziden dizeler döndürmek için Visual Basic yan tümcesini kullanır.  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Skip Yan Tümcesi](../../../language-reference/queries/skip-clause.md)
- [Skip While Yan Tümcesi](../../../language-reference/queries/skip-while-clause.md)
- [Take Yan Tümcesi](../../../language-reference/queries/take-clause.md)
- [Take While Yan Tümcesi](../../../language-reference/queries/take-while-clause.md)

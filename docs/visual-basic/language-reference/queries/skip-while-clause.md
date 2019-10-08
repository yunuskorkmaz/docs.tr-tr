---
title: Skip While Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004704"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While Tümcesi (Visual Basic)
Belirtilen koşul `true` olduğu sürece bir koleksiyondaki öğeleri atlar ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. İçin öğeleri test eden bir koşulu temsil eden bir ifade. İfade, bir @no__t 0 değeri veya bir `Boolean` olarak değerlendirilecek `Integer` gibi işlevsel eşdeğerini döndürmelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 yan tümcesi, sağlanan `expression` @no__t 2 ' ye dönene kadar öğeleri bir sorgu sonucunun başından atlar. @No__t-0 `false` döndürürse, sorgu kalan tüm öğeleri döndürür. @No__t-0, kalan sonuçlar için yok sayılır.  
  
 @No__t-0 yan tümcesi, belirli bir koşula uymayan bir sorgudaki tüm öğeleri dışlamak için `Where` yan tümcesinin `Where` tümceciğinden farklıdır. @No__t-0 yan tümcesi, yalnızca koşul karşılanmadığı sürece öğeleri dışlar. @No__t-0 yan tümcesi, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.  
  
 @No__t-0 yan tümcesini kullanarak bir sorgu sonucunun başından belirli sayıda sonucu atlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Birleşik Devletler ilk müşteri bulunana kadar sonuçları atlamak için `Skip While` yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Skip Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take While Yan Tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)

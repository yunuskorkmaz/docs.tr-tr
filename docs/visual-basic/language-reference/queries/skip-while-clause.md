---
title: Skip While Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 47703e445865435f5bf5312c3fe41833ac21aa3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333139"
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
|`expression`|Gerekli. İçin öğeleri test eden bir koşulu temsil eden bir ifade. İfade bir `Boolean` değeri veya bir `Boolean`olarak değerlendirilecek `Integer` gibi işlevsel eşdeğerini döndürmelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Skip While` yan tümcesi, sağlanan `expression` `false`dönene kadar öğeleri bir sorgu sonucunun başından atlar. `expression` `false`dönerse, sorgu kalan tüm öğeleri döndürür. Kalan sonuçlar için `expression` yok sayılır.  
  
 `Skip While` yan tümcesi, `Where` yan tümcesinin, belirli bir koşulu karşılamayan bir sorgudaki tüm öğeleri dışlamak için kullanılabilir `Where` yan tümcesinden farklıdır. `Skip While` yan tümcesi, yalnızca koşul karşılanmadığı sürece öğeleri dışlar. `Skip While` yan tümcesi, düzenli bir sorgu sonucuyla çalışırken en yararlı seçenektir.  
  
 `Skip` yan tümcesini kullanarak bir sorgu sonucunun başından itibaren belirli sayıda sonucu atlayabilirsiniz.  
  
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

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
ms.openlocfilehash: 9d95dc4a9f61a9ec3a50f9d594b31d673c2d3764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="skip-while-clause-visual-basic"></a>Skip While Tümcesi (Visual Basic)
Belirtilen bir koşul olduğu sürece bir koleksiyondaki öğelerin atlar `true` ve kalan öğeleri döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Öğeleri için test etmek için bir koşul temsil eden bir ifade. İfade döndürmelidir bir `Boolean` değeri veya işlevsel bir eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Skip While` Yan tümcesi atlar sağlanan kadar bir sorgu sonucunun başından öğeleri `expression` döndürür `false`. Sonra `expression` döndürür `false`, kalan tüm öğeleri sorgu döndürür. `expression` İçin kalan sonuçları göz ardı edilir.  
  
 `Skip While` Yan tümcesini farklı olarak `Where` yan tümcesinde, `Where` yan tümcesi, belirli bir koşula karşılamayan bir sorgudan tüm öğeleri dışlamak için kullanılabilir. `Skip While` Yan tümcesi koşula uyulmadığını yalnızca ilk kez kadar öğeleri dışlar. `Skip While` Sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlıdır.  
  
 Kullanarak bir sorgu sonucunun sonuçları başlangıçtan itibaren belirli sayıda atlayabilir `Skip` yan tümcesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Skip While` Amerika Birleşik Devletleri ilk müşteriden bulunana kadar sonuçları atlamak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Skip Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take While Yan Tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)

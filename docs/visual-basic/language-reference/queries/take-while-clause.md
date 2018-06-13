---
title: Take While Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 7e0a6bd77ca2594e9d74e669fcd9cddf91ee1cad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600916"
---
# <a name="take-while-clause-visual-basic"></a>Take While Tümcesi (Visual Basic)
Belirtilen bir koşul olduğu sürece bir koleksiyondaki öğeleri içeren `true` ve kalan öğeleri atlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Öğeleri için test etmek için bir koşul temsil eden bir ifade. İfade döndürmelidir bir `Boolean` değeri veya işlevsel bir eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Take While` Yan tümcesi bir sorgu sonucunun başından öğeleri sağlanan kadar içerir `expression` döndürür `false`. Sonra `expression` döndürür `false`, sorgu tüm kalan öğeleri atlayacaktır. `expression` İçin kalan sonuçları göz ardı edilir.  
  
 `Take While` Yan tümcesini farklı olarak `Where` yan tümcesinde, `Where` yan tümcesi, bir sorgudan belirli bir koşula tüm öğeleri dahil etmek için kullanılabilir. `Take While` Yan tümcesi koşula uyulmadığını yalnızca ilk kez kadar öğeleri içerir. `Take While` Sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Take While` siparişler olmadan ilk müşteri bulunana kadar sonuçları almak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take Yan Tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)

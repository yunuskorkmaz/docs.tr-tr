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
ms.openlocfilehash: 181cc641bb12329c898cc3bb226ea49f0836e979
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085361"
---
# <a name="take-while-clause-visual-basic"></a>Take While Tümcesi (Visual Basic)
Belirtilen koşul sürece öğeleri bir koleksiyona dahil `true` ve kalan öğeleri atlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Test etmek için öğeleri için bir koşulu temsil eden bir ifade. İfade döndürmelidir bir `Boolean` değer veya bir işlev eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Take While` Yan tümcesi başından itibaren bir sorgu sonucunun öğelerini sağlanan kadar içerir `expression` döndürür `false`. Sonra `expression` döndürür `false`, sorgunun kalan tüm öğeleri içerir. `expression` Kalan sonuçları göz ardı edilir.  
  
 `Take While` Yan tümcesi farklıdır `Where` yan tümcesinde, `Where` yan tümcesi, bir sorgudan belirli bir koşulu karşılayan tüm öğeleri dahil etmek için kullanılabilir. `Take While` Yan tümcesi koşulu karşılanmadı yalnızca ilk kez kadar öğeleri içerir. `Take While` Bir sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Take While` ilk müşteri siparişleri olmadan bulunana kadar sonuçları almak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/index.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take Yan Tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)

---
title: "Not İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac160aef7b7dc8acb8bf0211b403599692f2373c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="not-operator-visual-basic"></a>Not İşleci (Visual Basic)
Mantıksal değilleme gerçekleştiren bir `Boolean` ifadesi veya sayısal ifade bit tabanlı değil işlecini.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
 `expression`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin `Boolean` ifadeler, aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.  
  
|Varsa `expression` olduğu|Değeri `result` olduğu|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Sayısal ifadeler için `Not` işleci herhangi bir sayısal ifadeye bit değerini tersine çevirir ve karşılık gelen içinde bit ayarlar `result` aşağıdaki tabloya göre.  
  
|Varsa, bit `expression` olduğu|Bit `result` olduğu|  
|-------------------------------|----------------------------|  
|1.|0|  
|0|1.|  
  
> [!NOTE]
>  Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçleri düşük önceliğe sahip olduğundan, tüm bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmış.  
  
## <a name="data-types"></a>Veri Türleri  
 Bir Boole değilleme için sonuç veri türünde `Boolean`. Bit tabanlı değil işlecini için sonuç veri türü aynı değil `expression`. Ancak, deyim ise `Decimal`, sonuç `Long`.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Not` İşleci olabilir *aşırı*, kendi işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Not` mantıksal değilleme gerçekleştirileceği işleci bir `Boolean` ifade. Sonuç bir `Boolean` ifadesinin değerini tersine gösteren bir değer.  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 Önceki örnekte sonuçlarını üreten `False` ve `True`sırasıyla.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Not` mantıksal olumsuzlaştırma sayısal ifadesinin tek tek bit işleci. Sonuç düzeninde bit oturum bit dahil olmak üzere işleneni düzeninde karşılık gelen bit ters ayarlanır.  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 Önceki örnekte –11, –9 ve –7, sonuçları sırasıyla üretir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mantıksal ve bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

---
title: OrElse İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 28d1481b71979936bb16a2ecfb1140d85a674ef7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054997"
---
# <a name="orelse-operator-visual-basic"></a>OrElse İşleci (Visual Basic)
Kısa devre kapsamlı mantıksal veya işlecini iki gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` ifade.  
  
 `expression1`  
 Gerekli. Tüm `Boolean` ifade.  
  
 `expression2`  
 Gerekli. Tüm `Boolean` ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir mantıksal işlemi olduğu söylenir *kısa devre* , derlenmiş kod başka bir ifadenin sonucu bağlı olarak tek bir ifade değerlendirmesi devre dışı bırakabilir. Hesaplanan ilk ifadenin sonucu işlem son sonucunu belirlerse, ikinci ifade değerlendirilemiyor gerek yoktur nihai sonucu değiştiremezsiniz. Kısa devre Atlanan ifade karmaşıksa veya yordam çağrılarını içeriyorsa performansını iyileştirebilir.  
  
 Her ikisi de ifadeleri sonucunu verirse `True`, `result` olduğu `True`. Aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.  
  
|Varsa `expression1` olduğu|Ve `expression2` olduğu|Değerini `result` olduğu|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(Değerlendirilmedi)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Veri Türleri  
 `OrElse` İşleci yalnızca tanımlanmış [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic, her işlenen gerektiği şekilde dönüştürür `Boolean` ve tamamen işlemi gerçekleştiren `Boolean`. Sonucu bir sayısal tür için atarsanız, Visual Basic ondan dönüştürür `Boolean` bu türü. Bu, beklenmeyen davranışı üretebilir. Örneğin, `5 OrElse 12` sonuçlanır `–1` için dönüştürüldüğünde `Integer`.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [Veya işleci](../../../visual-basic/language-reference/operators/or-operator.md) ve [IsTrue işleci](../../../visual-basic/language-reference/operators/istrue-operator.md) olabilir *aşırı*, yani bu sınıf türünde bir işlenen sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, veya yapısı. Aşırı yükleme `Or` ve `IsTrue` işleçleri davranışını etkileyen `OrElse` işleci. Kodunuzu kullanıyorsa `OrElse` bir sınıf veya aşırı yapısı `Or` ve `IsTrue`, yeniden tanımlanan davranışlarını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `OrElse` mantıksal veya işlecini iki ifadelerini gerçekleştirmek için işleci. Sonuç bir `Boolean` gösteren bir değer ya da iki ifadenin true olup olmadığını. İlk ifade yanlışsa `True`, ikinci değerlendirilmez.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Yukarıdaki örnekte sonuçlarını üretir `True`, `True`, ve `False` sırasıyla. Hesaplamasında `firstCheck`, ilk zaten olduğundan ikinci ifade değerlendirilmez `True`. Ancak, ikinci ifade hesaplamasına değerlendirilir `secondCheck`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `If`... `Then` iki yordam çağrılarını içeren deyimi. İlk çağrı döndürürse `True`, ikinci yordam çağrılmaz. İkinci yordam, kodun bu bölümünü çalıştırıldığında, her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştiriyorsa bu beklenmeyen sonuçlara neden.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or İşleci](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

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
ms.openlocfilehash: 1ee3c1a5b6089f44742281eb40e2a7e9cb3e2812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604828"
---
# <a name="orelse-operator-visual-basic"></a>OrElse İşleci (Visual Basic)
Kapsayıcı mantıksal veya işlecini iki ifadeye kısa devre gerçekleştirir.  
  
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
 Mantıksal bir işlem olarak kabul edilir *kısa devre* derlenmiş kod başka bir ifade sonucuna bağlı olarak bir ifade değerlendirme devre dışı bırakabilir. İlk ifade Hesaplandı sonucunu işleminin son sonucu belirlerse, ikinci ifade değerlendirmek için gerek yoktur nihai sonucu değiştiremediğinizden. Kısa devre atlandığında ifade karmaşıksa veya yordam çağrıları içeriyorsa performansı artırabilir.  
  
 İçin veya her ikisi ifadeleri değerlendirin varsa `True`, `result` olan `True`. Aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.  
  
|Varsa `expression1` olduğu|Ve `expression2` olduğu|Değeri `result` olduğu|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(Değerlendirilmedi)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Veri Türleri  
 `OrElse` İşleci yalnızca için tanımlanmış [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic dönüştürür için gereken her işlenen `Boolean` ve tamamen işlemi gerçekleştirir `Boolean`. Sayısal bir tür sonucu atarsanız, Visual Basic ondan dönüştürür `Boolean` bu türü. Bu, beklenmeyen davranışları üretebilir. Örneğin, `5 OrElse 12` sonuçlanır `–1` için dönüştürüldüğünde `Integer`.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [Veya işleci](../../../visual-basic/language-reference/operators/or-operator.md) ve [IsTrue işleci](../../../visual-basic/language-reference/operators/istrue-operator.md) olabilir *aşırı*, o sınıfın tür işleneni sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, anlamına gelir veya yapısı. Aşırı yükleme `Or` ve `IsTrue` işleçleri davranışını etkileyen `OrElse` işleci. Kodunuzu kullanıyorsa `OrElse` bir sınıf veya overloads yapısı `Or` ve `IsTrue`, yeniden tanımlanan davranışlarını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `OrElse` iki ifadeleri mantıksal ayrım yapmak için işleci. Sonuç bir `Boolean` temsil eden bir değer ya da iki ifadenin doğru olup olmadığını. İlk ifade ise `True`, ikinci değerlendirilmez.  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 Önceki örnekte sonuçlarını üreten `True`, `True`, ve `False` sırasıyla. Hesaplanmasına `firstCheck`, ilk zaten olduğundan ikinci ifade değerlendirilmez `True`. Ancak, ikinci ifade hesaplaması olarak değerlendirilir `secondCheck`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `If`... `Then` iki yordam çağrıları içeren deyimi. İlk çağrıda döndürürse `True`, ikinci yordam çağrılmaz. İkinci yordam kodu'nun bu bölümünde çalıştığında, her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştiriyorsa bu beklenmeyen sonuçlara neden.  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mantıksal ve bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Or İşleci](../../../visual-basic/language-reference/operators/or-operator.md)  
 [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

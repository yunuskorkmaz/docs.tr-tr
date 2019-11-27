---
title: OrElse İşleci
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
ms.openlocfilehash: 361de44711c3b41411f2fa1dd81a3dd8db6b01e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348243"
---
# <a name="orelse-operator-visual-basic"></a>OrElse İşleci (Visual Basic)
İki ifadeye kısa devre uygulayan kapsamlı mantıksal ayırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` ifadesi.  
  
 `expression1`  
 Gerekli. Herhangi bir `Boolean` ifadesi.  
  
 `expression2`  
 Gerekli. Herhangi bir `Boolean` ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir. Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur. Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.  
  
 Ya da her iki ifade `True`olarak değerlendirilir `result` `True`. Aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.  
  
|`expression1`|Ve `expression2`|`result` değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(değerlendirilmedi)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Veri Türleri  
 `OrElse` işleci yalnızca [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)için tanımlanır. Visual Basic, ifadeyi değerlendirmeden önce `Boolean` gereken her işleneni dönüştürür. Sonucu sayısal bir türe atarsanız, Visual Basic `Boolean` `False` `0` haline gelir ve `True` `-1`hale gelir.
Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Aşırı Yükleme  
 [OR işleci](../../../visual-basic/language-reference/operators/or-operator.md) ve [IsTrue işleci](../../../visual-basic/language-reference/operators/istrue-operator.md) *aşırı*yüklenebilir, bu da bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir. `Or` aşırı yükleme ve `IsTrue` işleçleri `OrElse` işlecinin davranışını etkiler. Kodunuz, `Or` ve `IsTrue`aşırı yükleyen bir sınıf veya yapı üzerinde `OrElse` kullanıyorsa, yeniden tanımlanmış davranışlarını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye mantıksal ayırıcı gerçekleştirmek için `OrElse` işlecini kullanır. Sonuç, iki ifadeden birinin doğru olup olmadığını temsil eden bir `Boolean` değeridir. İlk ifade `True`, ikincisi değerlendirilmez.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Yukarıdaki örnek, sırasıyla `True`, `True`ve `False` sonuçları üretir. `firstCheck`hesaplamasında ikinci ifade değerlendirilmez çünkü ilki zaten `True`. Ancak, ikinci ifade `secondCheck`hesaplamasında değerlendirilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki yordam çağrısı içeren bir `If`...`Then` ifadesini gösterir. İlk çağrı `True`döndürürse ikinci yordam çağrılmaz. Bu, ikinci yordam kodun bu bölümü çalıştırıldığında her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştirdiğinde beklenmedik sonuçlar verebilir.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or İşleci](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue İşleci](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

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
ms.openlocfilehash: 3095a11523eeb8ec531c7f312fca74d2a070c92f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401413"
---
# <a name="orelse-operator-visual-basic"></a>OrElse İşleci (Visual Basic)
İki ifadeye kısa devre uygulayan kapsamlı mantıksal ayırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gereklidir. Herhangi bir `Boolean` ifade.  
  
 `expression1`  
 Gereklidir. Herhangi bir `Boolean` ifade.  
  
 `expression2`  
 Gereklidir. Herhangi bir `Boolean` ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir. Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur. Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.  
  
 Ya da her iki ifade olarak değerlendirilir `True` `result` `True` . Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .  
  
|İse `expression1`|Ve `expression2`|`result`Öğesinin değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(değerlendirilmedi)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Veri Türleri  
 `OrElse`İşleci yalnızca [Boole veri türü](../data-types/boolean-data-type.md)için tanımlanır. Visual Basic `Boolean` , ifadeyi değerlendirmeden önce her işleneni gerektiği şekilde dönüştürür. Sonucu sayısal bir türe atarsanız, Visual Basic, ve haline gelen bu türe dönüştürür `Boolean` `False` `0` `True` `-1` .
Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Aşırı Yükleme  
 [OR işleci](or-operator.md) ve [IsTrue işleci](istrue-operator.md) *aşırı*yüklenebilir, bu da bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir. `Or`Ve işleçlerini aşırı yüklemek `IsTrue` işlecin davranışını etkiler `OrElse` . Kodunuz `OrElse` , ve ' yi aşırı yükleyen bir sınıf veya yapı üzerinde kullanıyorsa `Or` `IsTrue` , yeniden tanımlanmış davranışlarını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `OrElse` iki ifadeye mantıksal ayırıcı gerçekleştirmek için işlecini kullanır. Sonuç, `Boolean` iki deyimden birinin doğru olup olmadığını temsil eden bir değerdir. İlk ifade ise, `True` ikincisi değerlendirilmez.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Yukarıdaki örnek,, ve gibi sonuçları üretir `True` `True` `False` . Hesaplamasında `firstCheck` ikinci ifade değerlendirilmez çünkü ilki zaten var `True` . Ancak, ikinci ifade hesaplamasında değerlendirilir `secondCheck` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `If` `Then` iki yordam çağrısı içeren bir... ifadesini gösterir. İlk çağrı döndürürse `True` ikinci yordam çağrılmaz. Bu, ikinci yordam kodun bu bölümü çalıştırıldığında her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştirdiğinde beklenmedik sonuçlar verebilir.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Or İşleci](or-operator.md)
- [IsTrue İşleci](istrue-operator.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

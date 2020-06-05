---
title: AndAlso İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371940"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso İşleci (Visual Basic)
İki ifadeye kısa devre mantıksal birlikte uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`result`|Gereklidir. Herhangi bir `Boolean` ifade. Sonuç, `Boolean` iki ifadenin karşılaştırmasının sonucudur.|  
|`expression1`|Gereklidir. Herhangi bir `Boolean` ifade.|  
|`expression2`|Gereklidir. Herhangi bir `Boolean` ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir. Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur. Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.  
  
 Her iki ifade ise olarak `True` değerlendirilir `result` `True` . Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .  
  
|İse `expression1`|Ve `expression2`|`result`Öğesinin değeri|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(değerlendirilmedi)|`False`|  
  
## <a name="data-types"></a>Veri Türleri  
 `AndAlso`İşleci yalnızca [Boole veri türü](../data-types/boolean-data-type.md)için tanımlanır. Visual Basic `Boolean` , ifadeyi değerlendirmeden önce her işleneni gerektiği şekilde dönüştürür. Sonucu sayısal bir türe atarsanız, Visual Basic, ve haline gelen bu türe dönüştürür `Boolean` `False` `0` `True` `-1` .
Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Aşırı Yükleme  
 [And işleci](and-operator.md) ve [IsFalse işleci](isfalse-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir. `And`Ve işleçlerini aşırı yüklemek `IsFalse` işlecin davranışını etkiler `AndAlso` . Kodunuz `AndAlso` , ve ' yi aşırı yükleyen bir sınıf veya yapı üzerinde kullanıyorsa `And` `IsFalse` , yeniden tanımlanmış davranışlarını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `AndAlso` iki ifadeye mantıksal bir birlikte gerçekleştirmek için işlecini kullanır. Sonuç, `Boolean` Tüm konkatılmış ifadenin doğru olup olmadığını temsil eden bir değerdir. İlk ifade ise, `False` ikincisi değerlendirilmez.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 Yukarıdaki örnek `True` sırasıyla,, ve sonuçlarını üretir `False` `False` . Hesaplamasında `secondCheck` ikinci ifade değerlendirilmez çünkü ilki zaten var `False` . Ancak, ikinci ifade hesaplamasında değerlendirilir `thirdCheck` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Function` dizinin öğeleri arasında belirli bir değeri arayan bir yordamı gösterir. Dizi boşsa veya dizi uzunluğu aşılmışsa, `While` ifade dizi öğesini arama değerine karşı test etmez.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [And İşleci](and-operator.md)
- [IsFalse İşleci](isfalse-operator.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

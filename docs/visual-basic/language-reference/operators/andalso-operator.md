---
title: AndAlso Işleci (Visual Basic)
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
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835222"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso Işleci (Visual Basic)
İki ifadeye kısa devre mantıksal birlikte uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Parçaya  
  
|Sözleşme Dönemi|Tanım|  
|---|---|  
|`result`|Gereklidir. Herhangi bir `Boolean` ifadesi. Sonuç, iki ifadenin karşılaştırmasının `Boolean` sonucu olur.|  
|`expression1`|Gereklidir. Herhangi bir `Boolean` ifadesi.|  
|`expression2`|Gereklidir. Herhangi bir `Boolean` ifadesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir. Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur. Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.  
  
 Her iki ifade `True` ' ı değerlendirirken, `result` `True` ' dir. Aşağıdaki tabloda `result` ' ın nasıl belirlendiği gösterilmektedir.  
  
|@No__t-0 ise|Ve `expression2`|@No__t-0 değeri|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(değerlendirilmedi)|`False`|  
  
## <a name="data-types"></a>Veri Türleri  
 @No__t-0 işleci yalnızca [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)için tanımlanır. Visual Basic, ifadeyi değerlendirmeden önce her işleneni gerektiği gibi `Boolean` ' a dönüştürür. Sonucu sayısal bir türe atarsanız, Visual Basic `Boolean` ' dan bu türe dönüştürür `False` `0` olur ve `True` `-1` olur.
Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Aşırı yükleme  
 [And işleci](../../../visual-basic/language-reference/operators/and-operator.md) ve [IsFalse işleci](../../../visual-basic/language-reference/operators/isfalse-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir. @No__t aşırı yükleme-0 ve `IsFalse` işleçleri `AndAlso` işlecinin davranışını etkiler. Kodunuz, `And` ve `IsFalse` ' yi aşırı yükleyen bir sınıf veya yapı üzerinde `AndAlso` kullanıyorsa, yeniden tanımlanmış davranışlarını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye mantıksal bir birlikte gerçekleştirmek için `AndAlso` işlecini kullanır. Sonuç, tüm konkatılmış ifadenin doğru olup olmadığını temsil eden bir `Boolean` değeridir. İlk ifade `False` ise, ikincisi değerlendirilmez.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 Yukarıdaki örnek sırasıyla `True`, `False` ve `False` sonuçları üretir. @No__t-0 hesaplamasında ikinci ifade değerlendirilmez çünkü ilki zaten `False` ' dir. Ancak, ikinci ifade `thirdCheck` hesaplamasında değerlendirilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizinin öğeleri arasında belirli bir değeri arayan `Function` yordamını gösterir. Dizi boşsa veya dizi uzunluğu aşılmışsa, `While` açıklaması dizi öğesini arama değerine karşı test etmez.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [IŞLEVLERE göre listelenen işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And Işleci](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse Işleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

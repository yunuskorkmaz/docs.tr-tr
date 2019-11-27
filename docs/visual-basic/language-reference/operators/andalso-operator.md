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
ms.openlocfilehash: b3801c7e05142e1bc793e3c9d49a6f6991756f9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350243"
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
|`result`|Gerekli. Herhangi bir `Boolean` ifadesi. Sonuç, iki ifadenin karşılaştırmasının `Boolean` sonucudur.|  
|`expression1`|Gerekli. Herhangi bir `Boolean` ifadesi.|  
|`expression2`|Gerekli. Herhangi bir `Boolean` ifadesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir. Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur. Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.  
  
 Her iki ifade de `True`olarak değerlendirilir `result` `True`. Aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.  
  
|`expression1`|Ve `expression2`|`result` değeri|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(değerlendirilmedi)|`False`|  
  
## <a name="data-types"></a>Veri Türleri  
 `AndAlso` işleci yalnızca [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md)için tanımlanır. Visual Basic, ifadeyi değerlendirmeden önce `Boolean` gereken her işleneni dönüştürür. Sonucu sayısal bir türe atarsanız, Visual Basic `Boolean` `False` `0` haline gelir ve `True` `-1`hale gelir.
Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Aşırı Yükleme  
 [And işleci](../../../visual-basic/language-reference/operators/and-operator.md) ve [IsFalse işleci](../../../visual-basic/language-reference/operators/isfalse-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir. `And` aşırı yükleme ve `IsFalse` işleçleri `AndAlso` işlecinin davranışını etkiler. Kodunuz, `And` ve `IsFalse`aşırı yükleyen bir sınıf veya yapı üzerinde `AndAlso` kullanıyorsa, yeniden tanımlanmış davranışlarını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye mantıksal bir birlikte gerçekleştirmek için `AndAlso` işlecini kullanır. Sonuç, tüm konkatılmış ifadenin doğru olup olmadığını temsil eden bir `Boolean` değeridir. İlk ifade `False`, ikincisi değerlendirilmez.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 Yukarıdaki örnek, sırasıyla `True`, `False`ve `False`sonuçları üretir. `secondCheck`hesaplamasında ikinci ifade değerlendirilmez çünkü ilki zaten `False`. Ancak, ikinci ifade `thirdCheck`hesaplamasında değerlendirilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizinin öğeleri arasında belirli bir değeri arayan bir `Function` yordamını gösterir. Dizi boşsa veya dizi uzunluğu aşılmışsa, `While` ifade dizi öğesini arama değerine karşı test etmez.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And İşleci](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse İşleci](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

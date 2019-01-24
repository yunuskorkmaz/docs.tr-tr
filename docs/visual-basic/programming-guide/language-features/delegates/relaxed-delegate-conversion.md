---
title: Gevşek Temsilci Dönüşümü (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: e2838b6473b8c00927073a530b4b49870fcfa9c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600393"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Gevşek Temsilci Dönüşümü (Visual Basic)
Gevşek temsilci dönüşümü bile bunların imzalarını aynı olmadığında abonelerimizin ve işlevleri temsilci veya işleyicileri için atamanızı sağlar. Bu nedenle, temsilciler bağlama zaten için yöntem çağrılarına izin verilen bağlama ile tutarlı olur.  
  
## <a name="parameters-and-return-type"></a>Parametreler ve dönüş türü  
 Tam imza eşleştirme yerine, aşağıdaki koşulların karşılanması gevşek dönüşüm gerektirir, `Option Strict` ayarlanır `On`:  
  
-   Bir genişletme dönüşümü her temsilcinin parametre veri türünden atanan işlevin karşılık gelen parametrenin veri türü için mevcut olmalıdır veya `Sub`. Aşağıdaki örnekte, temsilci `Del1` bir parametreye sahip bir `Integer`. Parametre `m` içinde atanan lambda ifadeleri var olan bir genişletme dönüşümü bir veri türüne sahip olmalıdır `Integer`, gibi `Long` veya `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     Daraltma dönüştürmeleri, yalnızca verilen `Option Strict` ayarlanır `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   Atanan işlevin dönüş türünden ters yönde genişletme dönüştürmesi olmalıdır veya `Sub` temsilcinin dönüş türü. Aşağıdaki örneklerde, her atanmış bir lambda ifadesinin gövdesi için widens bir veri türü değerlendirilmelidir `Integer` çünkü dönüş türü `del1` olduğu `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 Varsa `Option Strict` ayarlanır `Off`, kısıtlama genişletme her iki yönde de kaldırılır.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>Atlama parametre özellikleri  
 Gevşek temsilciler de tamamen atanan yöntemindeki parametre özellikleri atlamak izin ver:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 Bazı parametreler belirtin ve diğerleri atlamak olduğunu unutmayın.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 Parametreleri atlarsanız olanağı, burada birkaç karmaşık parametresi söz konusu olan bir olay işleyicisi tanımlama gibi bir durumda yararlıdır. Bazı olay işleyicilerine bağımsız değişkenleri kullanılmaz. Bunun yerine, işleyici üretileceği olayı kaydedilir ve bağımsız değişkenler yoksayar denetim durumunu doğrudan erişir. Gevşek temsilciler belirsizlikleri sonuç olduğunda bu tür bildirimleri bağımsız atlamak sağlar. Aşağıdaki örnekte, tam olarak belirtilen yöntem `OnClick` şeklinde yeniden yazılabilir `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf örnekleri  
 Lambda ifadeleri, önceki örneklerde, tür ilişkilerini görmek kolay hale getirmek için kullanılır. Ancak, aynı relaxations kullanan temsilci atamaları için izin verilen `AddressOf`, `Handles`, veya `AddHandler`.  
  
 Aşağıdaki örnekte, İşlevler `f1`, `f2`, `f3`, ve `f4` tüm atanabilir `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 Aşağıdaki örnek yalnızca geçerli olduğunda, `Option Strict` ayarlanır `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>Bırakma işlevi döndürür  
 Gevşek temsilci dönüşümü bir işleve atamanızı sağlar bir `Sub` temsilci, etkili bir şekilde işlev dönüş değeri yoksayılıyor. Ancak, atanamaz bir `Sub` için bir işlev temsilcisi. Aşağıdaki örnekte, işlevin adresini `doubler` atandığı `Sub` temsilci `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Lambda İfadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

---
title: Gevşek Temsilci Dönüşümü (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ac1246764d26d694d10b817b9195b13169d6d9be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651263"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Gevşek Temsilci Dönüşümü (Visual Basic)
Gevşek temsilci dönüşümü bile bunların imzalarını aynı olmadığında abonelerimizin ve işlevleri temsilci veya işleyicileri için atamanızı sağlar. Bu nedenle, temsilciler bağlama zaten için yöntem çağrılarına izin verilen bağlama ile tutarlı olur.  
  
## <a name="parameters-and-return-type"></a>Parametreler ve dönüş türü  
 Tam imza eşleştirme yerine, aşağıdaki koşulların karşılanması gevşek dönüşüm gerektirir, `Option Strict` ayarlanır `On`:  
  
- Bir genişletme dönüşümü her temsilcinin parametre veri türünden atanan işlevin karşılık gelen parametrenin veri türü için mevcut olmalıdır veya `Sub`. Aşağıdaki örnekte, temsilci `Del1` bir parametreye sahip bir `Integer`. Parametre `m` içinde atanan lambda ifadeleri var olan bir genişletme dönüşümü bir veri türüne sahip olmalıdır `Integer`, gibi `Long` veya `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Daraltma dönüştürmeleri, yalnızca verilen `Option Strict` ayarlanır `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- Atanan işlevin dönüş türünden ters yönde genişletme dönüştürmesi olmalıdır veya `Sub` temsilcinin dönüş türü. Aşağıdaki örneklerde, her atanmış bir lambda ifadesinin gövdesi için widens bir veri türü değerlendirilmelidir `Integer` çünkü dönüş türü `del1` olduğu `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 Varsa `Option Strict` ayarlanır `Off`, kısıtlama genişletme her iki yönde de kaldırılır.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Atlama parametre özellikleri  
 Gevşek temsilciler de tamamen atanan yöntemindeki parametre özellikleri atlamak izin ver:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Bazı parametreler belirtin ve diğerleri atlamak olduğunu unutmayın.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
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
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 Aşağıdaki örnek yalnızca geçerli olduğunda, `Option Strict` ayarlanır `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Bırakma işlevi döndürür  
 Gevşek temsilci dönüşümü bir işleve atamanızı sağlar bir `Sub` temsilci, etkili bir şekilde işlev dönüş değeri yoksayılıyor. Ancak, atanamaz bir `Sub` için bir işlev temsilcisi. Aşağıdaki örnekte, işlevin adresini `doubler` atandığı `Sub` temsilci `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda İfadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

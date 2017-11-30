---
title: "Gevşek Temsilci Dönüşümü (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cca3d09b538905714f627c9fa006187b8927383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Gevşek Temsilci Dönüşümü (Visual Basic)
Gevşek temsilci dönüşümü içerdikleri ve işlevleri temsilciler veya işleyicileri için kendi imzaları aynı olmadığında bile atamanızı sağlar. Bu nedenle, temsilciler bağlama zaten için yöntem çağrılarına izin verilen bağlama ile tutarlı olur.  
  
## <a name="parameters-and-return-type"></a>Parametreler ve dönüş türü  
 Aşağıdaki koşulların karşılanması gevşek dönüşüm tam imza eşleştirme yerine gerektirir zaman `Option Strict` ayarlanır `On`:  
  
-   Genişletme dönüşümü her temsilci parametre veri türünden atanan işlevi karşılık gelen parametrenin veri türü mevcut olmalıdır veya `Sub`. Aşağıdaki örnekte, temsilci `Del1` parametresinin, bir `Integer`. Parametre `m` atanan lambda ifadeleri var olduğu genişletme dönüştürme bir veri türüne sahip olmalıdır `Integer`, gibi `Long` veya `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     Daraltma dönüşümleri yalnızca izin verilen `Option Strict` ayarlanır `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   Genişletme dönüşümü atanan işlevinin dönüş türünden ters yönde mevcut olmalıdır veya `Sub` için temsilci dönüş türü. Aşağıdaki örneklerde, her atanan lambda ifadesi gövdesi için widens bir veri türü değerlendirilmelidir `Integer` dönüş türü olduğundan `del1` olan `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 Varsa `Option Strict` ayarlanır `Off`, kısıtlama genişletme her iki yönde de kaldırılır.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>Parametre belirtimleri atlama  
 Gevşek temsilci atanan yönteminde parametre özellikleri tamamen atlayın izin:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 Edemez bazı parametrelerini belirtin ve diğerleri atlayın olduğunu unutmayın.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 Parametrelerini atlayın yeteneği, burada birkaç karmaşık parametreleri dahil bir olay işleyicisi tanımlama gibi bir durumda yararlıdır. Bağımsız değişkenler bazı olay işleyicileri için kullanılmaz. Bunun yerine, işleyici üzerinde olayı kaydedilir ve bağımsız değişkenleri göz ardı eder denetim durumunu doğrudan erişir. Gevşek temsilci, bu tür bildirimleri belirsizlikleri sonuç olduğunda değişkenlerinde atlamak izin verir. Aşağıdaki örnekte, tam olarak belirtilen yöntem `OnClick` olarak yazılabilir `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf örnekleri  
 Lambda ifadeleri önceki örneklerde tür ilişkileri görmeyi kolaylaştırmak için kullanılır. Ancak, aynı relaxations kullanan temsilci atamaları izin verilen `AddressOf`, `Handles`, veya `AddHandler`.  
  
 Aşağıdaki örnekte, işlevleri `f1`, `f2`, `f3`, ve `f4` tüm atanabilir `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 Aşağıdaki örnekte yalnızca olduğunda geçerlidir olan `Option Strict` ayarlanır `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>Bırakma işlevi döndürür  
 Gevşek temsilci dönüşümü bir işleve atamanızı sağlar bir `Sub` temsilci, etkili bir şekilde işlevinin dönüş değeri yoksayılıyor. Ancak, atayamazsınız bir `Sub` için bir işlev temsilcisi. Aşağıdaki örnekte, işlevin adresini `doubler` atandığı `Sub` temsilci `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lambda ifadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Genişletme ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

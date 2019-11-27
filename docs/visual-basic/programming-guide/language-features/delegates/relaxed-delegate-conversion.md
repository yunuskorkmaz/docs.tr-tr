---
title: Gevşek Temsilci Dönüşümü
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345227"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Gevşek Temsilci Dönüşümü (Visual Basic)
Gevşek temsilci dönüştürme, imzaları özdeş olmasa bile temsilcilere veya işleyicilere alt öğeleri ve işlevleri atamanızı sağlar. Bu nedenle, temsilcilere bağlama, yöntem etkinleştirmeleri için zaten izin verilen bağlama ile tutarlı hale gelir.  
  
## <a name="parameters-and-return-type"></a>Parametreler ve dönüş türü  
 Tam imza eşleşmesi yerine, gevşek dönüştürme, `Option Strict` `On`olarak ayarlandığında aşağıdaki koşulların karşılanmasını gerektirir:  
  
- Her temsilci parametresinin veri türünden, atanan işlevin veya `Sub`karşılık gelen parametresinin veri türüne genişleyen bir dönüştürme bulunmalıdır. Aşağıdaki örnekte, temsilci `Del1` bir `Integer`parametresi vardır. Atanan Lambda ifadelerinde `m` parametresi, `Long` veya `Double`gibi `Integer`üzerinde genişleyen dönüştürme olan bir veri türüne sahip olmalıdır.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Daraltma dönüştürmelerine yalnızca `Option Strict` `Off`olarak ayarlandığında izin verilir.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- Genişleyen bir dönüştürme, atanan işlevin dönüş türünden ya da temsilcinin dönüş türüne `Sub` karşı yönde bulunmalıdır. Aşağıdaki örneklerde, `del1` dönüş türü `Integer`olduğundan, her bir atanan lambda ifadesinin gövdesi `Integer` bir veri türü olarak değerlendirilmelidir.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 `Option Strict` `Off`olarak ayarlanırsa, genişleyen kısıtlama her iki yönde de kaldırılır.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Parametre belirtimlerini atlama  
 Gevşek Temsilciler, atanan yöntemdeki parametre belirtimlerini tamamen atlamanızı da sağlar:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Bazı parametreleri belirtemezsiniz ve diğerlerini atlayamazsınız.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 Parametreleri atlama özelliği, çeşitli karmaşık parametrelerin dahil olduğu bir olay işleyicisini tanımlama gibi bir durumda yararlıdır. Bazı olay işleyicilerinin bağımsız değişkenleri kullanılmaz. Bunun yerine, işleyici doğrudan olayın kaydedildiği denetimin durumuna erişir ve bağımsız değişkenleri yoksayar. Gevşek Temsilciler, belirsizlikleri sonucu olmadığında bu bildirimlerin bağımsız değişkenlerini atlamanızı sağlar. Aşağıdaki örnekte, tam olarak belirtilen yöntem `OnClick` `RelaxedOnClick`olarak yeniden yazılabilir.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf örnekleri  
 Lambda ifadeleri, tür ilişkilerinin kolayca görmesini sağlamak için önceki örneklerde kullanılır. Ancak, `AddressOf`, `Handles`veya `AddHandler`kullanan temsilci atamaları için aynı relade izin verilir.  
  
 Aşağıdaki örnekte, `f1`, `f2`, `f3`ve `f4` işlevleri `Del1`atanabilir.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 Aşağıdaki örnek yalnızca `Option Strict` `Off`olarak ayarlandığında geçerlidir.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Işlev dönüşleri bırakılıyor  
 Gevşek temsilci dönüşümü, işlevin dönüş değerini etkin bir şekilde yok sayan bir `Sub` temsilcisine bir işlev atamanıza olanak sağlar. Ancak, bir işlev temsilcisine `Sub` atayamazsınız. Aşağıdaki örnekte, `doubler` işlev adresi `Sub` temsilci `Del3`atanır.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda İfadeleri](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: yordamları Visual Basic başka bir yordama geçirme](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

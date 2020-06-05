---
title: Gevşek Temsilci Dönüştürme
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: a581ffae77c496908d2e4e38df53491a54ae2ab8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410676"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Gevşek Temsilci Dönüşümü (Visual Basic)
Gevşek temsilci dönüştürme, imzaları özdeş olmasa bile temsilcilere veya işleyicilere alt öğeleri ve işlevleri atamanızı sağlar. Bu nedenle, temsilcilere bağlama, yöntem etkinleştirmeleri için zaten izin verilen bağlama ile tutarlı hale gelir.  
  
## <a name="parameters-and-return-type"></a>Parametreler ve dönüş türü  
 Tam imza eşleşmesi yerine, gevşek dönüştürme aşağıdaki koşulların yerine getirilmesi gerekir `Option Strict` `On` :  
  
- Her temsilci parametresinin veri türünden, atanan işlevin veya karşılık gelen parametresinin veri türüne genişleyen bir dönüştürme bulunmalıdır `Sub` . Aşağıdaki örnekte, temsilcinin bir `Del1` parametresi vardır `Integer` . `m`Atanan Lambda ifadelerinde parametresi, veya gibi bir üzerinde genişleyen dönüştürme olan bir veri türüne sahip olmalıdır `Integer` `Long` `Double` .  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Daraltma dönüştürmelerine yalnızca `Option Strict` öğesine ayarlandığında izin verilir `Off` .  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- Genişleyen bir dönüştürme, atanan işlevin dönüş türünden veya `Sub` temsilcinin dönüş türüne karşı yönde bulunmalıdır. Aşağıdaki örneklerde, atanan her lambda ifadesinin gövdesi, öğesinin dönüş türü olduğu için widens tarafından kullanılan bir veri türü olarak değerlendirilmelidir `Integer` `del1` `Integer` .  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 `Option Strict`Olarak ayarlanırsa `Off` , genişletme kısıtlaması her iki yönde de kaldırılır.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Parametre belirtimlerini atlama  
 Gevşek Temsilciler, atanan yöntemdeki parametre belirtimlerini tamamen atlamanızı da sağlar:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Bazı parametreleri belirtemezsiniz ve diğerlerini atlayamazsınız.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 Parametreleri atlama özelliği, çeşitli karmaşık parametrelerin dahil olduğu bir olay işleyicisini tanımlama gibi bir durumda yararlıdır. Bazı olay işleyicilerinin bağımsız değişkenleri kullanılmaz. Bunun yerine, işleyici doğrudan olayın kaydedildiği denetimin durumuna erişir ve bağımsız değişkenleri yoksayar. Gevşek Temsilciler, belirsizlikleri sonucu olmadığında bu bildirimlerin bağımsız değişkenlerini atlamanızı sağlar. Aşağıdaki örnekte, tam olarak belirtilen yöntem olarak yeniden `OnClick` yazılabilir `RelaxedOnClick` .  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf örnekleri  
 Lambda ifadeleri, tür ilişkilerinin kolayca görmesini sağlamak için önceki örneklerde kullanılır. Ancak,, veya kullanan temsilci atamaları için aynı relade izin verilir `AddressOf` `Handles` `AddHandler` .  
  
 Aşağıdaki örnekte,,, `f1` ve işlevleri `f2` `f3` `f4` öğesine atanabilir `Del1` .  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 Aşağıdaki örnek yalnızca `Option Strict` öğesine ayarlandığında geçerlidir `Off` .  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Işlev dönüşleri bırakılıyor  
 Gevşek temsilci dönüştürme, bir temsilciye bir işlevi atamanıza `Sub` ve işlevin dönüş değerini etkin bir şekilde yoksaymanızı sağlar. Ancak, bir `Sub` işlev temsilcisine bir atayamazsınız. Aşağıdaki örnekte, işlevin adresi `doubler` `Sub` temsilciye atanır `Del3` .  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda Ifadeleri](../procedures/lambda-expressions.md)
- [Genişletme ve Daraltma Dönüşümleri](../data-types/widening-and-narrowing-conversions.md)
- [Temsilciler](index.md)
- [Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme](how-to-pass-procedures-to-another-procedure.md)
- [Yerel Tür Arabirimi](../variables/local-type-inference.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)

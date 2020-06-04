---
title: Select...Case Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 3dedd43f920b493a0aca9ce48460b00815e1af5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404245"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case Deyimi (Visual Basic)
Bir ifadenin değerine bağlı olarak çeşitli deyim gruplarından birini çalıştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`testexpression`|Gereklidir. İfadesini. Tek bir veri türü ( `Boolean` , `Byte` ,,,, `Char` `Date` `Double` `Decimal` , `Integer` , `Long` , `Object` , `SByte` , `Short` , `Single` , `String` , `UInteger` , `ULong` , ve `UShort` ) olarak değerlendirilmelidir|  
|`expressionlist`|Bir bildirimde gereklidir `Case` . İçin eşleşme değerlerini temsil eden ifade yan tümceleri listesi `testexpression` . Birden çok ifade yan tümceleri virgüller ile ayrılmıştır. Her yan tümce aşağıdaki formlardan birini alabilir:<br /><br /> -   *İfade1* `To` *İfade2*<br />-[ `Is` ] *ComparisonOperator* *ifadesi*<br />-   *ifadesini*<br /><br /> `To`İçin bir eşleşme değerleri aralığının sınırlarını belirtmek için anahtar sözcüğünü kullanın `testexpression` . Değeri değerine `expression1` eşit veya ondan küçük olmalıdır `expression2` .<br /><br /> `Is` `=` `<>` `<` `<=` `>` `>=` Eşleştirme değerlerinde bir kısıtlama belirtmek için bir karşılaştırma işleci (,,,,, veya) ile anahtar sözcüğünü kullanın `testexpression` . `Is`Anahtar sözcüğü sağlanmazsa, *ComparisonOperator*öğesinden önce otomatik olarak eklenir.<br /><br /> Yalnızca belirten form, `expression` `Is` *ComparisonOperator* 'in eşittir işareti () olduğu formun özel durumu olarak değerlendirilir `=` . Bu form olarak değerlendirilir `testexpression`  =  `expression` .<br /><br /> İçindeki ifadeler `expressionlist` herhangi bir veri türünde olabilir, bu, türüne örtülü olarak dönüştürülebilir `testexpression` ve uygun olan `comparisonoperator` iki tür için geçerlidir.|  
|`statements`|İsteğe bağlı. `Case` `testexpression` ' Deki herhangi bir yan tümcesiyle eşleşiyorsa, çalıştıran bir veya daha fazla deyim `expressionlist` .|  
|`elsestatements`|İsteğe bağlı. Bir veya daha fazla deyimi, hiçbir `Case Else` `testexpression` deyimin içindeki herhangi bir yan tümce ile eşleşmezse çalışır `expressionlist` `Case` .|  
|`End Select`|`Select`... Oluşturma tanımını sonlandırır `Case` .|  
  
## <a name="remarks"></a>Açıklamalar  
 `testexpression`Any `Case` `expressionlist` yan tümcesiyle eşleşirse, bu `Case` deyimden sonraki deyimler Next `Case` , `Case Else` , veya deyimi ile çalışır `End Select` . Sonra Denetim aşağıdaki ifadeye geçer `End Select` . Birden `testexpression` `expressionlist` fazla yan tümcedeki bir yan tümcesiyle eşleşiyorsa `Case` , yalnızca ilk eşleşmeyi izleyen deyimler çalıştırılır.  
  
 `Case Else`Deyimi, `elsestatements` `testexpression` `expressionlist` diğer deyimlerden herhangi birinde ve yan tümcesi arasında eşleşme bulunmazsa çalıştırmak için öğesini tanıtmak için kullanılır `Case` . Gerekli olmasa da, `Case Else` `Select Case` öngörülenmeyen değerleri işlemek için oluşturma konusunda bir ifadeye sahip olmak iyi bir fikirdir `testexpression` . Hiçbir `Case` `expressionlist` yan tümce eşleşmez `testexpression` ve hiçbir deyimi yoksa `Case Else` , Denetim aşağıdaki deyime geçer `End Select` .  
  
 Her bir yan tümcesinde birden çok ifade veya Aralık kullanabilirsiniz `Case` . Örneğin, aşağıdaki satır geçerlidir.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> `Is`Ve deyimlerde kullanılan anahtar sözcük, `Case` `Case Else` nesne başvuru karşılaştırması Için kullanılan [, işleç işleci](../operators/is-operator.md)ile aynı değildir.  
  
 Karakter dizeleri için aralıklar ve birden çok ifade belirtebilirsiniz. Aşağıdaki örnekte, `Case` "elmalar" ile tam olarak eşit olan herhangi bir dizeyle eşleşir, alfabetik düzende "nut" ve "Soup" arasında bir değere sahiptir veya geçerli değeri ile tam olarak aynı değeri içerir `testItem` .  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ayarı, `Option Compare` dize karşılaştırmaları etkileyebilir. Altında `Option Compare Text` , "elmalar" ve "elmalar" dizeleri eşit olarak karşılaştırılır, ancak altında `Option Compare Binary` değildir.  
  
> [!NOTE]
> `Case`Birden çok yan tümcesini içeren bir ifade, kısa devre *dışı*olarak bilinen davranışları ortaya kaydedebilir. Visual Basic yan tümceleri soldan sağa değerlendirir ve biri ile eşleşme üretiyorsa `testexpression` , kalan yan tümceler değerlendirilmez. Kısa devre, performansı iyileştirebilir, ancak içindeki her ifadenin değerlendirilmesi bekleniyorsa beklenmeyen sonuçlar üretebilir `expressionlist` . Kısa devre dışı hakkında daha fazla bilgi için bkz. [Boolean ifadeleri](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Bir `Case` veya `Case Else` deyim bloğundaki kodun bloğunda daha fazla deyim çalıştırması gerekmiyorsa, deyimi kullanılarak bloğundan çıkabilir `Exit Select` . Bu, denetimi izleyen deyime hemen aktarır `End Select` .  
  
 `Select Case`kurulumlarını iç içe olabilir. İç içe yerleştirilmiş her `Select Case` oluşturma bir eşleşen `End Select` deyime sahip olmalı ve `Case` `Case Else` `Select Case` içinde iç içe olduğu dış oluşturma işleminin tek veya ifade bloğunda tamamen yer almalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Select Case` değişkeninin değerine karşılık gelen bir satırı yazmak için bir oluşturma kullanır `number` . İkinci `Case` ifade, geçerli değeri ile eşleşen değeri içerir `number` , bu nedenle "6 Ile 8 arasında", dahil "yazan bir ifade çalışır.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End Deyimi](end-statement.md)
- [If...Then...Else Deyimi](if-then-else-statement.md)
- [Option Compare Deyimi](option-compare-statement.md)
- [Exit Deyimi](exit-statement.md)

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
ms.openlocfilehash: 4dddfe5fbf7092c911291ffc6841e76f8c2748e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352821"
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
|`testexpression`|Gerekli. İfadesini. , Temel veri türlerinden biri olarak değerlendirilmelidir (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`ve `UShort`).|  
|`expressionlist`|`Case` bildiriminde gereklidir. `testexpression`için eşleşme değerlerini temsil eden ifade yan tümceleri listesi. Birden çok ifade yan tümceleri virgüller ile ayrılmıştır. Her yan tümce aşağıdaki formlardan birini alabilir:<br /><br /> -   *ifade1* `To` *İfade2*<br />-[`Is`] *ComparisonOperator* *ifadesi*<br />-   *ifadesi*<br /><br /> `testexpression`için bir eşleşme değerleri aralığının sınırlarını belirtmek üzere `To` anahtar sözcüğünü kullanın. `expression1` değeri `expression2`değerinden küçük veya bu değere eşit olmalıdır.<br /><br /> `<=`eşleşme değerlerinde bir kısıtlama belirtmek için karşılaştırma işleci (`=`, `<>`, `<`, `>`, `>=`veya `testexpression`) ile `Is` anahtar sözcüğünü kullanın. `Is` anahtar sözcüğü sağlanmazsa, *ComparisonOperator*öğesinden önce otomatik olarak eklenir.<br /><br /> Yalnızca `expression` belirten form, *ComparisonOperator* eşittir işareti (`=`) olduğu `Is` formunda özel bir durum olarak değerlendirilir. Bu form `testexpression` = `expression`olarak değerlendirilir.<br /><br /> `expressionlist` ifadeler herhangi bir veri türünde olabilir, bu, `testexpression` türüne örtülü olarak dönüştürülebilir ve uygun `comparisonoperator`, birlikte kullanıldığı iki tür için geçerlidir.|  
|`statements`|İsteğe bağlı. `testexpression` `expressionlist`herhangi bir yan tümcesiyle eşleşiyorsa çalıştırılan `Case` izleyen bir veya daha fazla deyim.|  
|`elsestatements`|İsteğe bağlı. `testexpression` `Case Else` sonraki bir veya daha fazla deyim, `Case` deyimlerinin herhangi bir `expressionlist` hiçbir yan tümcesiyle eşleşmezse.|  
|`End Select`|`Select`...`Case` oluşturma tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `testexpression` herhangi bir `Case` `expressionlist` yan tümcesiyle eşleşiyorsa, bu `Case` deyimini izleyen deyimler bir sonraki `Case`, `Case Else`veya `End Select` ifadesine kadar çalışır. Denetim daha sonra `End Select`izleyen ifadeye geçer. `testexpression` birden fazla `Case` yan tümcesindeki bir `expressionlist` yan tümcesiyle eşleşiyorsa, yalnızca ilk eşleşmeyi izleyen deyimler çalıştırılır.  
  
 `Case Else` deyimi, diğer `Case` deyimlerinin herhangi birinde `testexpression` ve `expressionlist` tümcesi arasında eşleşme bulunmazsa çalıştırılacak `elsestatements` tanıtmak için kullanılır. Gerekli olmasa da, öngörülemeyen `testexpression` değerlerini işlemek için `Select Case` oluşturma konusunda bir `Case Else` deyiminin olması iyi bir fikirdir. `Case` `expressionlist` yan tümcesinin `testexpression` eşleşmez ve `Case Else` deyimi yoksa, denetim `End Select`izleyen ifadeye geçer.  
  
 Her bir `Case` yan tümcesinde birden çok ifade veya Aralık kullanabilirsiniz. Örneğin, aşağıdaki satır geçerlidir.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> `Case` ve `Case Else` deyimlerde kullanılan `Is` anahtar sözcüğü, nesne başvuru karşılaştırması için kullanılan [, Işleç işleci](../../../visual-basic/language-reference/operators/is-operator.md)ile aynı değildir.  
  
 Karakter dizeleri için aralıklar ve birden çok ifade belirtebilirsiniz. Aşağıdaki örnekte, `Case`, "elmalar" ile tam olarak eşit olan herhangi bir dizeyle eşleşir, alfabetik düzende "nut" ve "Soup" arasında bir değere sahiptir veya geçerli `testItem`değeri ile tam aynı değeri içerir.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 `Option Compare` ayarı, dize karşılaştırmaları etkileyebilir. `Option Compare Text`altında, "elmalar" ve "elmalar" dizeleri eşit olarak karşılaştırılır, ancak `Option Compare Binary`altında değildir.  
  
> [!NOTE]
> Birden çok yan tümcesini içeren `Case` bir ifade, kısa devre *dışı*olarak bilinen davranışları ortaya kaydedebilir. Visual Basic yan tümceleri soldan sağa değerlendirir ve biri `testexpression`bir eşleşme üretirse, kalan yan tümceler değerlendirilmez. Kısa devre, performansı iyileştirebilir, ancak `expressionlist` içindeki her ifadenin değerlendirilmesi bekleniyorsa beklenmeyen sonuçlar üretebilir. Kısa devre dışı hakkında daha fazla bilgi için bkz. [Boolean ifadeleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Bir `Case` veya `Case Else` deyim bloğundaki kodun bloğunda daha fazla deyim çalıştırması gerekmiyorsa, `Exit Select` deyimini kullanarak bloğundan çıkabilir. Bu, denetimi hemen `End Select`izleyen deyime aktarır.  
  
 `Select Case` kurulumlarını iç içe olabilir. Her iç içe `Select Case` oluşturma, eşleşen bir `End Select` bildirimine sahip olmalı ve iç içe geçmiş dış `Select Case` oluşturma işleminin tek bir `Case` veya `Case Else` bir ifade bloğunda tamamen yer almalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `number`değişkeninin değerine karşılık gelen bir satırı yazmak için `Select Case` oluşturma kullanır. İkinci `Case` ifade, geçerli `number`değeri ile eşleşen değeri içerir, bu nedenle "6 ve 8. dahil" olarak yazan ifade çalışır.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)

---
title: Select...Case Deyimi (Visual Basic)
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
ms.openlocfilehash: 627318677270ba4ffa8ee430febea7ddf83bd245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957655"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case Deyimi (Visual Basic)
Bir ifadenin değerine bağlı olarak çeşitli deyim gruplarından birini çalıştırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`testexpression`|Gerekli. İfadesini. `Boolean`Tek bir veri türü (, `Decimal` ,`Object`,, `Double`,, ,,`Long` ,`SByte`,,,,,,,,,,, `Integer` `Date` `Char` `Byte` `Short` `Single`, ,`String` ,ve`UShort`). `UInteger` `ULong`|  
|`expressionlist`|Bir `Case` bildirimde gereklidir. İçin `testexpression`eşleşme değerlerini temsil eden ifade yan tümceleri listesi. Birden çok ifade yan tümceleri virgüller ile ayrılmıştır. Her yan tümce aşağıdaki formlardan birini alabilir:<br /><br /> -   *İfade1* `To` *İfade2*<br />-[ `Is` ] *ComparisonOperator* *ifadesi*<br />-   *ifadesini*<br /><br /> `To` İçin`testexpression`bir eşleşme değerleri aralığının sınırlarını belirtmek için anahtar sözcüğünü kullanın. Değeri `expression1` değerine eşit `expression2`veya ondan küçük olmalıdır.<br /><br /> `<=``=` `<>` `>` `<` `>=` Eşleştirmedeğerlerinde`testexpression`bir kısıtlama belirtmek için bir karşılaştırma işleci (,,,,, veya) ile anahtarsözcüğünükullanın.`Is` Anahtar sözcüğü sağlanmazsa, ComparisonOperator öğesinden önce otomatik olarak eklenir. `Is`<br /><br /> Yalnızca `expression` belirten form, *ComparisonOperator* 'in eşittir işareti (`=`) olduğu `Is` formun özel durumu olarak değerlendirilir. Bu form olarak `testexpression`  =  değerlendirilir`expression`.<br /><br /> İçindeki `expressionlist` ifadeler herhangi bir veri türünde olabilir, bu, `testexpression` türüne örtülü olarak dönüştürülebilir ve uygun `comparisonoperator` olan iki tür için geçerlidir.|  
|`statements`|İsteğe bağlı. ' Deki `Case` `testexpression` herhangibiryantümcesiyleeşleşiyorsa,çalıştıranbirveya`expressionlist`daha fazla deyim.|  
|`elsestatements`|İsteğe bağlı. Bir veya daha fazla deyimi `Case Else` , hiçbir `Case` deyimin içindeki `expressionlist` herhangi bir yan tümce ile eşleşmezse `testexpression` çalışır.|  
|`End Select`|Tanımını `Select`sonlandırır... `Case` oluşturma.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Case` `Case Else` `End Select` Any yantümcesiyle`Case`eşleşirse, bu `Case` deyimden sonraki deyimler Next,, veya deyimi ile çalışır. `testexpression` `expressionlist` Sonra Denetim aşağıdaki `End Select`ifadeye geçer. Birden fazla `Case` yan `expressionlist` tümcedeki bir yan tümcesiyle eşleşiyorsa,yalnızcailkeşleşmeyiizleyendeyimlerçalıştırılır.`testexpression`  
  
 `testexpression` `expressionlist` `elsestatements` Deyimi, diğer`Case` deyimlerden herhangi birinde ve yan tümcesi arasında eşleşme bulunmazsa çalıştırmak için öğesini tanıtmak için kullanılır. `Case Else` Gerekli olmasa da, öngörülenmeyen `Case Else` `testexpression` değerleri işlemek için `Select Case` oluşturma konusunda bir ifadeye sahip olmak iyi bir fikirdir. Hiçbir `Case` `End Select`yan tümce eşleşmez`testexpression` ve hiçbir`Case Else` deyimi yoksa, Denetim aşağıdaki deyime geçer. `expressionlist`  
  
 Her `Case` bir yan tümcesinde birden çok ifade veya Aralık kullanabilirsiniz. Örneğin, aşağıdaki satır geçerlidir.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> Ve deyimlerde kullanılan `Is`anahtarsözcük , nesne başvuru karşılaştırması için kullanılan [, işleç işleci](../../../visual-basic/language-reference/operators/is-operator.md)ile aynı değildir. `Case Else` `Case`  
  
 Karakter dizeleri için aralıklar ve birden çok ifade belirtebilirsiniz. Aşağıdaki örnekte, `Case` "elmalar" ile tam olarak eşit olan herhangi bir dizeyle eşleşir, alfabetik düzende "nut" ve "Soup" arasında bir değere sahiptir veya geçerli `testItem`değeri ile tam olarak aynı değeri içerir.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ayarı `Option Compare` , dize karşılaştırmaları etkileyebilir. Altında `Option Compare Text`, "elmalar" ve "elmalar" dizeleri eşit olarak karşılaştırılır, ancak `Option Compare Binary`altında değildir.  
  
> [!NOTE]
> Birden `Case` çok yan tümcesini içeren bir ifade, kısa devre *dışı*olarak bilinen davranışları ortaya kaydedebilir. Visual Basic yan tümceleri soldan sağa değerlendirir ve biri ile `testexpression`eşleşme üretiyorsa, kalan yan tümceler değerlendirilmez. Kısa devre, performansı iyileştirebilir, ancak içindeki `expressionlist` her ifadenin değerlendirilmesi bekleniyorsa beklenmeyen sonuçlar üretebilir. Kısa devre dışı hakkında daha fazla bilgi için bkz. [Boolean ifadeleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Bir `Case` `Exit Select` veya `Case Else` deyim bloğundaki kodun bloğunda daha fazla deyim çalıştırması gerekmiyorsa, deyimi kullanılarak bloğundan çıkabilir. Bu, denetimi izleyen `End Select`deyime hemen aktarır.  
  
 `Select Case`kurulumlarını iç içe olabilir. İç içe `Select Case` yerleştirilmiş her oluşturma bir eşleşen `End Select` deyime sahip olmalı ve içinde iç içe olduğu dış `Case` `Select Case` oluşturma `Case Else` işleminin tek veya ifade bloğunda tamamen yer almalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, değişkeninin `Select Case` `number`değerine karşılık gelen bir satırı yazmak için bir oluşturma kullanır. İkinci `Case` ifade, geçerli `number`değeri ile eşleşen değeri içerir, bu nedenle "6 ile 8 arasında", dahil "yazan bir ifade çalışır.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)

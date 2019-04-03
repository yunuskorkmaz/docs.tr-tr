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
ms.openlocfilehash: f99db4f1dc224e5f75ee67ba94c3745f28438724
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814620"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case Deyimi (Visual Basic)
Çeşitli deyim gruplarından birini bir ifadenin değerine bağlı olarak çalışır.  
  
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
|`testexpression`|Gerekli. Expression. Başlangıç veri türleri biri olarak değerlendirilmelidir (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, ve `UShort`).|  
|`expressionlist`|Gerekli bir `Case` deyimi. Eşleşme değerleri temsil eden ifadesi tümceleri listesi `testexpression`. Birden fazla ifade yan tümceleri virgülle ayrılır. Her bir yan tümceye aşağıdaki biçimlerden birini alabilir:<br /><br /> -   *İfade1* `To` *expression2*<br />-[ `Is` ] *comparisonoperator* *ifadesi*<br />-   *İfade*<br /><br /> Kullanım `To` anahtar sözcüğü, eşleşen bir dizi sınırlarını belirtmek için değerleri `testexpression`. Değerini `expression1` değerine eşit veya ondan daha az olmalıdır `expression2`.<br /><br /> Kullanım `Is` anahtar sözcüğü bir karşılaştırma işleci ile (`=`, `<>`, `<`, `<=`, `>`, veya `>=`) bir kısıtlama için eşleşen değerleri belirtmek için `testexpression`. Varsa `Is` anahtar sözcüğü sağlanmazsa, önce otomatik olarak eklenen *comparisonoperator*.<br /><br /> Yalnızca belirtme form `expression` özel bir durum olarak kabul edilir `Is` form nerede *comparisonoperator* eşittir işareti olan (`=`). Bu formu değerlendirmesinde `testexpression`  =  `expression`.<br /><br /> İfadelerde `expressionlist` türüne örtük olarak dönüştürülebilir sağlanan tüm veri türünde olabilir `testexpression` ve uygun `comparisonoperator` ile kullanıldığı iki türleri için geçerlidir.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyimlerini aşağıdaki `Case` çalıştırma olması durumunda `testexpression` herhangi yan tümcesinde eşleşen `expressionlist`.|  
|`elsestatements`|İsteğe bağlı. Bir veya daha fazla deyimlerini aşağıdaki `Case Else` çalıştırma olması durumunda `testexpression` herhangi yan tümcesinde eşleşmiyor `expressionlist` herhangi birinin `Case` deyimleri.|  
|`End Select`|Tanımını sonlandırır `Select`... `Case` oluşturma.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `testexpression` eşleşir `Case` `expressionlist` yan tümcesi, aşağıdaki deyimleri `Case` deyimi sonraki gerçekleştirdiğinizden `Case`, `Case Else`, veya `End Select` deyimi. Denetleyin ardından deyime geçer `End Select`. Varsa `testexpression` eşleşen bir `expressionlist` yan tümcesinde birden fazla `Case` yan tümcesi, yalnızca ilk eşleşmenin aşağıdaki deyimleri çalıştırın.  
  
 `Case Else` Deyimi tanıtmak için kullanılır `elsestatements` arasında hiçbir eşleşme bulunursa çalıştırılacak `testexpression` ve `expressionlist` herhangi diğer yan tümcesi `Case` deyimleri. Gerekli olmamakla birlikte, bu sahip için iyi bir fikirdir bir `Case Else` deyiminde, `Select Case` işlemek için yapı öngörülemeyen `testexpression` değerleri. Hayır ise `Case` `expressionlist` yan tümcesi eşleşen `testexpression` ve hiçbir `Case Else` deyimi, denetimi deyime geçer `End Select`.  
  
 Birden çok ifadeyi veya aralıkları her kullanabilirsiniz `Case` yan tümcesi. Örneğin, aşağıdaki satırı geçerli değil.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is` Kullanılan anahtar sözcüğü `Case` ve `Case Else` deyimleri aynı değil [işleci olan](../../../visual-basic/language-reference/operators/is-operator.md), nesne başvuru karşılaştırması için kullanılır.  
  
 Aralıkları ve karakter dizeleri için birden çok ifadeyi belirtebilirsiniz. Aşağıdaki örnekte, `Case` "apples" için tam olarak eşittir, alfabetik olarak "nuts" ve "A'dan" arasında bir değer olan veya geçerli değerini tam aynı değeri içeren herhangi bir dizeyle eşleşir `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ayarını `Option Compare` dize karşılaştırmaları etkileyebilir. Altında `Option Compare Text`, dizeleri "Apples" ve "apples" altında ancak eşit olarak karşılaştırmak `Option Compare Binary`, bunlar yapın.  
  
> [!NOTE]
>  A `Case` birden çok yan tümcesi ile deyimi olarak bilinen bir davranışı sergiler *kısa devre*. Visual Basic yan tümceleri soldan sağa doğru değerlendirilir ve varsa bir eşleşme ile üretir `testexpression`, kalan yan tümceleri değerlendirilmez. Kısa devre performansı geliştirebilir, ancak beklediğiniz tümcesindeki her ifade, beklenmedik sonuçlar üretebilirler `expressionlist` değerlendirilecek. Kısa devre daha fazla bilgi için bkz: [Boolean ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Kod içinde bir `Case` veya `Case Else` bloğunda deyimleri artık çalıştırmak deyim bloğunu gerekmez, blok kullanarak çıkabilirsiniz `Exit Select` deyimi. Bu denetim deyime hemen aktarır `End Select`.  
  
 `Select Case` yapılarını iç içe olabilir. Her iç içe `Select Case` eşleşen bir yapı olmalıdır `End Select` deyimi ve tamamen tek bir yer almalıdır `Case` veya `Case Else` deyim bloğu dış `Select Case` içinde bunu iç içe yapı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir `Select Case` değişkenin değerine karşılık gelen bir satır yazmak için yapı `number`. İkinci `Case` deyimi geçerli değeri ile eşleşen bir değer içeriyor `number`, "6 ve 8 dahil arasında" Yazar deyimi çalıştırır.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare Deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)

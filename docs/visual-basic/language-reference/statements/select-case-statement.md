---
title: Select...Case Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7527763a05ec32af88c6ba66ef717d839c33154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case Deyimi (Visual Basic)
İfadenin değerine bağlı olarak deyimlerinin birkaç gruplarından birini çalıştırır.  
  
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
|`testexpression`|Gerekli. İfade. Başlangıç veri türleri biri olarak değerlendirmeniz gerekir (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, ve `UShort`).|  
|`expressionlist`|Gerekli bir `Case` deyimi. Eşleşme değerlerini temsil eden ifade yan tümceleri listesi `testexpression`. Birden çok ifade yan tümceleri virgülle ayrılır. Her yan tümcesi aşağıdaki biçimlerden birini gerçekleştirebilirsiniz:<br /><br /> -   *İfade1* `To` *İfade2*<br />-[ `Is` ] *Karşılaştırmaİşleci* *ifadesi*<br />-   *ifade*<br /><br /> Kullanım `To` için eşleşen bir dizi sınırları belirtmek için anahtar sözcüğü değerler `testexpression`. Değeri `expression1` değerine eşit veya daha az olmalıdır `expression2`.<br /><br /> Kullanım `Is` anahtar sözcüğüyle bir karşılaştırma işleci (`=`, `<>`, `<`, `<=`, `>`, veya `>=`) eşleşme değerlerinde bir kısıtlama belirtmek için `testexpression`. Varsa `Is` anahtar sözcüğü sağlanmadı, önce otomatik olarak eklenen *Karşılaştırmaİşleci*.<br /><br /> Yalnızca belirtme form `expression` özel bir durum olarak kabul edilir `Is` form nerede *Karşılaştırmaİşleci* eşittir işaretidir (`=`). Bu form olarak değerlendirilir `testexpression`  =  `expression`.<br /><br /> İfadelerde `expressionlist` türüne örtük olarak dönüştürülebilir sağlanan tüm veri türünde olabilir `testexpression` ve uygun `comparisonoperator` ile kullanıldığı iki tür için geçerli değil.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyimleri aşağıdaki `Case` çalışma olması durumunda `testexpression` herhangi yan tümcesinde eşleşen `expressionlist`.|  
|`elsestatements`|İsteğe bağlı. Bir veya daha fazla deyimleri aşağıdaki `Case Else` çalışma olması durumunda `testexpression` herhangi yan tümcesinde eşleşmiyor `expressionlist` herhangi birinin `Case` deyimleri.|  
|`End Select`|Tanımını sonlandırır `Select`... `Case` oluşturma.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `testexpression` eşleşir `Case` `expressionlist` yan tümcesi, aşağıdaki deyimleri `Case` deyimi sonraki gerçekleştirdiğinizden `Case`, `Case Else`, veya `End Select` deyimi. Denetim sonra deyimi aşağıdaki geçer `End Select`. Varsa `testexpression` eşleşen bir `expressionlist` yan tümcesinde birden fazla `Case` yan tümcesi, yalnızca ilk eşleşmeye aşağıdaki deyimleri çalıştırın.  
  
 `Case Else` Deyimi tanıtmak için kullanılan `elsestatements` arasında eşleşme bulunamazsa, çalıştırmak için `testexpression` ve bir `expressionlist` yan tümcesinde herhangi diğer `Case` deyimleri. Gerekli değildir, ancak bunu sağlamak için iyi bir fikirdir bir `Case Else` deyiminde, `Select Case` işlemek için yapım öngörülemeyen `testexpression` değerleri. Öyle değilse `Case` `expressionlist` yan tümcesi ile eşleşen `testexpression` ve hiçbir `Case Else` deyimi, deyimi aşağıdaki denetim geçer `End Select`.  
  
 Birden çok ifadeyi veya aralıklar her kullanabilirsiniz `Case` yan tümcesi. Örneğin, aşağıdaki satırı geçerli değil.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is` Kullanılan anahtar sözcüğü `Case` ve `Case Else` deyimleri ile aynı değil [Is işlecini](../../../visual-basic/language-reference/operators/is-operator.md), nesne başvurusu karşılaştırma için kullanılır.  
  
 Aralıkları ve karakter dizeleri için birden çok ifadeyi belirtebilirsiniz. Aşağıdaki örnekte, `Case` "uygulama" tam olarak eşittir, alfabetik sırada "nuts" ve "Çorbası" arasında bir değer içeriyor veya geçerli değeri tam aynı değeri içeren herhangi bir dizeyle eşleşir `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ayarını `Option Compare` dize karşılaştırmaları etkileyebilir. Altında `Option Compare Text`, "Elmalar" ve "elmalar" dizeleri eşit olarak ancak altında karşılaştırmak `Option Compare Binary`, bunlar yapın.  
  
> [!NOTE]
>  A `Case` birden çok yan tümceleri deyimiyle olarak bilinen davranış sergileyen *kısa devre*. Visual Basic yan tümcelerini soldan sağa değerlendirir ve varsa bir eşleşme ile üreten `testexpression`, kalan yan tümceleri değerlendirilmez. Kısa devre performansı artırabilir, ancak her ifadesinde Bekleniyor durumunda beklenmeyen sonuçlara yol açabilir `expressionlist` değerlendirilecek. Kısa devre daha fazla bilgi için bkz: [Boole ifadeleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Varsa içindeki kod bir `Case` veya `Case Else` deyimi blok bloğunda bilgilerinin başka çalışması gerekmez, blok kullanarak çıkabilirsiniz `Exit Select` deyimi. Bu denetim deyimi aşağıdaki hemen aktarır `End Select`.  
  
 `Select Case`kurulumlarını iç içe. Her iç içe geçmiş `Select Case` yapım eşleşen olması gerekir `End Select` deyimi ve tek tamamen bulunmalıdır `Case` veya `Case Else` dış deyimi bloğunu `Select Case` yapı içinde bu iç içe geçmiş.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir `Select Case` değişkenin değerine karşılık gelen bir satır yazmak için yapım `number`. İkinci `Case` deyimi geçerli değeri ile eşleşen değerini içerdiği `number`, "6 ve 8 (bunlar dahil) arasında" Yazar deyim şekilde çalışır.  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [End deyimi](../../../visual-basic/language-reference/statements/end-statement.md)  
 [If... Then... Else deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Exit deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)

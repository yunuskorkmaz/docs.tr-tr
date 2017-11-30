---
title: If...Then...Else Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else Deyimi (Visual Basic)
İfadenin değerine bağlı olarak bir deyim grubunu koşullu yürütür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## <a name="parts"></a>Bölümler  
 `condition`  
 Gerekli. İfade. Değerlendirilmelidir `True` veya `False`, ya da örtük olarak parametresinin veri türü için `Boolean`.  
  
 İfade ise bir [null atanabilir](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değerlendiren değişkeni [hiçbir şey](../../../visual-basic/language-reference/nothing.md), koşul ifadesi gibi değilse kabul `True`ve `Else` bloğu. yürütülebilir.  
  
 `Then`  
 Tek satırlı sözdiziminde gerekli; birden çok satırlı sözdiziminde isteğe bağlı.  
  
 `statements`  
 İsteğe bağlı. Bir veya daha fazla deyimleri aşağıdaki `If`... `Then` varsa yürütülme `condition` değerlendiren `True`.  
  
 `elseifcondition`  
 Gerekli olursa `ElseIf` mevcuttur. İfade. Değerlendirilmelidir `True` veya `False`, ya da örtük olarak parametresinin veri türü için `Boolean`.  
  
 `elseifstatements`  
 İsteğe bağlı. Bir veya daha fazla deyimleri aşağıdaki `ElseIf`... `Then` varsa yürütülme `elseifcondition` değerlendiren `True`.  
  
 `elsestatements`  
 İsteğe bağlı. Hayır önceki varsa yürütülen bir veya daha fazla deyimleri `condition` veya `elseifcondition` ifadeyi hesaplar için `True`.  
  
 `End If`  
 Sonlandırır `If`... `Then`... `Else` bloğu.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="multiple-line-syntax"></a>Birden çok satırlı sözdizimi  
 Zaman bir `If`... `Then`... `Else` deyimi karşılaştı, `condition` test edilmiştir. Varsa `condition` olan `True`, aşağıdaki deyimleri `Then` yürütülür. Varsa `condition` olan `False`, her `ElseIf` deyimi (varsa) değerlendirildiği sırayla. Zaman bir `True``elseifcondition` , hemen ilişkili aşağıdaki deyimleri bulunan `ElseIf` yürütülür. Öyle değilse `elseifcondition` değerlendiren `True`, veya varsa hiçbir `ElseIf` deyimleri, aşağıdaki deyimleri `Else` yürütülür. Deyimlerini aşağıdaki yürütme sonrasında `Then`, `ElseIf`, veya `Else`, yürütülmeye deyimi aşağıdaki `End If`.  
  
 `ElseIf` Ve `Else` yan tümceleri olan isteğe bağlı hem de. Kadar olabilir `ElseIf` yan tümceleri aynı istediğiniz bir `If`... `Then`... `Else` deyimi ancak hiçbir `ElseIf` yan tümcesi sonra görünebilir bir `Else` yan tümcesi. `If`... `Then`... `Else` deyimleri iç içe geçirilemez diğer içinde.  
  
 Birden çok satırlı sözdiziminde `If` deyimi, ilk satırda yegane deyim olmalıdır. `ElseIf`, `Else`, Ve `End If` deyimleri yalnızca bir satır etiketle öncesinde. `If`... `Then`... `Else` bloğu ile bitmelidir bir `End If` deyimi.  
  
> [!TIP]
>  [Seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) birkaç olası değerlere sahip tek bir ifade değerlendirme daha yararlı olabilir.  
  
## <a name="single-line-syntax"></a>Tek satırlı sözdizimi  
 Tek satırlı sözdizimi kısa, basit testler için kullanabilirsiniz. Ancak, birden çok satırlı sözdizimi yapısı ve daha fazla esneklik sağlar ve okuma, korumanıza ve hata ayıklama daha kolay olur.  
  
 Hangi aşağıdaki `Then` anahtar sözcüğü bir deyim tek satırlı olup olmadığını belirlemek için incelenir `If`. Bir yorum dışında her şey sonra görünürse `Then` aynı satırda deyim tek satırlı kabul edilir `If` deyimi. Varsa `Then` yoksa, birden çok satırlı başlangıcı olmalıdır `If`... `Then`... `Else`.  
  
 Tek satırlı sözdiziminde sonucu olarak yürütülen birden çok deyime olabilir bir `If`... `Then` karar. Tüm ifadeler aynı satırda olmalıdır ve virgüllerle ayrılmış.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek birden çok satırlı sözdizimi kullanımı gösterilmektedir `If`... `Then`... `Else` deyimi.  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içeren iç içe geçmiş `If`... `Then`... `Else` deyimleri.  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek satırlı sözdizimi kullanımını göstermektedir.  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [İç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Karar yapıları](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Varsa işleci](../../../visual-basic/language-reference/operators/if-operator.md)

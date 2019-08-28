---
title: If...Then...Else Deyimi (Visual Basic)
ms.date: 04/16/2018
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
ms.openlocfilehash: 97ac8c82df14eb5ddc5e26fdaddf61cc774a0476
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046580"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else Deyimi (Visual Basic)

İfadenin değerine bağlı olarak bir deyim grubunu koşullu yürütür.

## <a name="syntax"></a>Sözdizimi

```
' Multiline syntax:
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

## <a name="quick-links-to-example-code"></a>Örnek koda hızlı bağlantılar

Bu makale, `If`... öğesinin kullanımını gösteren birkaç örnek içerir. `Then`... `Else` ifade:

* [Çok satırlı sözdizimi örneği](#multi-line)
* [İç içe geçmiş sözdizimi örneği](#nested)
* [Tek satırlık sözdizimi örneği](#single-line)

## <a name="parts"></a>Bölümler

`condition` \
Gerekli. İfadesini. Örtük olarak dönüştürülebilir `True` birveri`False`türü veya ya da olarak değerlendirilmelidir. `Boolean`

İfade [hiçbir şey](../../../visual-basic/language-reference/nothing.md)olarak `False` değerlendirilen [null yapılabilir](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` bir değişkense, koşul ifade gibi değerlendirilir ve `Else` blok yürütülür.

`Then` \
Tek satır sözdiziminde gereklidir; çok satırlı sözdiziminde isteğe bağlı.

`statements` \
İsteğe bağlı. Takip `If`eden bir veya daha fazla deyim... `Then` ,`condition` olarak değerlendirilirse`True`yürütülür.

`elseifcondition` \
Varsa `ElseIf` gereklidir. İfadesini. Örtük olarak dönüştürülebilir `True` birveri`False`türü veya ya da olarak değerlendirilmelidir. `Boolean`

`elseifstatements` \
İsteğe bağlı. Takip `ElseIf`eden bir veya daha fazla deyim... `Then` ,`elseifcondition` olarak değerlendirilirse`True`yürütülür.

`elsestatements` \
İsteğe bağlı. Önceki `condition` veya `elseifcondition` ifade olarak`True`değerlendirilen bir veya daha fazla deyim.

`End If` \
Öğesinin `If`çok satırlı sürümünü sonlandırır... `Then`... `Else` engelle.

## <a name="remarks"></a>Açıklamalar

### <a name="multiline-syntax"></a>Çok satırlı sözdizimi

Bir `If`... `Then`... ifadesiyle karşılaşıldı, `condition` test edildi. `Else` `condition` İse ,`True` aşağıdaki`Then` deyimler yürütülür. `condition` İse ,`False`her bir`ElseIf` ifade (varsa) sırayla değerlendirilir. Bir `True` `ElseIf` oluşturulduğunda, ilişkili olan deyimler hemen sonrasında yürütülür. `elseifcondition` , Olarak `elseifcondition` `True`hesaplanırsa `Else` veya deyim yoksa, `ElseIf` Aşağıdaki deyimler yürütülür. `Then`, Veya `ElseIf` `End If`sonraki deyimlerini yürüttükten sonra, yürütme aşağıdaki deyimle devam eder. `Else`

`ElseIf` Ve`Else` yan tümceleri her ikisi de isteğe bağlıdır. `ElseIf` Bir`If`... içinde istediğiniz sayıda yan tümce olabilir. `Then`... deyimi, ancak `Else` yan `ElseIf` tümce sonrasında hiçbir yan tümce görünmeyebilir. `Else` `If`... `Then`... `Else` deyimler birbirini içinde iç içe olabilir.

Çok satırlı sözdiziminde, `If` deyimin ilk satırdaki tek bir ifade olması gerekir. `ElseIf`, ,`Else`Ve deyimleri`End If` önünde yalnızca bir çizgi etiketi olabilir. `If`... `Then`... `Else` Block bir`End If` ifadesiyle bitmelidir.

> [!TIP]
> [Seç... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) , birkaç olası değeri olan tek bir ifadeyi değerlendirirken daha kullanışlı olabilir.

### <a name="single-line-syntax"></a>Tek satır sözdizimi

Doğru ise yürütmek üzere kod ile tek bir koşul için tek satırlık sözdizimini kullanabilirsiniz. Ancak, çok satırlı sözdizimi daha fazla yapı ve esneklik sağlar ve okunması, bakımını yapmak ve hata ayıklaması daha kolay olur.

Bir deyimin tek satırlı `If`olup olmadığını belirlemek için anahtarsözcüğüincelenir.`Then` Aynı satırdaki bir yorum dışında bir şey görünürse `Then` , ifadesi tek satırlık `If` bir ifade olarak değerlendirilir. Yoksa `Then` , birden çok satırlık `If`bir başlangıç olmalıdır... `Then`... `Else`.

Tek satır sözdiziminde, bir `If`... sonucu olarak birden çok deyim yürütülebileceğini sağlayabilirsiniz. `Then` karar. Tüm deyimler aynı satırda olmalıdır ve iki nokta üst üste ile ayrılmalıdır.

## <a name="multiline-syntax-example"></a>Çok satırlı sözdizimi örneği

<a name="multi-line"></a>

Aşağıdaki örnek, `If`... öğesinin çok satırlı sözdiziminin kullanımını gösterir. `Then`... `Else` bildirim.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>İç içe geçmiş sözdizimi örneği

<a name="nested"></a>

Aşağıdaki örnek iç içe geçmiş `If`... `Then`... `Else` deyimlerini.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Tek satırlık sözdizimi örneği

<a name="single-line"></a>Aşağıdaki örnek, tek satırlık sözdiziminin kullanımını gösterir.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case Deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Karar Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If İşleci](../../../visual-basic/language-reference/operators/if-operator.md)

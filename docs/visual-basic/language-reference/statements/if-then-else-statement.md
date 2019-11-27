---
title: If...Then...Else Deyimi
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
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351157"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else Deyimi (Visual Basic)

İfadenin değerine bağlı olarak bir deyim grubunu koşullu yürütür.

## <a name="syntax"></a>Sözdizimi

```vb
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

Bu makale `If`...`Then`...`Else` deyimin kullanımını gösteren birkaç örnek içerir:

- [Çok satırlı sözdizimi örneği](#multi-line)
- [İç içe geçmiş sözdizimi örneği](#nested)
- [Tek satırlık sözdizimi örneği](#single-line)

## <a name="parts"></a>Bölümler

`condition` \
Gerekli. İfadesini. `True` veya `False`veya `Boolean`örtük olarak dönüştürülebilir bir veri türü olarak değerlendirilmelidir.

İfade [hiçbir şey](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilen [null yapılabilir](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değişkense, koşul, ifade `False`gibi değerlendirilir ve `ElseIf` blokları varsa değerlendirilir veya varsa `Else` bloğu yürütülür.

`Then` \
Tek satır sözdiziminde gereklidir; çok satırlı sözdiziminde isteğe bağlı.

`statements` \
İsteğe bağlı. `condition` `True`olarak değerlendiriliyorsa yürütülen`Then` `If`... izleyen bir veya daha fazla deyim.

`elseifcondition` \
`ElseIf` varsa gereklidir. İfadesini. `True` veya `False`veya `Boolean`örtük olarak dönüştürülebilir bir veri türü olarak değerlendirilmelidir.

`elseifstatements` \
İsteğe bağlı. `elseifcondition` `True`olarak değerlendiriliyorsa yürütülen`Then` `ElseIf`... izleyen bir veya daha fazla deyim.

`elsestatements` \
İsteğe bağlı. Önceki `condition` veya `elseifcondition` ifadesi `True`olarak değerlendiriliyorsa yürütülen bir veya daha fazla deyim.

`End If` \
`If`...`Then`...`Else` bloğunun çok satırlı sürümünü sonlandırır.

## <a name="remarks"></a>Açıklamalar

### <a name="multiline-syntax"></a>Çok satırlı sözdizimi

Bir `If`...`Then`...`Else` ifadesiyle karşılaşıldığında, `condition` test edilir. `condition` `True`, `Then` Aşağıdaki deyimler yürütülür. `condition` `False`, her `ElseIf` deyimin (varsa) sırayla değerlendirilir. Bir `True` `elseifcondition` bulunduğunda, ilişkili `ElseIf` hemen sonraki deyimler yürütülür. `elseifcondition` `True`olarak değerlendiriliyorsa veya `ElseIf` deyim yoksa, `Else` Aşağıdaki deyimler yürütülür. `Then`, `ElseIf`veya `Else`sonraki deyimlerini yürüttükten sonra, yürütme `End If`aşağıdaki deyimle devam eder.

`ElseIf` ve `Else` yan tümceleri her ikisi de isteğe bağlıdır. Bir `If`...`Then`...`Else` ifadesinde istediğiniz sayıda `ElseIf` yan tümcesine sahip olabilirsiniz, ancak bir `ElseIf` yan tümcesi sonrasında hiçbir `Else` yan tümcesi görünebilirler. `If`...`Then`...`Else` deyimleri birbirini içinde iç içe olabilir.

Çok satırlı sözdiziminde, `If` deyimin ilk satırdaki tek bir ifade olması gerekir. `ElseIf`, `Else`ve `End If` deyimleri önünde yalnızca bir çizgi etiketi olabilir. `If`...`Then`...`Else` bloğunun bir `End If` ifadesiyle bitmesi gerekir.

> [!TIP]
> [Seç... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) , birkaç olası değeri olan tek bir ifadeyi değerlendirirken daha kullanışlı olabilir.

### <a name="single-line-syntax"></a>Tek satır sözdizimi

Doğru ise yürütmek üzere kod ile tek bir koşul için tek satırlık sözdizimini kullanabilirsiniz. Ancak, çok satırlı sözdizimi daha fazla yapı ve esneklik sağlar ve okunması, bakımını yapmak ve hata ayıklaması daha kolay olur.

Bir deyimin tek satırlı bir `If`olup olmadığını belirlemek için `Then` anahtar sözcüğünün incelenmesi önerilir. Aynı satırdaki `Then` sonrasında açıklama dışında bir şey görünürse, ifadesi tek satırlık bir `If` ifadesi olarak değerlendirilir. `Then` yoksa, birden çok satırlık bir `If`...`Then`...`Else`başlangıcı olmalıdır.

Tek satır sözdiziminde, bir `If`...`Then` kararının sonucu olarak birden çok deyim yürütülebileceğini sağlayabilirsiniz. Tüm deyimler aynı satırda olmalıdır ve iki nokta üst üste ile ayrılmalıdır.

## <a name="multiline-syntax-example"></a>Çok satırlı sözdizimi örneği

<a name="multi-line"></a>

Aşağıdaki örnek, `If`...`Then`...`Else` ifadesinin çok satırlı sözdiziminin kullanımını gösterir.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>İç içe geçmiş sözdizimi örneği

<a name="nested"></a>

Aşağıdaki örnek iç içe geçmiş `If`...`Then`...`Else` deyimlerini içerir.

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

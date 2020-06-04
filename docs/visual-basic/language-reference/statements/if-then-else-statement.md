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
ms.openlocfilehash: 0884b71c24742286e695e720add9d00dd4bfe52b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404595"
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

Bu makale, `If` .. `Then` . öğesinin kullanımını gösteren birkaç örnek içerir. ...`Else` Ekstre

- [Çok satırlı sözdizimi örneği](#multi-line)
- [İç içe geçmiş sözdizimi örneği](#nested)
- [Tek satırlık sözdizimi örneği](#single-line)

## <a name="parts"></a>Bölümler

`condition` \
Gereklidir. İfadesini. `True` `False` Örtük olarak dönüştürülebilir bir veri türü veya ya da olarak değerlendirilmelidir `Boolean` .

İfade [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` [hiçbir şey](../nothing.md)olarak değerlendirilen null yapılabilir bir değişkense, koşul ifade gibi değerlendirilir `False` ve bloklar varsa `ElseIf` değerlendirilir veya varsa, `Else` blok yürütülür.

`Then` \
Tek satır sözdiziminde gereklidir; çok satırlı sözdiziminde isteğe bağlı.

`statements` \
İsteğe bağlı. Bir veya daha fazla deyimi. `If` .. `Then` , `condition` olarak değerlendirilirse yürütülür `True` .

`elseifcondition` \
Varsa gereklidir `ElseIf` . İfadesini. `True` `False` Örtük olarak dönüştürülebilir bir veri türü veya ya da olarak değerlendirilmelidir `Boolean` .

`elseifstatements` \
İsteğe bağlı. Bir veya daha fazla deyimi. `ElseIf` .. `Then` , `elseifcondition` olarak değerlendirilirse yürütülür `True` .

`elsestatements` \
İsteğe bağlı. Önceki `condition` veya `elseifcondition` ifade olarak değerlendirilen bir veya daha fazla deyim `True` .

`End If` \
Öğesinin çok satırlı sürümünü sonlandırır `If` ... `Then` ...`Else` engelleyin.

## <a name="remarks"></a>Açıklamalar

### <a name="multiline-syntax"></a>Çok satırlı sözdizimi

Bir `If` .. `Then` . ...`Else` ifadesiyle karşılaşıldı, `condition` test edildi. `condition`İse `True` , aşağıdaki deyimler `Then` yürütülür. `condition`İse `False` , her `ElseIf` bir ifade (varsa) sırayla değerlendirilir. Bir `True` `elseifcondition` oluşturulduğunda, ilişkili olan deyimler hemen sonrasında `ElseIf` yürütülür. `elseifcondition`, Olarak hesaplanırsa `True` veya `ElseIf` deyim yoksa, aşağıdaki deyimler `Else` yürütülür. , Veya sonraki deyimlerini yürüttükten sonra, `Then` `ElseIf` `Else` yürütme aşağıdaki deyimle devam eder `End If` .

`ElseIf`Ve `Else` yan tümceleri her ikisi de isteğe bağlıdır. `ElseIf`Bir `If` .. `Then` . içinde istediğiniz sayıda yan tümce olabilir. ...`Else` deyimi, ancak `ElseIf` yan tümce sonrasında hiçbir yan tümce görünmeyebilir `Else` . `If`...`Then` ...`Else` deyimler birbirini içinde iç içe olabilir.

Çok satırlı sözdiziminde, `If` deyimin ilk satırdaki tek bir ifade olması gerekir. `ElseIf`, `Else` , Ve `End If` deyimleri önünde yalnızca bir çizgi etiketi olabilir. `If`.. `Then` . ...`Else` Block bir `End If` ifadesiyle bitmelidir.

> [!TIP]
> [Seç... Case deyimi](select-case-statement.md) , birkaç olası değeri olan tek bir ifadeyi değerlendirirken daha kullanışlı olabilir.

### <a name="single-line-syntax"></a>Tek satır sözdizimi

Doğru ise yürütmek üzere kod ile tek bir koşul için tek satırlık sözdizimini kullanabilirsiniz. Ancak, çok satırlı sözdizimi daha fazla yapı ve esneklik sağlar ve okunması, bakımını yapmak ve hata ayıklaması daha kolay olur.

`Then`Bir deyimin tek satırlı olup olmadığını belirlemek için anahtar sözcüğü incelenir `If` . Aynı satırdaki bir yorum dışında bir şey görünürse `Then` , ifadesi tek satırlık bir ifade olarak değerlendirilir `If` . Yoksa `Then` , birden çok satırlık bir başlangıç olmalıdır `If` ... `Then` ...`Else`.

Tek satır sözdiziminde, bir... kararı sonucu olarak birden çok deyim yürütülebileceğini sağlayabilirsiniz `If` `Then` . Tüm deyimler aynı satırda olmalıdır ve iki nokta üst üste ile ayrılmalıdır.

## <a name="multiline-syntax-example"></a>Çok satırlı sözdizimi örneği

<a name="multi-line"></a>

Aşağıdaki örnek, `If` .. `Then` . öğesinin çok satırlı sözdiziminin kullanımını gösterir. ...`Else` Ekstre.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>İç içe geçmiş sözdizimi örneği

<a name="nested"></a>

Aşağıdaki örnek iç içe geçmiş `If` ... `Then` ...`Else` deyimler.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Tek satırlık sözdizimi örneği

<a name="single-line"></a>Aşağıdaki örnek, tek satırlık sözdiziminin kullanımını gösterir.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If... Sonra... #Else yönergeler](../directives/if-then-else-directives.md)
- [Select...Case Deyimi](select-case-statement.md)
- [İç İçe Geçmiş Denetim Yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Karar Yapıları](../../programming-guide/language-features/control-flow/decision-structures.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If İşleci](../operators/if-operator.md)

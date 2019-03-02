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
ms.openlocfilehash: aeffdc842730a1be8160cd8db8e4c2aa849e94cc
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201735"
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

## <a name="quick-links-to-example-code"></a>Örnek kod için hızlı bağlantılar

Bu makalede kullanımlarını gösteren birkaç örnek içeren `If`... `Then`... `Else` deyimi:

* [Çok satırlı sözdizimi örneği](#multi-line)
* [İç içe geçmiş sözdizimi örneği](#nested)
* [Tek satırlı sözdizimi örneği](#single-line)

## <a name="parts"></a>Bölümler  
 `condition`  
 Gerekli. Expression. Değerlendirilmelidir `True` veya `False`, ya da örtük olarak dönüştürülebilir bir veri türüne `Boolean`.  
  
 İfade ise bir [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değerlendiren değişkeni [hiçbir şey](../../../visual-basic/language-reference/nothing.md), ifade ise, koşulu kabul edilir `False` ve `Else` bloğu yürütülür.  
  
 `Then`  
 Tek satırlı sözdiziminde gerekli; çok satırlı sözdiziminde isteğe bağlı.  
  
 `statements`  
 İsteğe bağlı. Bir veya daha fazla deyimlerini aşağıdaki `If`... `Then` durumunda yürütülen `condition` değerlendiren `True`.  
  
 `elseifcondition`  
 Gerekli if `ElseIf` mevcuttur. Expression. Değerlendirilmelidir `True` veya `False`, ya da örtük olarak dönüştürülebilir bir veri türüne `Boolean`.  
  
 `elseifstatements`  
 İsteğe bağlı. Bir veya daha fazla deyimlerini aşağıdaki `ElseIf`... `Then` durumunda yürütülen `elseifcondition` değerlendiren `True`.  
  
 `elsestatements`  
 İsteğe bağlı. Hayır önceki durumunda yürütülen bir veya daha fazla deyimleri `condition` veya `elseifcondition` ifadeyi hesaplar için `True`.  
  
 `End If`  
 Çok satırlı sürümünü sonlandırır `If`... `Then`... `Else` blok.  
  
## <a name="remarks"></a>Açıklamalar  
  
### <a name="multiline-syntax"></a>Çok satırlı söz dizimi  
 Olduğunda bir `If`... `Then`... `Else` deyimi karşılaştı, `condition` test edilir. Varsa `condition` olduğu `True`, aşağıdaki deyimleri `Then` yürütülür. Varsa `condition` olduğu `False`, her `ElseIf` deyimi (varsa) değerlendirilir sırada. Olduğunda bir `True` `elseifcondition` hemen ilişkili aşağıdaki deyimleri bulunana `ElseIf` yürütülür. Hayır ise `elseifcondition` değerlendiren `True`, veya varsa hiçbir `ElseIf` ifadeleri, aşağıdaki deyimleri `Else` yürütülür. Deyimler yürütüldükten sonra `Then`, `ElseIf`, veya `Else`, yürütme devam eder, deyimi aşağıdaki `End If`.  
  
 `ElseIf` Ve `Else` yan tümceleri olan hem de isteğe bağlı. Kadar olabilir `ElseIf` istediğiniz şekilde yan tümceleri bir `If`... `Then`... `Else` deyimi, ancak Hayır `ElseIf` yan tümcesi, sonra görünebilir bir `Else` yan tümcesi. `If`... `Then`... `Else` ifadeleri iç içe geçirilemez diğer içinde.  
  
 Çok satırlı sözdiziminde `If` deyimi ilk satırda tek deyim olması gerekir. `ElseIf`, `Else`, Ve `End If` deyimleri yalnızca bir satır etiketi tarafından öncesinde. `If`... `Then`... `Else` blok sonlanmalı bir `End If` deyimi.  
  
> [!TIP]
>  [Seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md) birkaç olası değerleri içeren tek bir ifade değerlendirirken daha kullanışlı olabilir.  
  
### <a name="single-line-syntax"></a>Tek satırlı söz dizimi  
 True ise yürütmek için kod ile tek bir koşul için tek satır sözdizimini kullanabilirsiniz. Ancak, çok satırlı söz dizimi daha fazla yapısı ve esneklik sağlar ve daha kolay okumak, güncelleştirmek ve hata ayıklama.  
  
 Aşağıda `Then` anahtar sözcüğü bir deyim tek satırlı olup olmadığını belirlemek için incelenir `If`. Bir açıklama dışındaki herhangi bir şey sonra görünürse `Then` aynı satırda deyimi tek satır kabul edilir `If` deyimi. Varsa `Then` eksik, çok satırlı başlangıcını olmalıdır `If`... `Then`... `Else`.  
  
 Tek satırlı sözdiziminde sonucu olarak çalıştırılan birden çok deyime sahip bir `If`... `Then` karar. Tüm ifadeler aynı satırda olmalıdır ve virgüllerle ayrılmış.  

## <a name="multiline-syntax-example"></a>Çok satırlı sözdizimi örneği

<a name="multi-line"></a>
 
 Çok satırlı söz diziminin kullanılması aşağıdaki örnekte `If`... `Then`... `Else` deyimi.  
  
 [!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>İç içe geçmiş sözdizimi örneği

<a name="nested"></a>

 Aşağıdaki örnek içeren iç içe geçmiş `If`... `Then`... `Else` deyimleri.  
  
 [!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Tek satırlı sözdizimi örneği
  
<a name="single-line"></a> Aşağıdaki örnek, tek satırlı söz dizimi kullanımını gösterir.  
  
 [!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case Deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Karar Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If İşleci](../../../visual-basic/language-reference/operators/if-operator.md)

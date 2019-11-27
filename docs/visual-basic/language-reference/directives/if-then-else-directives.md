---
title: '#If...Then...#Else Yönergeleri'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 40e93b718241c9819e3c0fd84595e76eb0c86472
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343821"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else Yönergeleri

Seçili Visual Basic kodu bloklarını koşullu olarak derler.

## <a name="syntax"></a>Sözdizimi

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a>Bölümler

`expression`  
`#If` ve `#ElseIf` deyimleri için gereklidir, başka bir yerde. Yalnızca bir veya daha fazla koşullu derleyici sabiti, sabit değer ve işleçlerden oluşan, `True` veya `False`değerlendirilen herhangi bir ifade.

`statements`  
`#If` bildiri bloğu için gerekli, başka bir yerde. İlişkili ifade `True`olarak değerlendirilirse derlenen program satırları veya derleyici yönergeleri Visual Basic.

`#End If`  
`#If` bildiri bloğunu sonlandırır.

## <a name="remarks"></a>Açıklamalar

Yüzeyde, `#If...Then...#Else` yönergelerinin davranışı `If...Then...Else` deyimleriyle aynı şekilde görünür. Ancak, `#If...Then...#Else` yönergeleri derleyicinin derlendiğini değerlendirir, ancak `If...Then...Else` deyimleri çalışma zamanında koşulları değerlendirir.

Koşullu derleme genellikle farklı platformlar için aynı programı derlemek için kullanılır. Hata ayıklama kodunun yürütülebilir bir dosyada görünmesini engellemek için de kullanılır. Koşullu derleme sırasında dışlanan kod, son yürütülebilir dosyadan tamamen atlandığından, boyut veya performans üzerinde hiçbir etkisi olmaz.

Herhangi bir değerlendirmenin sonucuna bakılmaksızın, tüm ifadeler `Option Compare Binary`kullanılarak değerlendirilir. `Option Compare` deyimi `#If` ve `#ElseIf` deyimlerindeki ifadeleri etkilemez.

> [!NOTE]
> `#If`, `#Else`, `#ElseIf`ve `#End If` yönergelerinin tek satırlık formu yoktur. Diğer hiçbir kod, yönergelerden biriyle aynı satırda görünemez.

Koşullu derleme bloğunun içindeki deyimler, tamamlanmış Mantıksal deyimler olmalıdır. Örneğin, yalnızca bir işlevin özniteliklerini koşullu olarak derlenemez, ancak işlevi öznitelikleri ile birlikte koşullu olarak bildirebilirsiniz:

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a>Örnek

Bu örnek, belirli deyimlerin derlenip derlenmeyeceğini anlamak için `#If...Then...#Else` yapısını kullanır.

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>

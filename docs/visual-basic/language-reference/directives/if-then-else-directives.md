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
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410016"
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
`#If`Ve deyimleri için gerekli `#ElseIf` , başka bir yerde. Veya olarak değerlendirilen bir veya daha fazla koşullu derleyici sabiti, sabit değer ve işleçlerden oluşan herhangi bir ifade `True` `False` .

`statements`  
For deyimleri için gerekli `#If` , başka bir yerde. İlişkili ifade olarak değerlendirildiğinde derlenen program satırları veya derleyici yönergeleri Visual Basic `True` .

`#End If`  
`#If`Ekstre bloğunu sonlandırır.

## <a name="remarks"></a>Açıklamalar

Yüzeyde, `#If...Then...#Else` yönergelerin davranışı deyimlerle aynı şekilde görünür `If...Then...Else` . Ancak, `#If...Then...#Else` yönergeler derleyici tarafından derlendiğini değerlendirir, ancak `If...Then...Else` deyimler çalışma zamanında koşulları değerlendirir.

Koşullu derleme genellikle farklı platformlar için aynı programı derlemek için kullanılır. Hata ayıklama kodunun yürütülebilir bir dosyada görünmesini engellemek için de kullanılır. Koşullu derleme sırasında dışlanan kod, son yürütülebilir dosyadan tamamen atlandığından, boyut veya performans üzerinde hiçbir etkisi olmaz.

Herhangi bir değerlendirmenin sonucuna bakılmaksızın, tüm ifadeler kullanılarak değerlendirilir `Option Compare Binary` . `Option Compare`Deyimi `#If` ve `#ElseIf` deyimlerindeki ifadeleri etkilemez.

> [!NOTE]
> `#If`,, `#Else` `#ElseIf` Ve yönergelerinin tek satırlık formu yoktur `#End If` . Diğer hiçbir kod, yönergelerden biriyle aynı satırda görünemez.

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

Bu örnek, `#If...Then...#Else` belirli deyimlerin derlenip derlenmeyeceğini anlamak için yapısını kullanır.

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [#Const Yönergesi](const-directive.md)
- [If...Then...Else Deyimi](../statements/if-then-else-statement.md)
- [Koşullu Derleme](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>

---
title: '#If... Sonra... #Else yönergeleri (Visual Basic)'
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
ms.openlocfilehash: 697521276e2d5a8d0a4aaae38789a21b7aa87fcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940755"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else Yönergeleri
Seçili Visual Basic kodu bloklarını koşullu olarak derler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 `#If` Ve`#ElseIf` deyimleri için gerekli, başka bir yerde. `True` Veya`False`olarak değerlendirilen bir veya daha fazla koşullu derleyici sabiti, sabit değer ve işleçlerden oluşan herhangi bir ifade.  
  
 `statements`  
 For deyimleri `#If` için gerekli, başka bir yerde. İlişkili ifade olarak `True`değerlendirildiğinde derlenen program satırları veya derleyici yönergeleri Visual Basic.  
  
 `#End If`  
 `#If` Ekstre bloğunu sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Yüzeyde, `#If...Then...#Else` yönergelerin davranışı `If...Then...Else` deyimlerle aynı şekilde görünür. Ancak, `#If...Then...#Else` yönergeler derleyici tarafından derlendiğini değerlendirir, `If...Then...Else` ancak deyimler çalışma zamanında koşulları değerlendirir.  
  
 Koşullu derleme genellikle farklı platformlar için aynı programı derlemek için kullanılır. Hata ayıklama kodunun yürütülebilir bir dosyada görünmesini engellemek için de kullanılır. Koşullu derleme sırasında dışlanan kod, son yürütülebilir dosyadan tamamen atlandığından, boyut veya performans üzerinde hiçbir etkisi olmaz.  
  
 Herhangi bir değerlendirmenin sonucuna bakılmaksızın, tüm ifadeler kullanılarak `Option Compare Binary`değerlendirilir. `Option Compare` Deyimi `#If` ve deyimlerindekiifadelerietkilemez.`#ElseIf`  
  
> [!NOTE]
> `#If` ,`#Else`, Ve yönergelerinin`#End If` tek satırlık formu yoktur. `#ElseIf` Diğer hiçbir kod, yönergelerden biriyle aynı satırda görünemez. 

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

- [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>

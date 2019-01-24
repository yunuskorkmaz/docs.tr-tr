---
title: '#If... Then... #Else yönergeleri (Visual Basic)'
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
ms.openlocfilehash: 8930e0e5c6bf9bd713b5601c91e6d1a5cbfd7a51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568237"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else Yönergeleri
Seçili Visual Basic kod bloklarını koşullu biçimde derler.  
  
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
 Gerekli `#If` ve `#ElseIf` deyimleri, isteğe bağlı başka bir yerde. Bir veya daha fazla koşullu derleyici sabitleri, sabit değerleri ve değerlendiren işleçler, özel olarak oluşan herhangi bir ifade `True` veya `False`.  
  
 `statements`  
 Gerekli `#If` deyim bloğu isteğe bağlı başka bir yerde. Visual Basic program satırları veya ilişkili ifadenin değerlendirdiği, derlenmiş derleyici yönergeleri `True`.  
  
 `#End If`  
 Sonlandırır `#If` deyim bloğu.  
  
## <a name="remarks"></a>Açıklamalar  
 Yüzeysel olarak, davranışını `#If...Then...#Else` yönergeleri görünür aynı şekilde `If...Then...Else` deyimleri. Ancak, `#If...Then...#Else` yönergeleri değerlendirmek derleyici tarafından derlenmiş ise `If...Then...Else` deyimleri, çalışma zamanında koşulları değerlendirin.  
  
 Koşullu derleme, genellikle aynı programın farklı platformlar için derlemek için kullanılır. Önlemek için de kullanılan bir yürütülebilir dosya olarak görüntülenmesini kodda hata ayıklama. Boyutu veya performans üzerinde hiçbir etkisi olmaz şekilde koşullu derleme sırasında dışlanan kod tamamen son yürütülebilir dosyadan atlandı.  
  
 Tüm değerlendirme sonucunu bağımsız olarak kullanarak tüm ifadeler değerlendirilir `Option Compare Binary`. `Option Compare` Deyimi ifadelerinde etkilemez `#If` ve `#ElseIf` deyimleri.  
  
> [!NOTE]
>  Hiçbir tek satır biçiminde `#If`, `#Else`, `#ElseIf`, ve `#End If` yönergeler bulunmaktadır. Başka bir kod tüm yönergeleri ile aynı satırda görünebilir. 

Koşullu derleme bloğundaki ifadeleri tam mantıksal ifadeler olmalıdır. Örneğin, yalnızca bir işlev özniteliklerini koşullu olarak derlenemez, ancak işlev özniteliklerini birlikte koşullu olarak bildirebilirsiniz:

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
 Bu örnekte `#If...Then...#Else` belirli deyimleri derleme belirlemek için yapı.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>



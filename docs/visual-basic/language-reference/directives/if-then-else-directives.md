---
title: '#If... Then... #Else yönergeleri'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else Yönergeleri
Visual Basic kodu seçili bloklarını koşullu olarak derler.  
  
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
 İçin gerekli `#If` ve `#ElseIf` deyimleri, isteğe bağlı başka bir yerde. Özel olarak bir veya daha fazla koşullu derleyici sabitleri, değişmez değerleri ve değerlendiren işleçleri oluşan herhangi bir ifade `True` veya `False`.  
  
 `statements`  
 İçin gerekli `#If` deyimi engellemek, isteğe bağlı başka bir yerde. Visual Basic programı çizgi veya ilişkili ifade değerlendirilirse derlenen derleyici yönergeleri `True`.  
  
 `#End If`  
 Sonlandırır `#If` deyimi bloğu.  
  
## <a name="remarks"></a>Açıklamalar  
 Yüzeyinde davranışını `#If...Then...#Else` yönergeleri görünür aynı aynı `If...Then...Else` deyimleri. Ancak, `#If...Then...#Else` yönergeleri değerlendirmek derleyicisi tarafından derlenen ancak `If...Then...Else` deyimleri çalışma zamanında koşulları değerlendirin.  
  
 Koşullu derleme genellikle farklı platformlar için aynı programı derlemek için kullanılır. Önlemek için de kullanılan yürütülebilir bir dosya olarak görünmesini kodda hata ayıklama. Boyutu veya performans üzerinde hiçbir etkisi olmaz şekilde koşullu derleme sırasında dışlanan kod tamamen son yürütülebilir dosyasından atlandı.  
  
 Tüm değerlendirme sonucunu bağımsız olarak tüm ifadeler kullanarak değerlendirilir `Option Compare Binary`. `Option Compare` Deyimi ifadelerinde etkilemez `#If` ve `#ElseIf` deyimleri.  
  
> [!NOTE]
>  Hiçbir tek satırlı biçiminde `#If`, `#Else`, `#ElseIf`, ve `#End If` yönergeleri bulunmaktadır. Başka bir kod herhangi yönergesi olarak aynı satırda görünebilir. 

Koşullu derleme bloğundaki ifadeleri tam mantıksal deyimler olmalıdır. Örneğin, yalnızca bir işlev özniteliklerini koşullu derlenemiyor, ancak koşullu özniteliklerini birlikte işlevi bildirebilir:

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
 Bu örnekte `#If...Then...#Else` yapı belirli deyimleri derlenip derlenmeyeceğini belirler.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)  
[If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
[Koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   



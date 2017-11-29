---
title: "#<a name=\"ifthenelse-directives\"></a>If... Then... #Else yönergeleri"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77757e441ae937aa86122f237e839d1005644409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
## <a name="example"></a>Örnek  
 Bu örnekte `#If...Then...#Else` yapı belirli deyimleri derlenip derlenmeyeceğini belirler.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [#Const yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)  
 [If... Then... Else deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)

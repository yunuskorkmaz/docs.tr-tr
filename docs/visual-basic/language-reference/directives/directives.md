---
title: Yönergeler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="directives-visual-basic"></a>Yönergeler (Visual Basic)
Bu bölümdeki konular, Visual Basic kaynak kodu derleyici yönergeleri belge.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [#Const yönergesi](../../../visual-basic/language-reference/directives/const-directive.md) --derleyici sabiti tanımlayın  
  
 [#ExternalSource yönergesi](../../../visual-basic/language-reference/directives/externalsource-directive.md) --kaynak satırları ve metin kaynağına dış arasında bir eşleme belirtmek  
  
 [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --seçili kod bloklarını derleme  
  
 [#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md) --daraltma ve Visual Studio düzenleyicisinde kodun bölümlerini gizleme  
  
 **#Disable, #Enable** --devre dışı bırakın ve kod bölgeler için belirli uyarıları etkinleştirin.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Devre dışı bırakabilir ve uyarı kodlarının virgülle ayrılmış bir liste çok etkinleştirin.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Visual Basic Dil Başvurusu](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)

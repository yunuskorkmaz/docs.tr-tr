---
title: Yönergeler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409193"
---
# <a name="directives-visual-basic"></a>Yönergeler (Visual Basic)
Bu bölümdeki konular, Visual Basic kaynak kod derleyici yönergeleri belgeleyin.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [#Const yönergesi](../../../visual-basic/language-reference/directives/const-directive.md) --derleyici sabiti tanımlayın  
  
 [#ExternalSource yönergesi](../../../visual-basic/language-reference/directives/externalsource-directive.md) --kaynak satırlarını ve dış kaynak metin arasındaki eşlemeyi gösterir  
  
 [#If... Then... #Else yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --seçili kod bloklarını derleyin  
  
 [#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md) --Daralt ve Visual Studio düzenleyicisinde kod bölümlerini Gizle  
  
 **#Disable, #Enable** --devre dışı bırakın ve bölgeleri için belirli uyarıları etkinleştirin.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Devre dışı bırakabilir ve uyarı kodlarının virgülle ayrılmış bir listesi çok etkinleştirin.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)

---
title: "Yönergeler (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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

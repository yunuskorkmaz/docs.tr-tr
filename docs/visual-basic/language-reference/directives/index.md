---
title: Yönergeler
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: d76e10ad5ce8ad3accdc84f97146e0816048d8f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343800"
---
# <a name="directives-visual-basic"></a>Yönergeler (Visual Basic)

Bu bölümdeki konular Visual Basic kaynak kodu derleyici yönergelerini belgeleyin.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md) --derleyici sabiti tanımlama  
  
 [#ExternalSource yönergesi](../../../visual-basic/language-reference/directives/externalsource-directive.md) --kaynak satırları ile kaynağın harici metni arasında bir eşleme belirtin  
  
 [#If... Sonra... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --seçili kod bloklarını derle  
  
 [#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md) --Visual Studio düzenleyicisinde kodun bölümlerini daraltma ve gizleme  
  
 **#Disable, #Enable** --kod bölgeleri için belirli uyarıları devre dışı bırakın ve etkinleştirin.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Virgülle ayrılmış bir uyarı kodları listesini devre dışı bırakabilir ve etkinleştirebilirsiniz.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)

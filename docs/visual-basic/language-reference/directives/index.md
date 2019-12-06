---
title: Yönergeler
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5e857198351b30c0d7a38dce1a9e6d1209b5258
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838149"
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
  
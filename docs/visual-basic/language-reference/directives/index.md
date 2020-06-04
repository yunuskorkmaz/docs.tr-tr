---
title: Yönergeler
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5fcf3cb8801bc99dd2096c28cc41ebefeb34592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410003"
---
# <a name="directives-visual-basic"></a>Yönergeler (Visual Basic)

Bu bölümdeki konular Visual Basic kaynak kodu derleyici yönergelerini belgeleyin.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [#Const Yönergesi](const-directive.md) --derleyici sabiti tanımlama  
  
 [#ExternalSource yönergesi](externalsource-directive.md) --kaynak satırları ile kaynağın harici metni arasında bir eşleme belirtin  
  
 [#If... Sonra... #Else yönergeleri](if-then-else-directives.md) --seçili kod bloklarını derle  
  
 [#Region yönergesi](region-directive.md) --Visual Studio düzenleyicisinde kodun bölümlerini daraltma ve gizleme  
  
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

 [Visual Basic dil başvurusu](../index.md)  
  
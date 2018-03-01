---
title: "Varsayılan özellik erişimi devralınan arabirim üyeleri &#39;arasında belirsiz; &lt;defaultpropertyname&gt;&#39; arabirimi &#39;&lt; interfacename1&gt;&#39; ve &#39;&lt; defaultpropertyname&gt;&#39; arabirimi &#39;&lt; interfacename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23d613668ee2d92484117759dd614ed2cad4bcb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a>Varsayılan özellik erişimi devralınan arabirim üyeleri &#39;arasında belirsiz; &lt;defaultpropertyname&gt;&#39; arabirimi &#39;&lt; interfacename1&gt;&#39; ve &#39;&lt; defaultpropertyname&gt;&#39; arabirimi &#39;&lt; interfacename2&gt;&#39;
İki arabirim, her biri aynı ada sahip varsayılan bir özellik bildiren bir arabirim devralır. Derleyici niteliğe olmadan bu varsayılan özellik için bir erişim çözümlenemiyor. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 Belirttiğinizde `testObj(1)`, derleyici varsayılan özelliğine çözümlemeyi dener. Ancak, iki olası varsayılan özellikleri devralınan arabirimi vardır nedeniyle, bu hatayı Derleyici sinyalleri şekilde.  
  
 **Hata Kimliği:** BC30686  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Aynı ada sahip tüm üyeleri devralma kaçının. Önceki örnekte varsa `testObj` üyelerini gerekmez, söyleyin, `Iface2`, aşağıdaki gibi bildirin:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     veya  
  
-   Türetilen arabirimi bir sınıfta uygulayın. Daha sonra farklı adlara sahip devralınan özelliklerin her biri uygulayabilirsiniz. Ancak, yalnızca biri uygulayan sınıfa varsayılan özelliği olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

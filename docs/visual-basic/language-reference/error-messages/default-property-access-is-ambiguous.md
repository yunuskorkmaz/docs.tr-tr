---
title: Varsayılan özellik erişimi '<defaultpropertyname>' arabiriminin '<interfacename1>' devralınan üyesi ile '<defaultpropertyname>' arabiriminin '<interfacename2>' devralınan üyesi arasında belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 5f058c8e7d480b9145452ae85f186a6ac2ed0d56
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836356"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>Devralınan üyelerin arasında varsayılan özellik erişimi belirsiz\<defaultpropertyname >' arabiriminin '\<interfacename1 >' ve '\<defaultpropertyname >' arabiriminin '\< interfacename2 >'
Her biri aynı ada sahip varsayılan bir özelliği bildirir, iki arabirim bir arabirimi devralır. Derleyici, nitelik olmadan bu varsayılan özellik için bir erişim çözümlenemiyor. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Belirttiğinizde `testObj(1)`, derleyici varsayılan özelliğine çözümlemeye çalışır. Ancak, iki olası varsayılan özellik devralınan arabirimi vardır nedeniyle, derleyicinin bu hatayı sinyalleri için.  
  
 **Hata Kimliği:** BC30686  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Aynı ada sahip tüm üyeleri devralan kaçının. Yukarıdaki örnekte, `testObj` üyelerinin gerekmez, örneğin `Iface2`, şu şekilde bildirmek:  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     veya  
  
-   Bir sınıfta devralan arabirim uygular. Ardından, her biri farklı adlara sahip devralınan özellikler uygulayabilirsiniz. Ancak, yalnızca bir tanesi uygulayan sınıfın varsayılan özelliği olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

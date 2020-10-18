---
title: Varsayılan özellik erişimi '<defaultpropertyname>' arabiriminin '<interfacename1>' devralınan üyesi ile '<defaultpropertyname>' arabiriminin '<interfacename2>' devralınan üyesi arasında belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: b7c4c9c75de1b3777f34a70470b89f323a5699f9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162069"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>BC30686: ' ' arabiriminin ' ' \<defaultpropertyname> \<interfacename1> ve ' ' \<defaultpropertyname> \<interfacename2> arabiriminin devralınan ' ' arabirim üyeleri arasında varsayılan özellik erişimi belirsiz

Bir arabirim, her biri aynı ada sahip bir varsayılan özellik bildiren iki arabirimden devralınır. Derleyici, bu varsayılan özelliğe bir erişimi nitelemeden çözümleyemiyor. Aşağıdaki örnek bunu göstermektedir.

```vb
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

Belirttiğinizde `testObj(1)` , derleyici onu varsayılan özelliğe çözümlemeye çalışır. Ancak, devralınan arabirimler nedeniyle mümkün olan iki varsayılan özellik bulunur, bu nedenle derleyici bu hatayı bildirir.

**Hata kimliği:** BC30686

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Aynı ada sahip tüm üyeleri devrmaktan kaçının. Yukarıdaki örnekte, üyesi yoksa,,, ve `testObj` `Iface2` daha sonra bunu şöyle bildirin:

  ```vb
  Dim testObj As Iface1
  ```

  \-veya

- Devralan arabirimi bir sınıfta uygulayın. Ardından, devralınan özelliklerden her birini farklı adlarla uygulayabilirsiniz. Ancak, bunlardan yalnızca biri uygulama sınıfının varsayılan özelliği olabilir. Aşağıdaki örnek bunu göstermektedir.

  ```vb
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

- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)

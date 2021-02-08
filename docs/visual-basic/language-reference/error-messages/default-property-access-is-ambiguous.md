---
description: "Şu konuda daha fazla bilgi edinin: BC30686: varsayılan özellik erişimi ' ' arabiriminin ' ' devralınan ' ' arabirimi üyeleri <defaultpropertyname> <interfacename1> ve ' <defaultpropertyname> ' arabiriminin ' '<interfacename2>"
title: Varsayılan özellik erişimi '<defaultpropertyname>' arabiriminin '<interfacename1>' devralınan üyesi ile '<defaultpropertyname>' arabiriminin '<interfacename2>' devralınan üyesi arasında belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 5ae5e5b2dc7a61540e26d125e960d4755141d975
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796658"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="32bab-103">BC30686: ' ' arabiriminin ' ' \<defaultpropertyname> \<interfacename1> ve ' ' \<defaultpropertyname> \<interfacename2> arabiriminin devralınan ' ' arabirim üyeleri arasında varsayılan özellik erişimi belirsiz</span><span class="sxs-lookup"><span data-stu-id="32bab-103">BC30686: Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="32bab-104">Bir arabirim, her biri aynı ada sahip bir varsayılan özellik bildiren iki arabirimden devralınır.</span><span class="sxs-lookup"><span data-stu-id="32bab-104">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="32bab-105">Derleyici, bu varsayılan özelliğe bir erişimi nitelemeden çözümleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="32bab-105">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="32bab-106">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="32bab-106">The following example illustrates this.</span></span>

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

<span data-ttu-id="32bab-107">Belirttiğinizde `testObj(1)` , derleyici onu varsayılan özelliğe çözümlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="32bab-107">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="32bab-108">Ancak, devralınan arabirimler nedeniyle mümkün olan iki varsayılan özellik bulunur, bu nedenle derleyici bu hatayı bildirir.</span><span class="sxs-lookup"><span data-stu-id="32bab-108">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="32bab-109">**Hata kimliği:** BC30686</span><span class="sxs-lookup"><span data-stu-id="32bab-109">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="32bab-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="32bab-110">To correct this error</span></span>

- <span data-ttu-id="32bab-111">Aynı ada sahip tüm üyeleri devrmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="32bab-111">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="32bab-112">Yukarıdaki örnekte, üyesi yoksa,,, ve `testObj` `Iface2` daha sonra bunu şöyle bildirin:</span><span class="sxs-lookup"><span data-stu-id="32bab-112">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="32bab-113">\-veya</span><span class="sxs-lookup"><span data-stu-id="32bab-113">\-or-</span></span>

- <span data-ttu-id="32bab-114">Devralan arabirimi bir sınıfta uygulayın.</span><span class="sxs-lookup"><span data-stu-id="32bab-114">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="32bab-115">Ardından, devralınan özelliklerden her birini farklı adlarla uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32bab-115">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="32bab-116">Ancak, bunlardan yalnızca biri uygulama sınıfının varsayılan özelliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="32bab-116">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="32bab-117">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="32bab-117">The following example illustrates this.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="32bab-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32bab-118">See also</span></span>

- [<span data-ttu-id="32bab-119">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="32bab-119">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)

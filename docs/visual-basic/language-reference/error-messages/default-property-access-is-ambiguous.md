---
title: Varsayılan özellik erişimi '<defaultpropertyname>' arabiriminin '<interfacename1>' devralınan üyesi ile '<defaultpropertyname>' arabiriminin '<interfacename2>' devralınan üyesi arasında belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: f76163d58f3f11d3ca946525a1604abc3ebba68d
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250378"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="17ee6-102">' @No__t-3ınterfacename2 > ' arabiriminin ' \<ınterfacename1 > ' ve ' \<defaultpropertyname > ' arabiriminin devralınan ' \<defaultpropertyname > ' arabirim üyeleri arasında varsayılan özellik erişimi belirsiz</span><span class="sxs-lookup"><span data-stu-id="17ee6-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="17ee6-103">Bir arabirim, her biri aynı ada sahip bir varsayılan özellik bildiren iki arabirimden devralınır.</span><span class="sxs-lookup"><span data-stu-id="17ee6-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="17ee6-104">Derleyici, bu varsayılan özelliğe bir erişimi nitelemeden çözümleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="17ee6-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="17ee6-105">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="17ee6-105">The following example illustrates this.</span></span>

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

<span data-ttu-id="17ee6-106">@No__t-0 belirttiğinizde, derleyici onu varsayılan özelliğe çözümlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="17ee6-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="17ee6-107">Ancak, devralınan arabirimler nedeniyle mümkün olan iki varsayılan özellik bulunur, bu nedenle derleyici bu hatayı bildirir.</span><span class="sxs-lookup"><span data-stu-id="17ee6-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="17ee6-108">**Hata kimliği:** BC30686</span><span class="sxs-lookup"><span data-stu-id="17ee6-108">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="17ee6-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="17ee6-109">To correct this error</span></span>

- <span data-ttu-id="17ee6-110">Aynı ada sahip tüm üyeleri devrmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="17ee6-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="17ee6-111">Yukarıdaki örnekte, `testObj` ' ın üyesi yoksa, `Iface2` ' i yoksa, aşağıdaki gibi bildirin:</span><span class="sxs-lookup"><span data-stu-id="17ee6-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="17ee6-112">\-veya-</span><span class="sxs-lookup"><span data-stu-id="17ee6-112">\-or-</span></span>

- <span data-ttu-id="17ee6-113">Devralan arabirimi bir sınıfta uygulayın.</span><span class="sxs-lookup"><span data-stu-id="17ee6-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="17ee6-114">Ardından, devralınan özelliklerden her birini farklı adlarla uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17ee6-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="17ee6-115">Ancak, bunlardan yalnızca biri uygulama sınıfının varsayılan özelliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="17ee6-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="17ee6-116">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="17ee6-116">The following example illustrates this.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="17ee6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17ee6-117">See also</span></span>

- [<span data-ttu-id="17ee6-118">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="17ee6-118">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)

---
title: Varsayılan özellik erişimi '<defaultpropertyname>' arabiriminin '<interfacename1>' devralınan üyesi ile '<defaultpropertyname>' arabiriminin '<interfacename2>' devralınan üyesi arasında belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: a7079ff3b56b94cb969a77707dbd79b1d7dd4bb1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270595"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="b943a-102">Devralınan üyelerin arasında varsayılan özellik erişimi belirsiz\<defaultpropertyname >' arabiriminin '\<interfacename1 >' ve '\<defaultpropertyname >' arabiriminin '\< interfacename2 >'</span><span class="sxs-lookup"><span data-stu-id="b943a-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>
<span data-ttu-id="b943a-103">Her biri aynı ada sahip varsayılan bir özelliği bildirir, iki arabirim bir arabirimi devralır.</span><span class="sxs-lookup"><span data-stu-id="b943a-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="b943a-104">Derleyici, nitelik olmadan bu varsayılan özellik için bir erişim çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="b943a-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="b943a-105">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b943a-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="b943a-106">Belirttiğinizde `testObj(1)`, derleyici varsayılan özelliğine çözümlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="b943a-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="b943a-107">Ancak, iki olası varsayılan özellik devralınan arabirimi vardır nedeniyle, derleyicinin bu hatayı sinyalleri için.</span><span class="sxs-lookup"><span data-stu-id="b943a-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="b943a-108">**Hata Kimliği:** BC30686</span><span class="sxs-lookup"><span data-stu-id="b943a-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b943a-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b943a-109">To correct this error</span></span>  
  
-   <span data-ttu-id="b943a-110">Aynı ada sahip tüm üyeleri devralan kaçının.</span><span class="sxs-lookup"><span data-stu-id="b943a-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="b943a-111">Yukarıdaki örnekte, `testObj` üyelerinin gerekmez, örneğin `Iface2`, şu şekilde bildirmek:</span><span class="sxs-lookup"><span data-stu-id="b943a-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="b943a-112">-veya-</span><span class="sxs-lookup"><span data-stu-id="b943a-112">-or-</span></span>  
  
-   <span data-ttu-id="b943a-113">Bir sınıfta devralan arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="b943a-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="b943a-114">Ardından, her biri farklı adlara sahip devralınan özellikler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b943a-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="b943a-115">Ancak, yalnızca bir tanesi uygulayan sınıfın varsayılan özelliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="b943a-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="b943a-116">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b943a-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b943a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b943a-117">See also</span></span>
- [<span data-ttu-id="b943a-118">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b943a-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

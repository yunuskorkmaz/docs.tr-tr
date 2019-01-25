---
title: Devralınan üyesi arasında varsayılan özellik erişimi belirsiz &#39; &lt;defaultpropertyname&gt; &#39; arabiriminin &#39; &lt;interfacename1&gt; &#39; ve &#39; &lt;defaultpropertyname&gt; &#39; arabiriminin &#39; &lt;interfacename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 1fae63506a35eb046676214a2b6c52977f24645d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518650"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a><span data-ttu-id="b294b-102">Devralınan üyesi arasında varsayılan özellik erişimi belirsiz &#39; &lt;defaultpropertyname&gt; &#39; arabiriminin &#39; &lt;interfacename1&gt; &#39; ve &#39; &lt;defaultpropertyname&gt; &#39; arabiriminin &#39; &lt;interfacename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="b294b-102">Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="b294b-103">Her biri aynı ada sahip varsayılan bir özelliği bildirir, iki arabirim bir arabirimi devralır.</span><span class="sxs-lookup"><span data-stu-id="b294b-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="b294b-104">Derleyici, nitelik olmadan bu varsayılan özellik için bir erişim çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="b294b-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="b294b-105">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b294b-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="b294b-106">Belirttiğinizde `testObj(1)`, derleyici varsayılan özelliğine çözümlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="b294b-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="b294b-107">Ancak, iki olası varsayılan özellik devralınan arabirimi vardır nedeniyle, derleyicinin bu hatayı sinyalleri için.</span><span class="sxs-lookup"><span data-stu-id="b294b-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="b294b-108">**Hata Kimliği:** BC30686</span><span class="sxs-lookup"><span data-stu-id="b294b-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b294b-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b294b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="b294b-110">Aynı ada sahip tüm üyeleri devralan kaçının.</span><span class="sxs-lookup"><span data-stu-id="b294b-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="b294b-111">Yukarıdaki örnekte, `testObj` üyelerinin gerekmez, örneğin `Iface2`, şu şekilde bildirmek:</span><span class="sxs-lookup"><span data-stu-id="b294b-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="b294b-112">-veya-</span><span class="sxs-lookup"><span data-stu-id="b294b-112">-or-</span></span>  
  
-   <span data-ttu-id="b294b-113">Bir sınıfta devralan arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="b294b-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="b294b-114">Ardından, her biri farklı adlara sahip devralınan özellikler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b294b-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="b294b-115">Ancak, yalnızca bir tanesi uygulayan sınıfın varsayılan özelliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="b294b-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="b294b-116">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b294b-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b294b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b294b-117">See also</span></span>
- [<span data-ttu-id="b294b-118">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b294b-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

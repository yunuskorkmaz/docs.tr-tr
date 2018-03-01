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
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a><span data-ttu-id="e0f82-102">Varsayılan özellik erişimi devralınan arabirim üyeleri &#39;arasında belirsiz; &lt;defaultpropertyname&gt;&#39; arabirimi &#39;&lt; interfacename1&gt;&#39; ve &#39;&lt; defaultpropertyname&gt;&#39; arabirimi &#39;&lt; interfacename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="e0f82-102">Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="e0f82-103">İki arabirim, her biri aynı ada sahip varsayılan bir özellik bildiren bir arabirim devralır.</span><span class="sxs-lookup"><span data-stu-id="e0f82-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="e0f82-104">Derleyici niteliğe olmadan bu varsayılan özellik için bir erişim çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="e0f82-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="e0f82-105">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e0f82-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="e0f82-106">Belirttiğinizde `testObj(1)`, derleyici varsayılan özelliğine çözümlemeyi dener.</span><span class="sxs-lookup"><span data-stu-id="e0f82-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="e0f82-107">Ancak, iki olası varsayılan özellikleri devralınan arabirimi vardır nedeniyle, bu hatayı Derleyici sinyalleri şekilde.</span><span class="sxs-lookup"><span data-stu-id="e0f82-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="e0f82-108">**Hata Kimliği:** BC30686</span><span class="sxs-lookup"><span data-stu-id="e0f82-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0f82-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e0f82-109">To correct this error</span></span>  
  
-   <span data-ttu-id="e0f82-110">Aynı ada sahip tüm üyeleri devralma kaçının.</span><span class="sxs-lookup"><span data-stu-id="e0f82-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="e0f82-111">Önceki örnekte varsa `testObj` üyelerini gerekmez, söyleyin, `Iface2`, aşağıdaki gibi bildirin:</span><span class="sxs-lookup"><span data-stu-id="e0f82-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="e0f82-112">veya</span><span class="sxs-lookup"><span data-stu-id="e0f82-112">-or-</span></span>  
  
-   <span data-ttu-id="e0f82-113">Türetilen arabirimi bir sınıfta uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e0f82-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="e0f82-114">Daha sonra farklı adlara sahip devralınan özelliklerin her biri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0f82-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="e0f82-115">Ancak, yalnızca biri uygulayan sınıfa varsayılan özelliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0f82-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="e0f82-116">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e0f82-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0f82-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0f82-117">See Also</span></span>  
 [<span data-ttu-id="e0f82-118">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0f82-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

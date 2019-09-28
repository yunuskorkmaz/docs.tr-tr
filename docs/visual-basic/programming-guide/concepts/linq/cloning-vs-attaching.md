---
title: Kopyalama ve İliştirme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 2849c648d8d280200d742663cbc7188b344d8306
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352971"
---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="d715e-102">Kopyalama ve İliştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d715e-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="d715e-103">@No__t-0 (<xref:System.Xml.Linq.XElement> dahil) veya <xref:System.Xml.Linq.XAttribute> nesneleri yeni bir ağaca eklerken, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="d715e-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="d715e-104">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="d715e-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="d715e-105">Yeni kopyalanan içerik daha sonra XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="d715e-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d715e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d715e-106">Example</span></span>  
 <span data-ttu-id="d715e-107">Aşağıdaki kod, bir ağaca bir üst öğeye sahip bir öğe eklediğinizde ve bir ağaca üst öğesi olmayan bir öğe eklediğinizde davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d715e-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="d715e-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d715e-108">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="d715e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d715e-109">See also</span></span>

- [<span data-ttu-id="d715e-110">XML ağaçları oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d715e-110">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

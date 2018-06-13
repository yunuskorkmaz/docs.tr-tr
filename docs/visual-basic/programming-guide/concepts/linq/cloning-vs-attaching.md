---
title: Kopyalama vs. Düğmelere (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 35a265d2aaef40977a9a6b89d174e9a585c525c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640312"
---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="e7334-102">Kopyalama vs. Düğmelere (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7334-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="e7334-103">Eklerken <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneleri için yeni bir ağaç, yeni içeriğe üst öğeye sahipse, nesneleri basitçe bağlı XML ağacına.</span><span class="sxs-lookup"><span data-stu-id="e7334-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="e7334-104">Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="e7334-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="e7334-105">Yeni kopyalanmış içerik ardından XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="e7334-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7334-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7334-106">Example</span></span>  
 <span data-ttu-id="e7334-107">Aşağıdaki kod bir ağacına üst öğeye sahip bir öğe eklediğinizde ve ağaca üst öğeye bir öğe eklediğinizde davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7334-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
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
  
 <span data-ttu-id="e7334-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="e7334-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7334-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7334-109">See Also</span></span>  
 [<span data-ttu-id="e7334-110">Oluşturma XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7334-110">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

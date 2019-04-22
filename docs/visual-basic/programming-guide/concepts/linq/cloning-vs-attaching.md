---
title: Kopyalama ve Düğmelere (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 59ffedfdbb2820683f1e6cc232154688f5c29fc8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832300"
---
# <a name="cloning-vs-attaching-visual-basic"></a>Kopyalama ve Düğmelere (Visual Basic)
Eklerken <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> yeni içerik üstü yoksa, nesneleri yalnızca bağlı XML ağacına yeni bir ağaç nesneleri. Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalanmış olan. Yeni kopyalanan içeriği sonra XML ağacına eklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir ağaca üst öğeye sahip bir öğe eklediğinizde ve bir ağaca hiçbir üst öğesi ile bir öğe eklediğinizde davranış gösterir.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

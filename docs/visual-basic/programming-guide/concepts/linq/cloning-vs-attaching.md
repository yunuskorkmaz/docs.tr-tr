---
title: Kopyalama ve Ekleme Karşılaştırması
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 1974e10579e87f17746d5a9ba8a86ea8d819d9ea
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555763"
---
# <a name="cloning-vs-attaching-visual-basic"></a>Kopyalama ile ekleme (Visual Basic)
Yeni <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XElement> bir ağaca (dahil) veya <xref:System.Xml.Linq.XAttribute> nesneleri eklerken, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir. Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır. Yeni kopyalanan içerik daha sonra XML ağacına eklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir ağaca bir üst öğeye sahip bir öğe eklediğinizde ve bir ağaca üst öğesi olmayan bir öğe eklediğinizde davranışını gösterir.  
  
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
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları oluşturma (Visual Basic)](../../../../standard/linq/xml-literals.md)

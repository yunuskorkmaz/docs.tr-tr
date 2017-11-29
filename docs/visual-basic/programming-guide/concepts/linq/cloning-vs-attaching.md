---
title: "Kopyalama vs. Düğmelere (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 811e0b9d6359287d779a8352482f5dc56a3b0035
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cloning-vs-attaching-visual-basic"></a>Kopyalama vs. Düğmelere (Visual Basic)
Eklerken <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneleri için yeni bir ağaç, yeni içeriğe üst öğeye sahipse, nesneleri basitçe bağlı XML ağacına. Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalandı. Yeni kopyalanmış içerik ardından XML ağacına eklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir ağacına üst öğeye sahip bir öğe eklediğinizde ve ağaca üst öğeye bir öğe eklediğinizde davranış gösterir.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

---
title: Bir özniteliğin değerini alma (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347429"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Bir özniteliğin değerini alma (LINQ to XML) (C#)
Bu konu, özniteliklerin değerinin nasıl alınacağını gösterir. İki ana yol vardır: <xref:System.Xml.Linq.XAttribute> istenen türe çevirebilirsiniz; Açık dönüştürme işleci daha sonra öğe veya özniteliğin içeriğini belirtilen türe dönüştürür. Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini de kullanabilirsiniz. Ancak, atama genellikle daha iyi bir yaklaşımdır. Özniteliğini null yapılabilir bir türe çevirebilirsiniz, bu, var olabilen veya varolmayan bir özniteliğin değeri alınırken yazmak daha basittir. Bu tekniğin örnekleri için bkz. [bir öğenin değerini alma (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Örnek  
 Bir özniteliğin değerini almak için <xref:System.Xml.Linq.XAttribute> nesnesini istediğiniz türe atamalısınız.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özniteliğinin bir ad alanında olduğu bir özniteliğin değerinin nasıl alınacağını gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)

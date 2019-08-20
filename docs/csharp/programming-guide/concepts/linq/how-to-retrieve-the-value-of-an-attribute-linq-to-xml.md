---
title: 'Nasıl yapılır: Bir özniteliğin değerini alma (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 54ea4b532669ed2c615fcde02011fdd1228705a3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592475"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Nasıl yapılır: Bir özniteliğin değerini alma (LINQ to XML) (C#)
Bu konu, özniteliklerin değerinin nasıl alınacağını gösterir. İki ana yol vardır: İstediğiniz türe çevirebilirsiniz <xref:System.Xml.Linq.XAttribute> ; açık dönüştürme işleci daha sonra öğenin veya özniteliğin içeriğini belirtilen türe dönüştürür. Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini de kullanabilirsiniz. Ancak, atama genellikle daha iyi bir yaklaşımdır. Özniteliğini null yapılabilir bir türe çevirebilirsiniz, bu, var olabilen veya varolmayan bir özniteliğin değeri alınırken yazmak daha basittir. Bu tekniğin örnekleri için bkz [. nasıl yapılır: Bir öğenin değerini Al (LINQ to XML) (C#).](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)  
  
## <a name="example"></a>Örnek  
 Bir özniteliğin değerini almak için, <xref:System.Xml.Linq.XAttribute> nesneyi istediğiniz türe atamalısınız.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
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
  
```  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)

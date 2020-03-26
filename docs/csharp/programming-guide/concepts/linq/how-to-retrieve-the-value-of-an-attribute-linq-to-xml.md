---
title: Bir öznitelik (LINQ xml) (C#) değerini almak için nasıl
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 212ad3bb3097e7e2c76da8f165011b181f329d4c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249200"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Bir öznitelik (LINQ xml) (C#) değerini almak için nasıl
Bu konu, özniteliklerin değerini nasıl elde edilebildiğini gösterir. İki ana yolu vardır: İstediğiniz türe bir <xref:System.Xml.Linq.XAttribute> döküm yapabilirsiniz; açık dönüştürme işleci daha sonra öğenin içeriğini veya belirtilen türe atnitelik dönüştürür. Alternatif olarak, <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği kullanabilirsiniz. Ancak, döküm genellikle daha iyi bir yaklaşımdır. Özniteliği boşkullanılabilir bir değer türüne atarsanız, var olabilir veya olmayabilir bir öznitelik değerini alırken kod yazmak daha kolaydır. Bu teknik örnekleri için, [bir öğenin (LINQ- XML) (C#) değerini nasıl alabildiğini](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)görün.  
  
## <a name="example"></a>Örnek  
 Bir özniteliğin değerini almak için nesneyi <xref:System.Xml.Linq.XAttribute> istediğiniz türe atmanız önerilir.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özniteliğin ad alanında olduğu bir özniteliğin değerini nasıl alınacağını gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
abcde  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](./linq-to-xml-axes-overview.md)

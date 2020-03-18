---
title: XML Bildirimi (C#) ile serileştirme
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4533d69f2b0bee68b4adee6e18fe28dde18078ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483476"
---
# <a name="serializing-with-an-xml-declaration-c"></a>XML Bildirimi (C#) ile serileştirme
Bu konu, serileştirmenin bir XML bildirimi oluşturup oluşturmadığını nasıl denetleyiş olarak açıklar.  
  
## <a name="xml-declaration-generation"></a>XML Beyanname Oluşturma  
 Bir veya <xref:System.IO.File> yöntem <xref:System.IO.TextWriter> veya <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntem kullanarak serileştirme bir XML bildirimi oluşturur. Bir <xref:System.Xml.XmlWriter>, yazar ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnede belirtilen) bir XML bildirimi oluşturulur olup olmadığını belirlemek için serileştirdiğinizde.  
  
 `ToString` Yöntemi kullanarak bir dize serihale ediyorsanız, ortaya çıkan XML bir XML bildirimi içermez.  
  
### <a name="serializing-with-an-xml-declaration"></a>XML Bildirimi ile Serileştirme  
 Aşağıdaki örnek, <xref:System.Xml.Linq.XElement>belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>XML Bildirimi olmadan serileştirme  
 Aşağıdaki örnekte, bir <xref:System.Xml.Linq.XElement> 'den <xref:System.Xml.XmlWriter>bir'e nasıl kaydılsüreceğini gösterir  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Ağaçlarını Serihale Getirme (C#)](serializing-to-files-textwriters-and-xmlwriters.md)

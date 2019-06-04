---
title: (C#) bir XML bildirimi ile serileştirme
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4533d69f2b0bee68b4adee6e18fe28dde18078ae
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483476"
---
# <a name="serializing-with-an-xml-declaration-c"></a>(C#) bir XML bildirimi ile serileştirme
Bu konuda, serileştirme bir XML bildirimi oluşturup oluşturmayacağını denetlemek nasıl açıklanmaktadır.  
  
## <a name="xml-declaration-generation"></a>XML bildirimi oluşturma  
 Seri hale getirme için bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> kullanarak <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntem bir XML bildirimi oluşturur. Ne zaman serileştirmek için bir <xref:System.Xml.XmlWriter>, yazıcı ayarları (belirtilen bir <xref:System.Xml.XmlWriterSettings> nesne) veya bir XML bildirimi oluşturulup oluşturulmayacağını belirler.  
  
 Kullanarak bir dize cricheditdoc::m_brtf `ToString` elde edilen XML yöntemi, bir XML bildirimi içermez.  
  
### <a name="serializing-with-an-xml-declaration"></a>XML Bildirimi ile Serileştirme  
 Aşağıdaki örnek, oluşturur bir <xref:System.Xml.Linq.XElement>, belgeyi bir dosyaya kaydeder ve sonra dosyanın konsola yazdırır:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Bir XML bildirimi seri hale getirme  
 Aşağıdaki örnek nasıl kaydedileceğini gösterir bir <xref:System.Xml.Linq.XElement> için bir <xref:System.Xml.XmlWriter>.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirmek XML ağaçları (C#)](serializing-to-files-textwriters-and-xmlwriters.md)

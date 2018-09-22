---
title: (C#) bir XML bildirimi ile serileştirme
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 613280efc8c734c53c4af9252b4b83e2dd942f36
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46586311"
---
# <a name="serializing-with-an-xml-declaration-c"></a>(C#) bir XML bildirimi ile serileştirme
Bu konuda, serileştirme bir XML bildirimi oluşturup oluşturmayacağını denetlemek nasıl açıklanmaktadır.  
  
## <a name="xml-declaration-generation"></a>XML bildirimi oluşturma  
 Seri hale getirme için bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> kullanarak <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntem bir XML bildirimi oluşturur. Ne zaman serileştirmek için bir <xref:System.Xml.XmlWriter>, yazıcı ayarları (belirtilen bir <xref:System.Xml.XmlWriterSettings> nesne) veya bir XML bildirimi oluşturulup oluşturulmayacağını belirler.  
  
 Kullanarak bir dize cricheditdoc::m_brtf `ToString` elde edilen XML yöntemi, bir XML bildirimi içermez.  
  
### <a name="serializing-with-an-xml-declaration"></a>Bir XML bildirimi ile serileştirme  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Serileştirmek XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

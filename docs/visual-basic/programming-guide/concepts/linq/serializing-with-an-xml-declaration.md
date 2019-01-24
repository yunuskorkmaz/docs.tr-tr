---
title: Serileştirmek bir XML bildirimi (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: d0d6ccfdffa76de61c36e4cdb3f68f7cf85f1e68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558481"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>Serileştirmek bir XML bildirimi (Visual Basic)
Bu konuda, serileştirme bir XML bildirimi oluşturup oluşturmayacağını denetlemek nasıl açıklanmaktadır.  
  
## <a name="xml-declaration-generation"></a>XML bildirimi oluşturma  
 Seri hale getirme için bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> kullanarak <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntem bir XML bildirimi oluşturur. Ne zaman serileştirmek için bir <xref:System.Xml.XmlWriter>, yazıcı ayarları (belirtilen bir <xref:System.Xml.XmlWriterSettings> nesne) veya bir XML bildirimi oluşturulup oluşturulmayacağını belirler.  
  
 Kullanarak bir dize cricheditdoc::m_brtf `ToString` elde edilen XML yöntemi, bir XML bildirimi içermez.  
  
### <a name="serializing-with-an-xml-declaration"></a>Bir XML bildirimi ile serileştirme  
 Aşağıdaki örnek, oluşturur bir <xref:System.Xml.Linq.XElement>, belgeyi bir dosyaya kaydeder ve sonra dosyanın konsola yazdırır:  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
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
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [(Visual Basic) XML ağaçlarını serileştirme](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)

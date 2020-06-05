---
title: XML Bildirimi ile Serileştirme
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: cd303a800efe42d3fa99d601f25d54320570bed3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411811"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>XML bildirimiyle serileştirme (Visual Basic)
Bu konu, serileştirme 'in bir XML bildirimi oluşturup oluşturmayacağını nasıl denetleneceğini açıklar.  
  
## <a name="xml-declaration-generation"></a>XML bildirimi oluşturma  
 <xref:System.IO.File>Yöntemini veya yöntemini kullanarak bir veya öğesine serileştirmek BIR <xref:System.IO.TextWriter> <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> XML bildirimi oluşturur. ' A serileştirçalıştığınızda <xref:System.Xml.XmlWriter> , yazıcı ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnede belirtilir) bir XML bildiriminin oluşturulup oluşturulmayacağını belirtir.  
  
 Yöntemini kullanarak bir dizeye serileştirme yapıyorsanız `ToString` , elde EDILEN XML BIR XML bildirimi içermez.  
  
### <a name="serializing-with-an-xml-declaration"></a>XML Bildirimi ile Serileştirme  
 Aşağıdaki örnek bir dosyası oluşturur <xref:System.Xml.Linq.XElement> , belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:  
  
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
  
### <a name="serializing-without-an-xml-declaration"></a>XML bildirimi olmadan serileştirme  
 Aşağıdaki örnekte, bir ' a nasıl kaydedileceği gösterilmektedir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlWriter> .  
  
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

- [XML ağaçlarını serileştirme (Visual Basic)](serializing-xml-trees.md)

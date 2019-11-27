---
title: XML Bildirimi ile Serileştirme
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 96c95b4c94290016684721a194ca31a836a49740
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350627"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>XML bildirimiyle serileştirme (Visual Basic)
Bu konu, serileştirme 'in bir XML bildirimi oluşturup oluşturmayacağını nasıl denetleneceğini açıklar.  
  
## <a name="xml-declaration-generation"></a>XML bildirimi oluşturma  
 <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntemi kullanılarak bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> serileştirilmesi bir XML bildirimi oluşturur. Bir <xref:System.Xml.XmlWriter>seri hale getirmek istediğinizde, yazıcı ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnesinde belirtilen) bir XML bildiriminin oluşturulup oluşturulmayacağını belirtir.  
  
 `ToString` yöntemini kullanarak bir dizeye serileştirilirsiniz, sonuçta elde edilen XML bir XML bildirimi içermez.  
  
### <a name="serializing-with-an-xml-declaration"></a>XML Bildirimi ile Serileştirme  
 Aşağıdaki örnek bir <xref:System.Xml.Linq.XElement>oluşturur, belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:  
  
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
 Aşağıdaki örnekte, bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlWriter>nasıl kaydedileceği gösterilmektedir.  
  
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

- [XML ağaçlarını serileştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)

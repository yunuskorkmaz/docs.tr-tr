---
title: Bir XML bildirimi (Visual Basic) ile seri hale getirme
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 6b7351d85dab997ba6cb0ef023972e9e4e4fca14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>Bir XML bildirimi (Visual Basic) ile seri hale getirme
Bu konu, serileştirme bir XML bildirimi oluşturup oluşturmayacağını denetlemek açıklar.  
  
## <a name="xml-declaration-generation"></a>XML bildirimi oluşturma  
 İçin seri hale getirilirken bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> kullanarak <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntemi bir XML bildirimi oluşturur. Ne zaman serileştirmek için bir <xref:System.Xml.XmlWriter>, yazıcı ayarları (içinde belirtilen bir <xref:System.Xml.XmlWriterSettings> nesnesi) veya bir XML bildirimi oluşturulup oluşturulmayacağını belirler.  
  
 Kullanarak bir dize serileştirme, `ToString` yöntemi, sonuç XML olmayan bir XML bildirimi içerir.  
  
### <a name="serializing-with-an-xml-declaration"></a>Bir XML bildirimi ile seri hale getirme  
 Aşağıdaki örnekte bir <xref:System.Xml.Linq.XElement>, belgeyi bir dosyaya kaydeder ve dosyanın konsola yazdırır:  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Bir XML bildirimi seri hale getirme  
 Aşağıdaki örnekte nasıl kaydedileceğini gösteren bir <xref:System.Xml.Linq.XElement> için bir <xref:System.Xml.XmlWriter>.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendiricisi XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)

---
title: (Çağrılıyor XSLT) XmlReader'a serileştirme (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: b1f5bc8bd71036636df9da152c4e364ea5ec6b6e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649874"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>(Çağrılıyor XSLT) XmlReader'a serileştirme (C#)
Kullanırken <xref:System.Xml?displayProperty=nameWithType> birlikte çalışabilirlik özelliklerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], kullanabileceğiniz <xref:System.Xml.Linq.XNode.CreateReader%2A> oluşturmak için bir <xref:System.Xml.XmlReader>. Buradan okur Modülü <xref:System.Xml.XmlReader> XML ağacından düğümleri okur ve bunları uygun şekilde işler.  
  
## <a name="invoking-an-xslt-transformation"></a>XSLT dönüşümü çağırma  
 Bu yöntem bir olası kullanım XSLT dönüştürmesi çağrılırken içindir. Bir XML ağacı oluşturma, oluşturun bir <xref:System.Xml.XmlReader> XML ağacından bir yeni belge oluşturun ve ardından oluşturmak bir <xref:System.Xml.XmlWriter> yeni belgesine yazılacak. Öğesinde geçen XSLT dönüşümü, daha sonra çağırabilirsiniz <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>. Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşümü sonuçları ile doldurulur.  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Serileştirmek XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

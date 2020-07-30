---
title: XmlReader 'a serileştirme (XSLT çağırma) (C#)
description: C# ' de CreateReader kullanarak bir XmlReader oluşturma hakkında bilgi edinin. Bu XmlReader 'dan okuyan modül, düğümleri XML ağacından okur ve bunları işler.
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: aa5a232c74c5314cb7f1cf03c2a8875ca1cd04df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302418"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>XmlReader 'a serileştirme (XSLT çağırma) (C#)
<xref:System.Xml?displayProperty=nameWithType>Uygulamasının birlikte çalışabilirlik yeteneklerini kullandığınızda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , <xref:System.Xml.Linq.XNode.CreateReader%2A> oluşturmak için kullanabilirsiniz <xref:System.Xml.XmlReader> . Bu öğesinden okuyan modül, <xref:System.Xml.XmlReader> DÜĞÜMLERI XML ağacından okur ve bunlara göre işler.  
  
## <a name="invoking-an-xslt-transformation"></a>XSLT dönüşümünü çağırma  
 Bu yöntem için olası bir kullanım XSLT dönüşümünü çağırmada olur. Bir XML ağacı oluşturabilir, XML ağacından oluşturabilir, <xref:System.Xml.XmlReader> Yeni bir belge oluşturabilir ve sonra <xref:System.Xml.XmlWriter> yeni belgeye yazmak için oluşturabilirsiniz. Ardından, ve ile geçirerek XSLT dönüşümünü çağırabilirsiniz <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> . Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını serileştirme (C#)](serializing-to-files-textwriters-and-xmlwriters.md)

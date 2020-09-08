---
title: XmlReader 'a serileştirme (XSLT 'yi çağır)-LINQ to XML
description: XSLT dönüşümüne bir XML ağacının düğümlerini sağlayan bir XmlReader oluşturmak için CreateReader kullanabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: e079627b5fe114438feabaa1a49f42a65afedf43
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553064"
---
# <a name="serialize-to-an-xmlreader-invoke-xslt-linq-to-xml"></a>XmlReader 'a serileştirme (XSLT 'yi çağır) (LINQ to XML)

<xref:System.Xml?displayProperty=nameWithType>LINQ to XML birlikte çalışabilirlik yeteneklerini kullandığınızda, <xref:System.Xml.Linq.XNode.CreateReader%2A> oluşturmak için kullanabilirsiniz <xref:System.Xml.XmlReader> . Bu öğesinden okuyan modül, <xref:System.Xml.XmlReader> DÜĞÜMLERI XML ağacından okur ve bunlara göre işler.

## <a name="example-invoke-an-xslt-transformation"></a>Örnek: XSLT dönüşümünü çağırma

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

```vb
Dim xslMarkup As XDocument = _
    <?xml version='1.0'?>
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
    </xsl:stylesheet>

Dim xmlTree As XDocument = _
    <?xml version='1.0'?>
    <Parent>
        <Child1>Child1 data</Child1>
        <Child2>Child2 data</Child2>
    </Parent>

Dim newTree As XDocument = New XDocument()
Using writer As XmlWriter = newTree.CreateWriter()
    ' Load the style sheet.
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()
    xslt.Load(xslMarkup.CreateReader())

    ' Execute the transformation and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer)
End Using

Console.WriteLine(newTree)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

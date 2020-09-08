---
title: Bir XML ağacını XmlWriter-LINQ to XML doldurma
description: C# ve Visual Basic bir XML ağacını doldurmak için, CreateWriter kullanarak bir XMLWriter oluşturun ve ardından XmlWriter 'a yazın.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 3f8005eca009ae5f2102444a5494336d2caa2450
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553454"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml"></a>XML ağacını XmlWriter ile doldurma (LINQ to XML)

Bir XML ağacını doldurmanın bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter> , oluşturmak ve sonra öğesine yazmak için kullanmaktır <xref:System.Xml.XmlWriter> . XML ağacı, üzerine yazılan tüm düğümlerle doldurulur <xref:System.Xml.XmlWriter> .

Bu yöntemi genellikle, gibi bir öğesine yazmayı bekleyen başka bir sınıfla LINQ to XML kullandığınızda kullanırsınız <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .

## <a name="example-create-an-xmlwriter-to-accept-the-output-of-an-xslt-transformation"></a>Örnek: bir XSLT dönüşümünün çıkışını kabul etmek için bir XmlWriter oluşturma

<xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter> XSLT dönüşümünün çıkışını kabul etmek için ' i oluşturmak üzere öğesini kullanabilirsiniz. Bu, aşağıdaki örnekte gösterilmiştir:

- Bir XML ağacı ve <xref:System.Xml.XmlReader> öğesinden okumak için bir dosyası oluşturur.
- Yeni bir ağaç ve yazmak için bir ağaç oluşturur <xref:System.Xml.XmlWriter> .
- XSLT dönüşümünü çağırır, ve ile sağlar  <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .

Dönüştürme daha sonra yeni ağacı doldurur.

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
using (XmlWriter writer = newTree.CreateWriter())
{
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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [XML ağaçları](functional-construction.md)

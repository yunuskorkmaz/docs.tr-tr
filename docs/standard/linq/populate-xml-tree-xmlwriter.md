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
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml"></a><span data-ttu-id="e9e89-103">XML ağacını XmlWriter ile doldurma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e9e89-103">How to populate an XML tree with an XmlWriter (LINQ to XML)</span></span>

<span data-ttu-id="e9e89-104">Bir XML ağacını doldurmanın bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter> , oluşturmak ve sonra öğesine yazmak için kullanmaktır <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="e9e89-104">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="e9e89-105">XML ağacı, üzerine yazılan tüm düğümlerle doldurulur <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="e9e89-105">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="e9e89-106">Bu yöntemi genellikle, gibi bir öğesine yazmayı bekleyen başka bir sınıfla LINQ to XML kullandığınızda kullanırsınız <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="e9e89-106">You'd typically use this method when you use LINQ to XML with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

## <a name="example-create-an-xmlwriter-to-accept-the-output-of-an-xslt-transformation"></a><span data-ttu-id="e9e89-107">Örnek: bir XSLT dönüşümünün çıkışını kabul etmek için bir XmlWriter oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9e89-107">Example: Create an XmlWriter to accept the output of an XSLT transformation</span></span>

<span data-ttu-id="e9e89-108"><xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter> XSLT dönüşümünün çıkışını kabul etmek için ' i oluşturmak üzere öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9e89-108">You can use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter> to accept the output of an XSLT transformation.</span></span> <span data-ttu-id="e9e89-109">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e9e89-109">This is shown in the following example, which does the following:</span></span>

- <span data-ttu-id="e9e89-110">Bir XML ağacı ve <xref:System.Xml.XmlReader> öğesinden okumak için bir dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9e89-110">Creates an XML tree and an <xref:System.Xml.XmlReader> to read from it.</span></span>
- <span data-ttu-id="e9e89-111">Yeni bir ağaç ve yazmak için bir ağaç oluşturur <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="e9e89-111">Creates a new tree and an <xref:System.Xml.XmlWriter> to write to it.</span></span>
- <span data-ttu-id="e9e89-112">XSLT dönüşümünü çağırır, ve ile sağlar  <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="e9e89-112">Invokes the XSLT transformation, providing it with the  <xref:System.Xml.XmlReader> and the <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="e9e89-113">Dönüştürme daha sonra yeni ağacı doldurur.</span><span class="sxs-lookup"><span data-stu-id="e9e89-113">The transformation then populates the new tree.</span></span>

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

<span data-ttu-id="e9e89-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e9e89-114">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="e9e89-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9e89-115">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="e9e89-116">XML ağaçları</span><span class="sxs-lookup"><span data-stu-id="e9e89-116">XML trees</span></span>](functional-construction.md)

---
title: XML Ağacını Dönüştürmek için XSLT kullanma (C#)
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 7ebcfbd6be86fdd5e12bfc48a0fe80a084c6f9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74140918"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="99996-102">XML Ağacını Dönüştürmek için XSLT kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="99996-102">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="99996-103">Bir XML ağacı oluşturabilir, <xref:System.Xml.XmlReader> XML ağacından bir oluşturma, yeni bir <xref:System.Xml.XmlWriter> belge oluşturabilir ve yeni belgeye yazacak bir belge oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99996-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="99996-104">Daha sonra, XSLT dönüşümve dönüşüm <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> geçirerek çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99996-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="99996-105">Dönüşüm başarıyla tamamlandıktan sonra, yeni XML ağacı dönüşümün sonuçlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="99996-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99996-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="99996-106">Example</span></span>  
  
```csharp  
string xslt = @"<?xml version='1.0'?>  
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

var oldDocument = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

var newDocument = new XDocument();

using (var stringReader = new StringReader(xslt))
{
    using (XmlReader xsltReader = XmlReader.Create(stringReader))
    {
        var transformer = new XslCompiledTransform();
        transformer.Load(xsltReader);
        using (XmlReader oldDocumentReader = oldDocument.CreateReader())
        {
            using (XmlWriter newDocumentWriter = newDocument.CreateWriter())
            {
                transformer.Transform(oldDocumentReader, newDocumentWriter);
            }
        }
    }
}

string result = newDocument.ToString();
Console.WriteLine(result);
```  
  
 <span data-ttu-id="99996-107">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="99996-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99996-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99996-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>

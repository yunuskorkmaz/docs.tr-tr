---
title: XML ağacını dönüştürmek için XSLT kullanma (C#)
description: XmlReader ve XmlWriter örnekleri üzerinde XSLT dönüşümünü çağırarak C# ' deki bir XML ağacını dönüştürmek için XSLT 'yi nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: bce92136850aeef52e5b17cd7bc658b85fe70604
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302275"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="710f2-103">XML ağacını dönüştürmek için XSLT kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="710f2-103">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="710f2-104">Bir XML ağacı oluşturabilir, XML ağacından oluşturabilir, <xref:System.Xml.XmlReader> Yeni bir belge oluşturabilir ve <xref:System.Xml.XmlWriter> yeni belgeye yazılacak bir oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="710f2-104">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="710f2-105">Ardından, XSLT dönüşümünü çağırarak <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> dönüşümünü dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="710f2-105">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="710f2-106">Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="710f2-106">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="710f2-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="710f2-107">Example</span></span>  
  
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
  
 <span data-ttu-id="710f2-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="710f2-108">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="710f2-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="710f2-109">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>

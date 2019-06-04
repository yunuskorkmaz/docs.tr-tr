---
title: (C#) XML ağacı dönüştürmek için XSLT kullanma
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 69d1dd639b5bee226c8e295efe5d623eed169ac6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487031"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="f1504-102">(C#) XML ağacı dönüştürmek için XSLT kullanma</span><span class="sxs-lookup"><span data-stu-id="f1504-102">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="f1504-103">Bir XML ağacı oluşturma, oluşturun bir <xref:System.Xml.XmlReader> XML ağacından bir yeni belge oluşturun ve oluşturma bir <xref:System.Xml.XmlWriter> yeni belgeye yazacak.</span><span class="sxs-lookup"><span data-stu-id="f1504-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="f1504-104">XSLT dönüşümü geçirme, daha sonra çağırabilirsiniz <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> dönüşümü için.</span><span class="sxs-lookup"><span data-stu-id="f1504-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="f1504-105">Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşüm sonuçları ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="f1504-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1504-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1504-106">Example</span></span>  
  
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
  
    // Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="f1504-107">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f1504-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1504-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1504-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>

---
title: (Visual Basic) XML ağacı dönüştürmek için XSLT kullanma
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: a013e042bcaab321d8a5596368c349f296240d0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820171"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a><span data-ttu-id="5d5d8-102">(Visual Basic) XML ağacı dönüştürmek için XSLT kullanma</span><span class="sxs-lookup"><span data-stu-id="5d5d8-102">Using XSLT to Transform an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="5d5d8-103">Bir XML ağacı oluşturma, oluşturun bir <xref:System.Xml.XmlReader> XML ağacından bir yeni belge oluşturun ve oluşturma bir <xref:System.Xml.XmlWriter> yeni belgeye yazacak.</span><span class="sxs-lookup"><span data-stu-id="5d5d8-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="5d5d8-104">XSLT dönüşümü geçirme, daha sonra çağırabilirsiniz <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> dönüşümü için.</span><span class="sxs-lookup"><span data-stu-id="5d5d8-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="5d5d8-105">Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşüm sonuçları ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="5d5d8-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d5d8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d5d8-106">Example</span></span>  
  
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
  
Dim xmlTree As XElement = _   
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = _  
        New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="5d5d8-107">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5d5d8-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d5d8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d5d8-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5d5d8-109">Gelişmiş LINQ to XML programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d5d8-109">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

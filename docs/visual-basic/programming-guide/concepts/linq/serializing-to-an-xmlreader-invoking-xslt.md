---
title: XmlReader’a Serileştirme (XSLT Çağırma)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: 39ecbc1851764d221ac99c3e47c26bcbe84c9e46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349360"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="060f5-102">XmlReader 'a serileştirme (XSLT çağırma) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="060f5-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="060f5-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<xref:System.Xml?displayProperty=nameWithType> birlikte çalışabilirlik özelliklerini kullandığınızda, <xref:System.Xml.XmlReader>oluşturmak için <xref:System.Xml.Linq.XNode.CreateReader%2A> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="060f5-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="060f5-104">Bu <xref:System.Xml.XmlReader> okuyan modül, düğümleri XML ağacından okur ve bunlara göre işler.</span><span class="sxs-lookup"><span data-stu-id="060f5-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="060f5-105">XSLT dönüşümünü çağırma</span><span class="sxs-lookup"><span data-stu-id="060f5-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="060f5-106">Bu yöntem için olası bir kullanım XSLT dönüşümünü çağırmada olur.</span><span class="sxs-lookup"><span data-stu-id="060f5-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="060f5-107">XML ağacı oluşturabilir, XML ağacından bir <xref:System.Xml.XmlReader> oluşturabilir, yeni bir belge oluşturabilir ve sonra yeni belgeye yazmak için bir <xref:System.Xml.XmlWriter> oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="060f5-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="060f5-108">Ardından, <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>geçirerek XSLT dönüşümünü çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="060f5-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="060f5-109">Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="060f5-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="060f5-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="060f5-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="060f5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="060f5-111">See also</span></span>

- [<span data-ttu-id="060f5-112">XML ağaçlarını serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="060f5-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)

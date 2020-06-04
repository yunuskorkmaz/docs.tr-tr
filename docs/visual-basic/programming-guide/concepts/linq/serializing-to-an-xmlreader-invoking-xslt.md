---
title: XmlReader’a Serileştirme (XSLT Çağırma)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: e51bfc031ad6d5d0eb98718f5d547fb18eb45295
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357380"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="03f2e-102">XmlReader 'a serileştirme (XSLT çağırma) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03f2e-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="03f2e-103"><xref:System.Xml?displayProperty=nameWithType>Uygulamasının birlikte çalışabilirlik yeteneklerini kullandığınızda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , <xref:System.Xml.Linq.XNode.CreateReader%2A> oluşturmak için kullanabilirsiniz <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="03f2e-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="03f2e-104">Bu öğesinden okuyan modül, <xref:System.Xml.XmlReader> DÜĞÜMLERI XML ağacından okur ve bunlara göre işler.</span><span class="sxs-lookup"><span data-stu-id="03f2e-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="03f2e-105">XSLT dönüşümünü çağırma</span><span class="sxs-lookup"><span data-stu-id="03f2e-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="03f2e-106">Bu yöntem için olası bir kullanım XSLT dönüşümünü çağırmada olur.</span><span class="sxs-lookup"><span data-stu-id="03f2e-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="03f2e-107">Bir XML ağacı oluşturabilir, XML ağacından oluşturabilir, <xref:System.Xml.XmlReader> Yeni bir belge oluşturabilir ve sonra <xref:System.Xml.XmlWriter> yeni belgeye yazmak için oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03f2e-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="03f2e-108">Ardından, ve ile geçirerek XSLT dönüşümünü çağırabilirsiniz <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="03f2e-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="03f2e-109">Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="03f2e-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="03f2e-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="03f2e-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03f2e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03f2e-111">See also</span></span>

- [<span data-ttu-id="03f2e-112">XML ağaçlarını serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03f2e-112">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)

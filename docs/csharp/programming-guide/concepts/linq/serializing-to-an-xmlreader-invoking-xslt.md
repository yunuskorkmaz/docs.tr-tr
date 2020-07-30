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
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="e97a0-104">XmlReader 'a serileştirme (XSLT çağırma) (C#)</span><span class="sxs-lookup"><span data-stu-id="e97a0-104">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="e97a0-105"><xref:System.Xml?displayProperty=nameWithType>Uygulamasının birlikte çalışabilirlik yeteneklerini kullandığınızda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , <xref:System.Xml.Linq.XNode.CreateReader%2A> oluşturmak için kullanabilirsiniz <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="e97a0-105">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="e97a0-106">Bu öğesinden okuyan modül, <xref:System.Xml.XmlReader> DÜĞÜMLERI XML ağacından okur ve bunlara göre işler.</span><span class="sxs-lookup"><span data-stu-id="e97a0-106">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="e97a0-107">XSLT dönüşümünü çağırma</span><span class="sxs-lookup"><span data-stu-id="e97a0-107">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="e97a0-108">Bu yöntem için olası bir kullanım XSLT dönüşümünü çağırmada olur.</span><span class="sxs-lookup"><span data-stu-id="e97a0-108">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="e97a0-109">Bir XML ağacı oluşturabilir, XML ağacından oluşturabilir, <xref:System.Xml.XmlReader> Yeni bir belge oluşturabilir ve sonra <xref:System.Xml.XmlWriter> yeni belgeye yazmak için oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e97a0-109">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="e97a0-110">Ardından, ve ile geçirerek XSLT dönüşümünü çağırabilirsiniz <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="e97a0-110">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="e97a0-111">Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="e97a0-111">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="e97a0-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e97a0-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e97a0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e97a0-113">See also</span></span>

- [<span data-ttu-id="e97a0-114">XML ağaçlarını serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="e97a0-114">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)

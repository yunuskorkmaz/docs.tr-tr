---
title: 'Nasıl yapılır: bir XmlWriter (LINQ-XML) içeren bir XML ağacı Doldur (C#)'
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: cc3aeb8e8fbef3b109c9bc591084f0d033f5f476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323680"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="22245-102">Nasıl yapılır: bir XmlWriter (LINQ-XML) içeren bir XML ağacı Doldur (C#)</span><span class="sxs-lookup"><span data-stu-id="22245-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="22245-103">Bir XML ağacı doldurmak için bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> oluşturmak için bir <xref:System.Xml.XmlWriter>ve ardından yazma <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="22245-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="22245-104">XML ağaç yazılan tüm düğümleri doldurulur <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="22245-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="22245-105">Kullandığınızda bu yöntem genellikle kullanırsınız [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yazmak için bekliyor başka bir sınıf ile bir <xref:System.Xml.XmlWriter>, gibi <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="22245-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22245-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="22245-106">Example</span></span>  
 <span data-ttu-id="22245-107">Olası kullanım için <xref:System.Xml.Linq.XContainer.CreateWriter%2A> XSLT dönüştürmesi çağrılırken oluşan.</span><span class="sxs-lookup"><span data-stu-id="22245-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="22245-108">Bu örnek bir XML ağaç oluşturur, oluşturur bir <xref:System.Xml.XmlReader> XML ağacından bir yeni belge oluşturur ve ardından oluşturan bir <xref:System.Xml.XmlWriter> yeni belgesine yazılacak.</span><span class="sxs-lookup"><span data-stu-id="22245-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="22245-109">Ardından tümleştirilmesidir XSLT dönüşümü çağırır <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="22245-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="22245-110">Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşüm sonuçları ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="22245-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="22245-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="22245-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22245-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22245-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="22245-113">Oluşturma XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="22245-113">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

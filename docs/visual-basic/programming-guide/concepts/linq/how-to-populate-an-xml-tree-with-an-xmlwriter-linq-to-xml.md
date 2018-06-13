---
title: 'Nasıl yapılır: bir XmlWriter (LINQ-XML) içeren bir XML ağacı Doldur (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: bc17b84b945e93443ab6d9f337e852feba5b0662
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642109"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="1f6e6-102">Nasıl yapılır: bir XmlWriter (LINQ-XML) içeren bir XML ağacı Doldur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f6e6-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="1f6e6-103">Bir XML ağacı doldurmak için bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> oluşturmak için bir <xref:System.Xml.XmlWriter>ve ardından yazma <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="1f6e6-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="1f6e6-104">XML ağaç yazılan tüm düğümleri doldurulur <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="1f6e6-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="1f6e6-105">Kullandığınızda bu yöntem genellikle kullanırsınız [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yazmak için bekliyor başka bir sınıf ile bir <xref:System.Xml.XmlWriter>, gibi <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="1f6e6-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f6e6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f6e6-106">Example</span></span>  
 <span data-ttu-id="1f6e6-107">Olası kullanım için <xref:System.Xml.Linq.XContainer.CreateWriter%2A> XSLT dönüştürmesi çağrılırken oluşan.</span><span class="sxs-lookup"><span data-stu-id="1f6e6-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="1f6e6-108">Bu örnek bir XML ağaç oluşturur, oluşturur bir <xref:System.Xml.XmlReader> XML ağacından bir yeni belge oluşturur ve ardından oluşturan bir <xref:System.Xml.XmlWriter> yeni belgesine yazılacak.</span><span class="sxs-lookup"><span data-stu-id="1f6e6-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="1f6e6-109">Ardından tümleştirilmesidir XSLT dönüşümü çağırır <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="1f6e6-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="1f6e6-110">Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşüm sonuçları ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1f6e6-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="1f6e6-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="1f6e6-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f6e6-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f6e6-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="1f6e6-113">Oluşturma XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f6e6-113">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

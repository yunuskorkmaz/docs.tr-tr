---
title: 'Nasıl yapılır: XML Ağacını XmlWriter ile Doldurma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: b3a36326175eeba8cd692a2c71f1f9b0fde24b5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397979"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="34669-102">Nasıl yapılır: bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34669-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="34669-103">Bir XML ağacını doldurmanın bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter> , oluşturmak ve sonra öğesine yazmak için kullanmaktır <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="34669-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="34669-104">XML ağacı, üzerine yazılan tüm düğümlerle doldurulur <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="34669-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="34669-105">Bu yöntemi genellikle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , gibi bir öğesine yazmayı bekleyen başka bir sınıf ile kullandığınızda kullanırsınız <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="34669-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34669-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="34669-106">Example</span></span>  
 <span data-ttu-id="34669-107">İçin olası bir kullanım <xref:System.Xml.Linq.XContainer.CreateWriter%2A> XSLT dönüşümünü çağırırken olur.</span><span class="sxs-lookup"><span data-stu-id="34669-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="34669-108">Bu örnek bir XML ağacı oluşturur, <xref:System.Xml.XmlReader> XML ağacından bir oluşturur, yeni bir belge oluşturur ve <xref:System.Xml.XmlWriter> yeni belgeye yazmak için bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34669-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="34669-109">Ardından, ve geçirerek XSLT dönüşümünü çağırır <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="34669-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="34669-110">Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="34669-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="34669-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="34669-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34669-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34669-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="34669-113">XML ağaçları oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34669-113">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)

---
title: Bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (C#)
description: Bir XmlWriter oluşturmak için CreateWriter kullanarak bir XML ağacının nasıl doldurulacağını öğrenin ve ardından C# ' de LINQ to XML ' de XmlWriter 'a yazın.
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 9639c5947583bccf4f8ba427fc8611e181ef1536
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104798"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="587f4-103">Bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="587f4-103">How to populate an XML tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="587f4-104">Bir XML ağacını doldurmanın bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter> , oluşturmak ve sonra öğesine yazmak için kullanmaktır <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="587f4-104">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="587f4-105">XML ağacı, üzerine yazılan tüm düğümlerle doldurulur <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="587f4-105">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="587f4-106">Bu yöntemi genellikle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , gibi bir öğesine yazmayı bekleyen başka bir sınıf ile kullandığınızda kullanırsınız <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="587f4-106">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="587f4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="587f4-107">Example</span></span>  
 <span data-ttu-id="587f4-108">İçin olası bir kullanım <xref:System.Xml.Linq.XContainer.CreateWriter%2A> XSLT dönüşümünü çağırırken olur.</span><span class="sxs-lookup"><span data-stu-id="587f4-108">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="587f4-109">Bu örnek bir XML ağacı oluşturur, <xref:System.Xml.XmlReader> XML ağacından bir oluşturur, yeni bir belge oluşturur ve <xref:System.Xml.XmlWriter> yeni belgeye yazmak için bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="587f4-109">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="587f4-110">Ardından, ve geçirerek XSLT dönüşümünü çağırır <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="587f4-110">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="587f4-111">Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="587f4-111">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="587f4-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="587f4-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="587f4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="587f4-113">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="587f4-114">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="587f4-114">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)

---
title: 'Nasıl yapılır: Bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 88b088ddad54d1fef67cb4c86f8df4eee7bf3662
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593111"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="d8e46-102">Nasıl yapılır: Bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8e46-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d8e46-103">Bir xml ağacını doldurmanın bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter>, oluşturmak <xref:System.Xml.XmlWriter>ve sonra öğesine yazmak için kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d8e46-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="d8e46-104">XML ağacı, <xref:System.Xml.XmlWriter>üzerine yazılan tüm düğümlerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d8e46-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="d8e46-105">Bu yöntemi genellikle, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlWriter>gibi bir öğesine yazmayı bekleyen başka bir sınıf ile kullandığınızda kullanırsınız. <xref:System.Xml.Xsl.XslCompiledTransform></span><span class="sxs-lookup"><span data-stu-id="d8e46-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8e46-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8e46-106">Example</span></span>  
 <span data-ttu-id="d8e46-107">İçin <xref:System.Xml.Linq.XContainer.CreateWriter%2A> olası bir kullanım XSLT dönüşümünü çağırırken olur.</span><span class="sxs-lookup"><span data-stu-id="d8e46-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="d8e46-108">Bu örnek bir XML ağacı oluşturur, XML ağacından <xref:System.Xml.XmlReader> bir oluşturur, yeni bir belge oluşturur ve yeni belgeye yazmak için bir <xref:System.Xml.XmlWriter> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8e46-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="d8e46-109">Ardından, <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>geçirerek XSLT dönüşümünü çağırır.</span><span class="sxs-lookup"><span data-stu-id="d8e46-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="d8e46-110">Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d8e46-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="d8e46-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d8e46-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8e46-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8e46-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="d8e46-113">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="d8e46-113">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)

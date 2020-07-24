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
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (C#)
Bir XML ağacını doldurmanın bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter> , oluşturmak ve sonra öğesine yazmak için kullanmaktır <xref:System.Xml.XmlWriter> . XML ağacı, üzerine yazılan tüm düğümlerle doldurulur <xref:System.Xml.XmlWriter> .  
  
 Bu yöntemi genellikle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , gibi bir öğesine yazmayı bekleyen başka bir sınıf ile kullandığınızda kullanırsınız <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
## <a name="example"></a>Örnek  
 İçin olası bir kullanım <xref:System.Xml.Linq.XContainer.CreateWriter%2A> XSLT dönüşümünü çağırırken olur. Bu örnek bir XML ağacı oluşturur, <xref:System.Xml.XmlReader> XML ağacından bir oluşturur, yeni bir belge oluşturur ve <xref:System.Xml.XmlWriter> yeni belgeye yazmak için bir oluşturur. Ardından, ve geçirerek XSLT dönüşümünü çağırır <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> . Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [XML ağaçları oluşturma (C#)](./linq-to-xml-overview.md)

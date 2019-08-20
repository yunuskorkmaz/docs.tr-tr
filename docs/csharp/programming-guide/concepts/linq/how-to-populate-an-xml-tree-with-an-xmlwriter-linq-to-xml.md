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
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Nasıl yapılır: Bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (C#)
Bir xml ağacını doldurmanın bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter>, oluşturmak <xref:System.Xml.XmlWriter>ve sonra öğesine yazmak için kullanmaktır. XML ağacı, <xref:System.Xml.XmlWriter>üzerine yazılan tüm düğümlerle doldurulur.  
  
 Bu yöntemi genellikle, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlWriter>gibi bir öğesine yazmayı bekleyen başka bir sınıf ile kullandığınızda kullanırsınız. <xref:System.Xml.Xsl.XslCompiledTransform>  
  
## <a name="example"></a>Örnek  
 İçin <xref:System.Xml.Linq.XContainer.CreateWriter%2A> olası bir kullanım XSLT dönüşümünü çağırırken olur. Bu örnek bir XML ağacı oluşturur, XML ağacından <xref:System.Xml.XmlReader> bir oluşturur, yeni bir belge oluşturur ve yeni belgeye yazmak için bir <xref:System.Xml.XmlWriter> oluşturur. Ardından, <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>geçirerek XSLT dönüşümünü çağırır. Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.  
  
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

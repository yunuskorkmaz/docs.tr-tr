---
title: Bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: f48843af403f2ee0e6d2850deab009a143f55dc7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345767"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (C#)
Bir XML ağacını doldurmanın bir yolu, bir <xref:System.Xml.XmlWriter>oluşturmak ve ardından <xref:System.Xml.XmlWriter>yazmak için <xref:System.Xml.Linq.XContainer.CreateWriter%2A> kullanmaktır. XML ağacı, <xref:System.Xml.XmlWriter>yazılmış tüm düğümlerle doldurulur.  
  
 Bu yöntemi genellikle <xref:System.Xml.Xsl.XslCompiledTransform>gibi bir <xref:System.Xml.XmlWriter>yazmayı bekleyen başka bir sınıfla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullandığınızda kullanırsınız.  
  
## <a name="example"></a>Örnek  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> için olası bir kullanım XSLT dönüşümünü çağırmada olur. Bu örnek bir XML ağacı oluşturur, XML ağacından bir <xref:System.Xml.XmlReader> oluşturur, yeni bir belge oluşturur ve sonra yeni belgeye yazmak için bir <xref:System.Xml.XmlWriter> oluşturur. Ardından <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>geçirerek XSLT dönüşümünü çağırır. Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.  
  
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

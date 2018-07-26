---
title: 'Nasıl yapılır: XML ağacını XmlWriter (LINQ to XML) ile doldurma (C#)'
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: cc3aeb8e8fbef3b109c9bc591084f0d033f5f476
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198555"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Nasıl yapılır: XML ağacını XmlWriter (LINQ to XML) ile doldurma (C#)
Bir XML ağacı doldurma yollarından biri kullanmaktır <xref:System.Xml.Linq.XContainer.CreateWriter%2A> oluşturmak için bir <xref:System.Xml.XmlWriter>ve ardından yazma <xref:System.Xml.XmlWriter>. XML ağacı yazılan tüm düğümleri doldurulur <xref:System.Xml.XmlWriter>.  
  
 Kullandığınızda bu yöntem genellikle kullanırsınız [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yazılacak bekliyor başka bir sınıf ile bir <xref:System.Xml.XmlWriter>, gibi <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Örnek  
 Olası kullanım için <xref:System.Xml.Linq.XContainer.CreateWriter%2A> XSLT dönüştürmesi çağrılırken oluşan. Bu örnek, bir XML ağacı oluşturur, oluşturur bir <xref:System.Xml.XmlReader> XML ağacından yeni bir belge oluşturur ve ardından oluşturan bir <xref:System.Xml.XmlWriter> yeni belgesine yazılacak. Ardından tümleştirilmesidir XSLT dönüşümü, çağıran <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>. Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşümü sonuçları ile doldurulur.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [XML ağaçları oluşturma (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

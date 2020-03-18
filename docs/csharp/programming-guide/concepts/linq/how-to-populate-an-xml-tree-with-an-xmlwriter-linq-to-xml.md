---
title: Bir XML ağacıxmlWriter (LINQ- XML) (C#) ile doldurma
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: f48843af403f2ee0e6d2850deab009a143f55dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345767"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Bir XML ağacıxmlWriter (LINQ- XML) (C#) ile doldurma
Bir XML ağacı doldurmak için bir <xref:System.Xml.Linq.XContainer.CreateWriter%2A> yolu <xref:System.Xml.XmlWriter>oluşturmak için kullanmak <xref:System.Xml.XmlWriter>ve sonra yazmak . XML ağacı, 'ye yazılan tüm düğümlerle <xref:System.Xml.XmlWriter>doldurulur.  
  
 Bu yöntemi genellikle, bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform>' ye yazmayı bekleyen başka bir sınıfla kullandığınızda kullanırsınız.  
  
## <a name="example"></a>Örnek  
 Olası kullanımlardan <xref:System.Xml.Linq.XContainer.CreateWriter%2A> biri XSLT dönüşümü için çağrıda bulunan dır. Bu örnek bir XML ağacı oluşturur, XML ağacından bir oluşturma, <xref:System.Xml.XmlReader> yeni bir <xref:System.Xml.XmlWriter> belge oluşturur ve sonra yeni belgeye yazılması gereken bir belge oluşturur. Daha sonra XSLT dönüşüm çağırır, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>geçen ve . Dönüşüm başarıyla tamamlandıktan sonra, yeni XML ağacı dönüşümün sonuçlarıyla doldurulur.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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
- [XML Ağaçları Oluşturma (C#)](./linq-to-xml-overview.md)

---
title: XmlReader'a serileştirme (XSLT Başlatma) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: b079fe05fa8c230f644e011dcb62ec54f55cae60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487185"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>XmlReader'a serileştirme (XSLT Başlatma) (C#)
<xref:System.Xml?displayProperty=nameWithType> Birlikte çalışabilirlik yeteneklerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullandığınızda, <xref:System.Xml.Linq.XNode.CreateReader%2A> bir <xref:System.Xml.XmlReader>. Buradan <xref:System.Xml.XmlReader> okuyan modül XML ağacındaki düğümleri okur ve buna göre işler.  
  
## <a name="invoking-an-xslt-transformation"></a>XSLT Dönüşümü'ne neden olmak  
 Bu yöntem için olası bir kullanım bir XSLT dönüşümü çağırArak. Bir XML ağacı oluşturabilir, <xref:System.Xml.XmlReader> XML ağacından bir oluşturma, yeni bir <xref:System.Xml.XmlWriter> belge oluşturabilir ve ardından yeni belgeye yazacak bir belge oluşturabilirsiniz. Daha sonra, XSLT dönüşümlerini çağırabilir, içeri girebilirsiniz <xref:System.Xml.XmlReader> ve. <xref:System.Xml.XmlWriter> Dönüşüm başarıyla tamamlandıktan sonra, yeni XML ağacı dönüşümün sonuçlarıyla doldurulur.  
  
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
using (XmlWriter writer = newTree.CreateWriter()) {  
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

- [XML Ağaçlarını Serihale Getirme (C#)](serializing-to-files-textwriters-and-xmlwriters.md)

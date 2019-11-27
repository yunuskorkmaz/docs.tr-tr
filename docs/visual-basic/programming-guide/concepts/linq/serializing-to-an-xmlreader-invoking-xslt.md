---
title: XmlReader’a Serileştirme (XSLT Çağırma)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: 39ecbc1851764d221ac99c3e47c26bcbe84c9e46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349360"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>XmlReader 'a serileştirme (XSLT çağırma) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<xref:System.Xml?displayProperty=nameWithType> birlikte çalışabilirlik özelliklerini kullandığınızda, <xref:System.Xml.XmlReader>oluşturmak için <xref:System.Xml.Linq.XNode.CreateReader%2A> kullanabilirsiniz. Bu <xref:System.Xml.XmlReader> okuyan modül, düğümleri XML ağacından okur ve bunlara göre işler.  
  
## <a name="invoking-an-xslt-transformation"></a>XSLT dönüşümünü çağırma  
 Bu yöntem için olası bir kullanım XSLT dönüşümünü çağırmada olur. XML ağacı oluşturabilir, XML ağacından bir <xref:System.Xml.XmlReader> oluşturabilir, yeni bir belge oluşturabilir ve sonra yeni belgeye yazmak için bir <xref:System.Xml.XmlWriter> oluşturabilirsiniz. Ardından, <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>geçirerek XSLT dönüşümünü çağırabilirsiniz. Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını serileştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)

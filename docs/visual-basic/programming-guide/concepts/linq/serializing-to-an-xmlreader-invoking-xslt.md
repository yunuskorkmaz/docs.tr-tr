---
title: XmlReader’a Serileştirme (XSLT Çağırma)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: e51bfc031ad6d5d0eb98718f5d547fb18eb45295
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357380"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>XmlReader 'a serileştirme (XSLT çağırma) (Visual Basic)
<xref:System.Xml?displayProperty=nameWithType>Uygulamasının birlikte çalışabilirlik yeteneklerini kullandığınızda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , <xref:System.Xml.Linq.XNode.CreateReader%2A> oluşturmak için kullanabilirsiniz <xref:System.Xml.XmlReader> . Bu öğesinden okuyan modül, <xref:System.Xml.XmlReader> DÜĞÜMLERI XML ağacından okur ve bunlara göre işler.  
  
## <a name="invoking-an-xslt-transformation"></a>XSLT dönüşümünü çağırma  
 Bu yöntem için olası bir kullanım XSLT dönüşümünü çağırmada olur. Bir XML ağacı oluşturabilir, XML ağacından oluşturabilir, <xref:System.Xml.XmlReader> Yeni bir belge oluşturabilir ve sonra <xref:System.Xml.XmlWriter> yeni belgeye yazmak için oluşturabilirsiniz. Ardından, ve ile geçirerek XSLT dönüşümünü çağırabilirsiniz <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> . Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.  
  
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

- [XML ağaçlarını serileştirme (Visual Basic)](serializing-xml-trees.md)

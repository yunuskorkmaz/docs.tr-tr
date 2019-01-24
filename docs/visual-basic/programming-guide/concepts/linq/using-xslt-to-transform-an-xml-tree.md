---
title: (Visual Basic) XML ağacı dönüştürmek için XSLT kullanma
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: 37fd25a327906327f33106ae145d45c5387cae47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690403"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a>(Visual Basic) XML ağacı dönüştürmek için XSLT kullanma
Bir XML ağacı oluşturma, oluşturun bir <xref:System.Xml.XmlReader> XML ağacından bir yeni belge oluşturun ve oluşturma bir <xref:System.Xml.XmlWriter> yeni belgeye yazacak. XSLT dönüşümü geçirme, daha sonra çağırabilirsiniz <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> dönüşümü için. Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşüm sonuçları ile doldurulur.  
  
## <a name="example"></a>Örnek  
  
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
  
Dim xmlTree As XElement = _   
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = _  
        New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transform and output the results to a writer.  
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
- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [Gelişmiş LINQ to XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

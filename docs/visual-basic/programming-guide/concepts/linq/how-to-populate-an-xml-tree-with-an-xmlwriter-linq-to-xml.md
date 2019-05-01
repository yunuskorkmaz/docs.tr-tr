---
title: 'Nasıl yapılır: Bir XML ağacını XmlWriter (LINQ to XML) ile doldurun (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: de020444950695e27b9d840dac41fab74b9c7eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789083"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Nasıl yapılır: Bir XML ağacını XmlWriter (LINQ to XML) ile doldurun (Visual Basic)
Bir XML ağacı doldurma yollarından biri kullanmaktır <xref:System.Xml.Linq.XContainer.CreateWriter%2A> oluşturmak için bir <xref:System.Xml.XmlWriter>ve ardından yazma <xref:System.Xml.XmlWriter>. XML ağacı yazılan tüm düğümleri doldurulur <xref:System.Xml.XmlWriter>.  
  
 Kullandığınızda bu yöntem genellikle kullanırsınız [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yazılacak bekliyor başka bir sınıf ile bir <xref:System.Xml.XmlWriter>, gibi <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Örnek  
 Olası kullanım için <xref:System.Xml.Linq.XContainer.CreateWriter%2A> XSLT dönüştürmesi çağrılırken oluşan. Bu örnek, bir XML ağacı oluşturur, oluşturur bir <xref:System.Xml.XmlReader> XML ağacından yeni bir belge oluşturur ve ardından oluşturan bir <xref:System.Xml.XmlWriter> yeni belgesine yazılacak. Ardından tümleştirilmesidir XSLT dönüşümü, çağıran <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>. Dönüştürme başarıyla tamamlandıktan sonra yeni bir XML ağacı dönüşümü sonuçları ile doldurulur.  
  
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

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [XML ağaçları (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

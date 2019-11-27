---
title: 'Nasıl yapılır: bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: ec44f6e21453a1333f842030bae0c4f80dedb9c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333767"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Nasıl yapılır: bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (Visual Basic)
Bir XML ağacını doldurmanın bir yolu, bir <xref:System.Xml.XmlWriter>oluşturmak ve ardından <xref:System.Xml.XmlWriter>yazmak için <xref:System.Xml.Linq.XContainer.CreateWriter%2A> kullanmaktır. XML ağacı, <xref:System.Xml.XmlWriter>yazılmış tüm düğümlerle doldurulur.  
  
 Bu yöntemi genellikle <xref:System.Xml.Xsl.XslCompiledTransform>gibi bir <xref:System.Xml.XmlWriter>yazmayı bekleyen başka bir sınıfla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullandığınızda kullanırsınız.  
  
## <a name="example"></a>Örnek  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> için olası bir kullanım XSLT dönüşümünü çağırmada olur. Bu örnek bir XML ağacı oluşturur, XML ağacından bir <xref:System.Xml.XmlReader> oluşturur, yeni bir belge oluşturur ve sonra yeni belgeye yazmak için bir <xref:System.Xml.XmlWriter> oluşturur. Ardından <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>geçirerek XSLT dönüşümünü çağırır. Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.  
  
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
- [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

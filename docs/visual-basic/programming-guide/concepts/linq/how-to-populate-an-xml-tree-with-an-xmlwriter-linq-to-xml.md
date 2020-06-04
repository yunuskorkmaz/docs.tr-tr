---
title: 'Nasıl yapılır: XML Ağacını XmlWriter ile Doldurma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: b3a36326175eeba8cd692a2c71f1f9b0fde24b5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397979"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Nasıl yapılır: bir XmlWriter ile bir XML ağacını doldurma (LINQ to XML) (Visual Basic)
Bir XML ağacını doldurmanın bir yolu <xref:System.Xml.Linq.XContainer.CreateWriter%2A> <xref:System.Xml.XmlWriter> , oluşturmak ve sonra öğesine yazmak için kullanmaktır <xref:System.Xml.XmlWriter> . XML ağacı, üzerine yazılan tüm düğümlerle doldurulur <xref:System.Xml.XmlWriter> .  
  
 Bu yöntemi genellikle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , gibi bir öğesine yazmayı bekleyen başka bir sınıf ile kullandığınızda kullanırsınız <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
## <a name="example"></a>Örnek  
 İçin olası bir kullanım <xref:System.Xml.Linq.XContainer.CreateWriter%2A> XSLT dönüşümünü çağırırken olur. Bu örnek bir XML ağacı oluşturur, <xref:System.Xml.XmlReader> XML ağacından bir oluşturur, yeni bir belge oluşturur ve <xref:System.Xml.XmlWriter> yeni belgeye yazmak için bir oluşturur. Ardından, ve geçirerek XSLT dönüşümünü çağırır <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> . Dönüştürme başarıyla tamamlandıktan sonra, yeni XML ağacı dönüştürmenin sonuçlarıyla doldurulur.  
  
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
- [XML ağaçları oluşturma (Visual Basic)](creating-xml-trees.md)

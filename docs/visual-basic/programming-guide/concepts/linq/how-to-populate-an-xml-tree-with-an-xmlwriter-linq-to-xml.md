---
title: 'Nasıl yapılır: XmlWriter ile bir XML Ağacı doldurma (XML IÇIN LINQ)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: fecf57eac570a9ca57dd1fe2f7a0b54cd78c33b5
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267008"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Nasıl yapılır: XmlWriter (LINQ - XML) (Visual Basic) ile Bir XML Ağacını Doldurma
Bir XML ağacı doldurmak için bir <xref:System.Xml.Linq.XContainer.CreateWriter%2A> yolu <xref:System.Xml.XmlWriter>oluşturmak için kullanmak <xref:System.Xml.XmlWriter>ve sonra yazmak . XML ağacı, 'ye yazılan tüm düğümlerle <xref:System.Xml.XmlWriter>doldurulur.  
  
 Bu yöntemi genellikle, bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform>' ye yazmayı bekleyen başka bir sınıfla kullandığınızda kullanırsınız.  
  
## <a name="example"></a>Örnek  
 Olası kullanımlardan <xref:System.Xml.Linq.XContainer.CreateWriter%2A> biri XSLT dönüşümü için çağrıda bulunan dır. Bu örnek bir XML ağacı oluşturur, XML ağacından bir oluşturma, <xref:System.Xml.XmlReader> yeni bir <xref:System.Xml.XmlWriter> belge oluşturur ve sonra yeni belgeye yazılması gereken bir belge oluşturur. Daha sonra XSLT dönüşüm çağırır, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>geçen ve . Dönüşüm başarıyla tamamlandıktan sonra, yeni XML ağacı dönüşümün sonuçlarıyla doldurulur.  
  
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
- [XML Ağaçları Oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

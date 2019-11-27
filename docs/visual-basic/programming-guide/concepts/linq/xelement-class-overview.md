---
title: XElement Sınıfına Genel Bakış
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: ff751a14abf9a9cb5d64e44e601c5d0ca6218c7d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349317"
---
# <a name="xelement-class-overview-visual-basic"></a>XElement sınıfına genel bakış (Visual Basic)
<xref:System.Xml.Linq.XElement> sınıfı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]temel sınıflardan biridir. Bir XML öğesini temsil eder. Bu sınıfı, öğeler oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirme; alt öğeleri ekleyin, değiştirin veya silin; özniteliği bir öğeye ekleyin; veya metin biçimindeki bir öğenin içeriğini seri hale getirme. Ayrıca, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>ve <xref:System.Xml.Xsl.XslCompiledTransform>gibi <xref:System.Xml?displayProperty=nameWithType>diğer sınıflarla da birlikte kullanabilirsiniz.  
  
## <a name="xelement-functionality"></a>XElement Işlevselliği  
 Bu konu, <xref:System.Xml.Linq.XElement> sınıfı tarafından sunulan işlevleri açıklamaktadır.  
  
### <a name="constructing-xml-trees"></a>XML ağaçları oluşturma  
 Aşağıdakiler dahil olmak üzere çeşitli yollarla XML ağaçları oluşturabilirsiniz:  
  
- Kodda bir XML ağacı oluşturabilirsiniz. Daha fazla bilgi için bkz. [xml ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
- <xref:System.IO.TextReader>, metin dosyaları veya Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan XML ayrıştırılabilir. Daha fazla bilgi için bkz. [XML 'ı ayrıştırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).  
  
- Ağacı doldurmak için bir <xref:System.Xml.XmlReader> kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
- Bir <xref:System.Xml.XmlWriter>içerik yazabilmesi için bir modülünüzün varsa, bir yazıcı oluşturmak, yazıcıyı modüle geçirmek ve sonra da XML ağacını doldurmak için <xref:System.Xml.XmlWriter> yazılan içeriği kullanmak için <xref:System.Xml.Linq.XContainer.CreateWriter%2A> yöntemini kullanabilirsiniz.  
  
 Ancak, bir XML ağacı oluşturmanın en yaygın yolu aşağıdaki gibidir:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Bir XML ağacı oluşturmaya yönelik başka bir çok yaygın teknik, aşağıdaki örnekte gösterildiği gibi bir XML ağacını doldurmak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusunun sonuçlarının kullanılmasını içerir:  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>XML Ağaçlarını Serileştirme  
 XML ağacını bir <xref:System.IO.File>, <xref:System.IO.TextWriter>veya <xref:System.Xml.XmlWriter>seri hale getirebilirsiniz.  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını serileştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>XML verilerini eksen yöntemleri aracılığıyla alma  
 Öznitelikleri, alt öğeleri, alt öğeleri ve üst öğeleri almak için eksen yöntemlerini kullanabilirsiniz. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları eksen yöntemleri üzerinde çalışır ve bir XML ağacı üzerinde gezinmek ve işlemek için çeşitli esnek ve güçlü yollar sunar.  
  
 Daha fazla bilgi için bkz. [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>XML Ağaçlarını Sorgulama  
 Bir XML ağacından veri çıkaran [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları yazabilirsiniz.  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını sorgulama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>XML ağaçlarını değiştirme  
 Bir öğeyi, içeriğini veya özniteliklerini değiştirme gibi çeşitli yollarla değiştirebilirsiniz. Ayrıca bir öğeyi üst öğesinden da kaldırabilirsiniz.  
  
 Daha fazla bilgi için bkz. [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

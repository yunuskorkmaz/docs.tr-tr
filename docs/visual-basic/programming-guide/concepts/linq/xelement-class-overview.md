---
title: "XElement sınıfına genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: decd7c4f805de0d23b091972ee95a323baf0b7d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xelement-class-overview-visual-basic"></a>XElement sınıfına genel bakış (Visual Basic)
<xref:System.Xml.Linq.XElement> Sınıfı temel sınıflarda biridir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Bir XML öğesi temsil eder. Bu sınıf, öğeleri oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirme; ekleme, değiştirme veya alt öğeleri silme; öznitelikleri için bir öğe ekleyin; veya içeriği, bir öğenin metin biçiminde seri hale. Ayrıca diğer sınıflarda ile çalışabilirler <xref:System.Xml?displayProperty=nameWithType>, gibi <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="xelement-functionality"></a>XElement işlevi  
 Bu konuda tarafından sağlanan işlevleri açıklanmaktadır <xref:System.Xml.Linq.XElement> sınıfı.  
  
### <a name="constructing-xml-trees"></a>XML ağaçları oluşturma  
 Aşağıdakiler dahil olmak üzere çeşitli XML ağaçlarında oluşturabileceğiniz:  
  
-   Kod XML ağacında oluşturabilirsiniz. Daha fazla bilgi için bkz: [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
-   XML dahil olmak üzere çeşitli kaynaklardan ayrıştıramıyor bir <xref:System.IO.TextReader>, metin dosyaları veya bir Web adresi (URL). Daha fazla bilgi için bkz: [XML Ayrıştırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).  
  
-   Kullanabileceğiniz bir <xref:System.Xml.XmlReader> ağaç doldurmak için. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.  
  
-   İçeriği yazabilen bir modül varsa bir <xref:System.Xml.XmlWriter>, kullanabileceğiniz <xref:System.Xml.Linq.XContainer.CreateWriter%2A> bir yazıcı oluşturmak, yazıcı modülü geçirmek ve yazılan içeriği kullanmak için yöntemi <xref:System.Xml.XmlWriter> XML ağaç doldurmak için.  
  
 Ancak, bir XML ağacı oluşturmak için en yaygın yolu şu şekildedir:  
  
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
  
 Bir XML ağacı oluşturmak için başka bir yaygın yöntem sonuçlarını kullanılmasına bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] aşağıdaki örnekte gösterildiği gibi bir XML ağacı doldurmak için sorgu:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>XML ağaçları seri hale getirme  
 XML ağaca serileştirebiliyorsa bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.  
  
 Daha fazla bilgi için bkz: [seri hale getirme XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Eksen yöntemleriyle XML verilerini alma  
 Eksen yöntemleri öznitelikleri, alt öğe, alt öğeleri ve üst öğeleri almak için kullanabilirsiniz. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]sorguları eksen yöntemlere çalışır ve aracılığıyla gidin ve bir XML ağacı işlemek için birden fazla esnek ve güçlü yollar sağlar.  
  
 Daha fazla bilgi için bkz: [LINQ-XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>XML ağaçları sorgulama  
 Yazabileceğiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir XML ağacından veri ayıklamak sorgular.  
  
 Daha fazla bilgi için bkz: [sorgulama XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>XML ağaçlarını değiştirme  
 Öğenin, içeriği veya özniteliklerini değiştirme dahil olmak üzere çeşitli değiştirebilirsiniz. Ayrıca, bir öğenin üst öğesinden kaldırabilirsiniz.  
  
 Daha fazla bilgi için bkz: [XML ağaçlarını değiştirme (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

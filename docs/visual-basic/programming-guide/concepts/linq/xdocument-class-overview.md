---
title: XDocument Sınıfına Genel Bakış
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: cbc1ccca53978da07f31c0ba7e54eca9f06b0e72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349284"
---
# <a name="xdocument-class-overview-visual-basic"></a>XDocument sınıfına genel bakış (Visual Basic)
Bu konu, <xref:System.Xml.Linq.XDocument> sınıfını tanıtır.  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument sınıfına genel bakış  
 <xref:System.Xml.Linq.XDocument> sınıfı, geçerli bir XML belgesi için gereken bilgileri içerir. Buna bir XML bildirimi, işleme yönergeleri ve açıklamalar dahildir.  
  
 <xref:System.Xml.Linq.XDocument> sınıfı tarafından sunulan belirli işlevselliğe ihtiyacınız varsa yalnızca <xref:System.Xml.Linq.XDocument> nesneleri oluşturmanız gerektiğini unutmayın. Birçok durumda, <xref:System.Xml.Linq.XElement>doğrudan ile çalışabilirsiniz. <xref:System.Xml.Linq.XElement> doğrudan çalışmak daha basit bir programlama modelidir.  
  
 <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer>türetilir. Bu nedenle, alt düğümler içerebilir. Ancak <xref:System.Xml.Linq.XDocument> nesneleri yalnızca bir alt <xref:System.Xml.Linq.XElement> düğümüne sahip olabilir. Bu, bir XML belgesinde yalnızca bir kök öğe olabilecek XML standardını yansıtır.  
  
## <a name="components-of-xdocument"></a>XDocument bileşenleri  
 <xref:System.Xml.Linq.XDocument>, aşağıdaki öğeleri içerebilir:  
  
- Bir <xref:System.Xml.Linq.XDeclaration> nesnesi. <xref:System.Xml.Linq.XDeclaration> bir XML bildiriminin ilgili parçalarını belirtmenizi sağlar: XML sürümü, belgenin kodlaması ve XML belgesinin tek başına olup olmadığı.  
  
- Bir <xref:System.Xml.Linq.XElement> nesnesi. Bu, XML belgesinin kök düğümüdür.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesne. Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesne. Yorumlar, kök öğesi için eşdüzey olacak. <xref:System.Xml.Linq.XComment> nesnesi, bir XML belgesinin bir açıklama ile başlaması için geçerli olmadığından listedeki ilk bağımsız değişken olamaz.  
  
- DTD için bir <xref:System.Xml.Linq.XDocumentType>.  
  
 Bir <xref:System.Xml.Linq.XDocument>seri hale geldiğinde, `XDocument.Declaration` `null`olsa bile, yazıcının `Writer.Settings.OmitXmlDeclaration` (varsayılan) `false` olarak ayarlanmış olması durumunda çıktıda bir XML bildirimi olur.  
  
 Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürümü "1,0" olarak ayarlar ve kodlamayı "UTF-8" olarak ayarlar.  
  
## <a name="using-xelement-without-xdocument"></a>XDocument olmadan XElement kullanma  
 Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XElement> sınıfı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimindeki ana sınıftır. Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez. <xref:System.Xml.Linq.XElement> sınıfını kullanarak bir XML ağacı oluşturabilir, buna başka XML ağaçları ekleyebilir, XML ağacını değiştirebilir ve kaydedebilirsiniz.  
  
## <a name="using-xdocument"></a>XDocument kullanma  
 <xref:System.Xml.Linq.XDocument>oluşturmak için, <xref:System.Xml.Linq.XElement> nesneleri oluşturmak için yaptığınız gibi işlevsel oluşturma kullanın.  
  
 Aşağıdaki kod <xref:System.Xml.Linq.XDocument> nesnesi ve ilişkili içerilen nesneleri oluşturur.  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 Test. xml dosyasını incelediğinizde aşağıdaki çıktıyı alırsınız:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

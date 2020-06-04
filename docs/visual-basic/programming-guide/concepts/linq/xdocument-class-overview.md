---
title: XDocument Sınıfına Genel Bakış
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 90c97349006407b2eca861be31080ec17901fa5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413238"
---
# <a name="xdocument-class-overview-visual-basic"></a>XDocument sınıfına genel bakış (Visual Basic)
Bu konu sınıfı tanıtır <xref:System.Xml.Linq.XDocument> .  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument sınıfına genel bakış  
 <xref:System.Xml.Linq.XDocument>Sınıfı, geçerli BIR XML belgesi için gereken bilgileri içerir. Buna bir XML bildirimi, işleme yönergeleri ve açıklamalar dahildir.  
  
 Yalnızca <xref:System.Xml.Linq.XDocument> sınıf tarafından sunulan belirli işlevselliğe ihtiyacınız varsa nesneler oluşturmanız gerektiğini unutmayın <xref:System.Xml.Linq.XDocument> . Birçok durumda, doğrudan ile çalışabilirsiniz <xref:System.Xml.Linq.XElement> . İle doğrudan çalışmak <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.  
  
 <xref:System.Xml.Linq.XDocument>türetiliyor <xref:System.Xml.Linq.XContainer> . Bu nedenle, alt düğümler içerebilir. Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt düğüme sahip olabilir <xref:System.Xml.Linq.XElement> . Bu, bir XML belgesinde yalnızca bir kök öğe olabilecek XML standardını yansıtır.  
  
## <a name="components-of-xdocument"></a>XDocument bileşenleri  
 , <xref:System.Xml.Linq.XDocument> Aşağıdaki öğeleri içerebilir:  
  
- Bir <xref:System.Xml.Linq.XDeclaration> nesne. <xref:System.Xml.Linq.XDeclaration>XML bildiriminin ilgili parçalarını belirtmenizi sağlar: XML sürümü, belgenin kodlaması ve XML belgesinin tek başına olup olmadığı.  
  
- Bir <xref:System.Xml.Linq.XElement> nesne. Bu, XML belgesinin kök düğümüdür.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesne. Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesne. Yorumlar, kök öğesi için eşdüzey olacak. <xref:System.Xml.Linq.XComment>Nesne, BIR XML belgesinin bir açıklama ile başlaması için geçerli olmadığından, listedeki ilk bağımsız değişken olamaz.  
  
- <xref:System.Xml.Linq.XDocumentType>DTD için bir tane.  
  
 Bir seri hale getirmek istediğinizde,, <xref:System.Xml.Linq.XDocument> `XDocument.Declaration` `null` yazıcı olarak AYARLANDıYSA çıkış bir XML bildirimine sahip olacaktır `Writer.Settings.OmitXmlDeclaration` `false` (varsayılan).  
  
 Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürümü "1,0" olarak ayarlar ve kodlamayı "UTF-8" olarak ayarlar.  
  
## <a name="using-xelement-without-xdocument"></a>XDocument olmadan XElement kullanma  
 Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XElement> sınıfı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimindeki ana sınıftır. Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez. <xref:System.Xml.Linq.XElement>Sınıfını kullanarak BIR XML ağacı oluşturabilir, buna başka xml ağaçları ekleyebilir, xml ağacını değiştirebilir ve kaydedebilirsiniz.  
  
## <a name="using-xdocument"></a>XDocument kullanma  
 Oluşturmak için <xref:System.Xml.Linq.XDocument> , nesneleri oluşturmak için yaptığınız gibi işlevsel oluşturma kullanın <xref:System.Xml.Linq.XElement> .  
  
 Aşağıdaki kod bir <xref:System.Xml.Linq.XDocument> nesne ve ilişkili içerilen nesneleri oluşturur.  
  
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

- [LINQ to XML programlamaya genel bakış (Visual Basic)](linq-to-xml-programming-overview.md)

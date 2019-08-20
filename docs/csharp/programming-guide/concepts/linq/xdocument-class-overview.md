---
title: XDocument sınıfına genel bakışC#()
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590848"
---
# <a name="xdocument-class-overview-c"></a>XDocument sınıfına genel bakışC#()
Bu konu <xref:System.Xml.Linq.XDocument> sınıfı tanıtır.  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument sınıfına genel bakış  
 Sınıfı <xref:System.Xml.Linq.XDocument> , geçerli bir XML belgesi için gereken bilgileri içerir. Buna bir XML bildirimi, işleme yönergeleri ve açıklamalar dahildir.  
  
 Yalnızca <xref:System.Xml.Linq.XDocument> sınıf<xref:System.Xml.Linq.XDocument> tarafından sunulan belirli işlevselliğe ihtiyacınız varsa nesneler oluşturmanız gerektiğini unutmayın. Birçok durumda, doğrudan ile <xref:System.Xml.Linq.XElement>çalışabilirsiniz. İle <xref:System.Xml.Linq.XElement> doğrudan çalışmak daha basit bir programlama modelidir.  
  
 <xref:System.Xml.Linq.XDocument>türetiliyor <xref:System.Xml.Linq.XContainer>. Bu nedenle, alt düğümler içerebilir. Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt <xref:System.Xml.Linq.XElement> düğüme sahip olabilir. Bu, bir XML belgesinde yalnızca bir kök öğe olabilecek XML standardını yansıtır.  
  
## <a name="components-of-xdocument"></a>XDocument bileşenleri  
 <xref:System.Xml.Linq.XDocument> , Aşağıdaki öğeleri içerebilir:  
  
- Bir <xref:System.Xml.Linq.XDeclaration> nesne. <xref:System.Xml.Linq.XDeclaration>XML bildiriminin ilgili parçalarını belirtmenizi sağlar: XML sürümü, belgenin kodlaması ve XML belgesinin tek başına olup olmadığı.  
  
- Bir <xref:System.Xml.Linq.XElement> nesne. Bu, XML belgesinin kök düğümüdür.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesne. Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesne. Yorumlar, kök öğesi için eşdüzey olacak. <xref:System.Xml.Linq.XComment> Nesne, bir XML belgesinin bir açıklama ile başlaması için geçerli olmadığından, listedeki ilk bağımsız değişken olamaz.  
  
- DTD <xref:System.Xml.Linq.XDocumentType> için bir tane.  
  
 Bir <xref:System.Xml.Linq.XDocument> `Writer.Settings.OmitXmlDeclaration` `false` seri hale getirmek istediğinizde,, yazıcı olarak ayarlandıysa çıkış bir XML bildirimine sahip olacaktır (varsayılan). `XDocument.Declaration` `null`  
  
 Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürümü "1,0" olarak ayarlar ve kodlamayı "UTF-8" olarak ayarlar.  
  
## <a name="using-xelement-without-xdocument"></a>XDocument olmadan XElement kullanma  
 Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XElement> sınıfı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimindeki ana sınıftır. Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez. <xref:System.Xml.Linq.XElement> Sınıfını kullanarak bir XML ağacı oluşturabilir, buna başka xml ağaçları ekleyebilir, xml ağacını değiştirebilir ve kaydedebilirsiniz.  
  
## <a name="using-xdocument"></a>XDocument kullanma  
 Oluşturmak <xref:System.Xml.Linq.XDocument>için, nesneleri oluşturmak <xref:System.Xml.Linq.XElement> için yaptığınız gibi işlevsel oluşturma kullanın.  
  
 Aşağıdaki kod bir <xref:System.Xml.Linq.XDocument> nesne ve ilişkili içerilen nesneleri oluşturur.  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
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

- [LINQ to XML programlamaya genel bakışC#()](./linq-to-xml-overview.md)

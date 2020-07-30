---
title: XDocument sınıfına genel bakış (C#)
description: C# ' deki XDocument sınıfı, XML bildirimi, işleme yönergeleri ve açıklamalar dahil olmak üzere geçerli bir XML belgesi için gereken bilgileri Içerir.
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: 6d522cef25e99e4a5ea54e644855c8dfa7a05f4a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302197"
---
# <a name="xdocument-class-overview-c"></a>XDocument sınıfına genel bakış (C#)
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
  
 Dosyayı test.xml incelediğinizde aşağıdaki çıktıyı alırsınız:  
  
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

- [LINQ to XML programlamaya genel bakış (C#)](./linq-to-xml-overview.md)

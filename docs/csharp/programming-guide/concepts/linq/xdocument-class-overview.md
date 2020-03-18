---
title: XDocument Sınıf Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590848"
---
# <a name="xdocument-class-overview-c"></a>XDocument Sınıf Genel Bakış (C#)
Bu konu <xref:System.Xml.Linq.XDocument> sınıf tanıttı.  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument sınıfına genel bakış  
 Sınıf, <xref:System.Xml.Linq.XDocument> geçerli bir XML belgesi için gerekli bilgileri içerir. Buna bir XML bildirimi, işleme yönergeleri ve açıklamalar dahildir.  
  
 Yalnızca <xref:System.Xml.Linq.XDocument> sınıf tarafından sağlanan <xref:System.Xml.Linq.XDocument> belirli işlevselliği gerekiyorsa nesneler oluşturmanız gerektiğini unutmayın. Birçok durumda, doğrudan . <xref:System.Xml.Linq.XElement> Doğrudan çalışmak <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.  
  
 <xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XContainer>türetilmiştir. Bu nedenle, alt düğümleri içerebilir. Ancak, <xref:System.Xml.Linq.XDocument> nesnelerin yalnızca bir <xref:System.Xml.Linq.XElement> alt düğüm olabilir. Bu, bir XML belgesinde yalnızca bir kök öğesi olabileceği yönündeki XML standardını yansıtır.  
  
## <a name="components-of-xdocument"></a>XDocument bileşenleri  
 An <xref:System.Xml.Linq.XDocument> aşağıdaki öğeleri içerebilir:  
  
- Bir <xref:System.Xml.Linq.XDeclaration> nesne. <xref:System.Xml.Linq.XDeclaration>XML bildiriminin ilgili bölümlerini belirtmenizi sağlar: XML sürümü, belgenin kodlanması ve XML belgesinin tek başına olup olmadığı.  
  
- Bir <xref:System.Xml.Linq.XElement> nesne. Bu, XML belgesinin kök düğümüdür.  
  
- Herhangi bir <xref:System.Xml.Linq.XProcessingInstruction> sayıda nesne. İşleme yönergesi, bilgileri XML'i işleyen bir uygulamaya iletir.  
  
- Herhangi bir <xref:System.Xml.Linq.XComment> sayıda nesne. Yorumlar kök öğesine kardeş olacaktır. Bir <xref:System.Xml.Linq.XComment> XML belgesinin bir açıklamayla başlaması geçerli olmadığından, nesne listedeki ilk bağımsız değişken olamaz.  
  
- DTD için bir tane. <xref:System.Xml.Linq.XDocumentType>  
  
 Bir <xref:System.Xml.Linq.XDocument>, olsa `XDocument.Declaration` `null`bile, yazar `Writer.Settings.OmitXmlDeclaration` `false` (varsayılan) olarak ayarlanmışsa çıktıbir XML bildirimi olacaktır serialize zaman.  
  
 Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürümü "1.0" olarak ayarlar ve kodlamayı "utf-8" olarak ayarlar.  
  
## <a name="using-xelement-without-xdocument"></a>XDocument olmadan XElement kullanma  
 Daha önce de belirtildiği <xref:System.Xml.Linq.XElement> gibi, sınıf [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabiriminde ana sınıftır. Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez. <xref:System.Xml.Linq.XElement> Sınıfı kullanarak, bir XML ağacı oluşturabilir, diğer XML ağaçları ekleyebilir, XML ağacını değiştirebilir ve kaydedebilirsiniz.  
  
## <a name="using-xdocument"></a>XDocument'ı Kullanma  
 Nesneleri oluşturmak <xref:System.Xml.Linq.XDocument>için yaptığınız gibi, işlevsel bir <xref:System.Xml.Linq.XElement> yapı oluşturmak için kullanın.  
  
 Aşağıdaki kod bir <xref:System.Xml.Linq.XDocument> nesne oluşturur ve ilişkili içerdiği nesneleri.  
  
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
  
 Dosya test.xml'i incelediğinizde, aşağıdaki çıktıyı alırsınız:  
  
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

- [LINQ - XML Programlamaya Genel Bakış (C#)](./linq-to-xml-overview.md)

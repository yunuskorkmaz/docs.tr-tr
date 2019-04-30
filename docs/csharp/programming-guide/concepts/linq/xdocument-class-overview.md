---
title: XDocument sınıfına genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: e3ef7d66cb9759bd71e69c1a0db3614a02f785b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680645"
---
# <a name="xdocument-class-overview-c"></a>XDocument sınıfına genel bakış (C#)
Bu konu tanıtır <xref:System.Xml.Linq.XDocument> sınıfı.  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument sınıfına genel bakış  
 <xref:System.Xml.Linq.XDocument> Sınıfı, geçerli bir XML belgesi için gereken bilgileri içerir. Bu işleme yönergeleri ve açıklamaları, bir XML bildirimi içerir.  
  
 Yalnızca oluşturmak zorunda Not <xref:System.Xml.Linq.XDocument> tarafından sağlanan belirli işlevleri gerektirip gerektirmediğini nesneleri <xref:System.Xml.Linq.XDocument> sınıfı. Çoğu durumda, doğrudan çalışabileceğiniz <xref:System.Xml.Linq.XElement>. Doğrudan çalışma <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.  
  
 <xref:System.Xml.Linq.XDocument> öğesinden türetilen <xref:System.Xml.Linq.XContainer>. Bu nedenle, bu alt düğümler içerebilir. Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt sahip <xref:System.Xml.Linq.XElement> düğümü. Bu, bir XML belgesinde yalnızca bir kök öğe olabileceğini XML standardı yansıtır.  
  
## <a name="components-of-xdocument"></a>XDocument bileşenleri  
 Bir <xref:System.Xml.Linq.XDocument> aşağıdaki öğeleri içerebilir:  
  
- Bir <xref:System.Xml.Linq.XDeclaration> nesne. <xref:System.Xml.Linq.XDeclaration> bir XML bildirimi ilgili bölümleri belirtmenize olanak tanıyan: kodlama belgenin XML sürümü ve XML belge tek başına olup.  
  
- Bir <xref:System.Xml.Linq.XElement> nesne. Bu işlev, XML belgesi kök düğümüdür.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesneleri. Bir işlem yönergesi, XML işleme uygulamaya bilgi iletişim kurar.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesneleri. Açıklamalar, kök öğe kardeş olacaktır. <xref:System.Xml.Linq.XComment> Bir yorum ile başlatmak bir XML belgesi için geçerli olmadığından, nesne ilk bağımsız değişken listesinde olamaz.  
  
- Bir <xref:System.Xml.Linq.XDocumentType> DTD'nin için.  
  
 Serileştirmek ne zaman bir <xref:System.Xml.Linq.XDocument>bile `XDocument.Declaration` olduğu `null`, yazıcı çıkış XML bildirimi varsa `Writer.Settings.OmitXmlDeclaration` kümesine `false` (varsayılan).  
  
 Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ayarlar sürüm "1.0" ve "utf-8" kodlama ayarlar.  
  
## <a name="using-xelement-without-xdocument"></a>XElement XDocument olmadan kullanma  
 Daha önce belirtildiği gibi <xref:System.Xml.Linq.XElement> ana sınıfı içinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimi. Çoğu durumda, bir belge oluşturmak, uygulamanızın gerek yoktur. Kullanarak <xref:System.Xml.Linq.XElement> sınıfı, bir XML ağacı oluşturma, diğer XML ağaçlarını ekleyin, XML ağacı değiştirebilir ve kaydedebilirsiniz.  
  
## <a name="using-xdocument"></a>XDocument kullanma  
 Oluşturmak için bir <xref:System.Xml.Linq.XDocument>, oluşturmak için yaptığınız gibi işlev yapım kullanın <xref:System.Xml.Linq.XElement> nesneleri.  
  
 Aşağıdaki kod oluşturur bir <xref:System.Xml.Linq.XDocument> nesne ve onun ilişkili kapsanan nesneleri.  
  
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
  
 Dosya test.xml incelediğinizde, aşağıdaki çıkışı alırsınız:  
  
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

- [LINQ to XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

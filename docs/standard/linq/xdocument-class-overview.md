---
title: XDocument sınıfına genel bakış
description: LINQ to XML XDocument sınıfı, geçerli bir XML belgesi için gereken bilgileri içerir. Çoğu durumda, bir XDocument nesnesinin işlevselliğine gerek kalmaz ve bunun yerine bir XElement nesnesi kullanabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552925"
---
# <a name="xdocument-class-overview"></a>XDocument sınıfına genel bakış

<xref:System.Xml.Linq.XDocument>Sınıfı, BIR XML bildirimi, işleme yönergeleri ve açıklamalar içeren geçerli BIR XML belgesi için gereken bilgileri içerir.

Yalnızca <xref:System.Xml.Linq.XDocument> sınıf tarafından sunulan belirli işlevselliğe ihtiyacınız varsa nesneler oluşturmanız gerekir <xref:System.Xml.Linq.XDocument> . Birçok durumda, doğrudan ile çalışabilirsiniz <xref:System.Xml.Linq.XElement> . İle doğrudan çalışmak <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.

<xref:System.Xml.Linq.XDocument> öğesinden türetilir <xref:System.Xml.Linq.XContainer> , bu nedenle alt düğümler içerebilir. Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt düğüme sahip olabilir <xref:System.Xml.Linq.XElement> . Bu, bir XML belgesinde yalnızca bir kök öğe olabilecek XML standardını yansıtır.

## <a name="components-of-xdocument"></a>XDocument bileşenleri

, <xref:System.Xml.Linq.XDocument> Aşağıdaki öğeleri içerebilir:

- Bir <xref:System.Xml.Linq.XDeclaration> nesne. <xref:System.Xml.Linq.XDeclaration> XML bildiriminin ilgili parçalarını belirtmenizi sağlar: XML sürümü, belgenin kodlaması ve XML belgesinin tek başına olup olmadığı.
- Bir <xref:System.Xml.Linq.XElement> nesne. Bu nesne, XML belgesinin kök düğümüdür.
- Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesne. Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.
- Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesne. Yorumlar, kök öğesi için eşdüzey olacak. <xref:System.Xml.Linq.XComment>Nesne, BIR XML belgesinin bir açıklama ile başlaması için geçerli olmadığından, listedeki ilk bağımsız değişken olamaz.
- <xref:System.Xml.Linq.XDocumentType>DTD için bir tane.

Bir seri hale getirmek istediğinizde,, <xref:System.Xml.Linq.XDocument> `XDocument.Declaration` `null` yazıcı olarak AYARLANDıYSA çıkış bir XML bildirimine sahip olacaktır `Writer.Settings.OmitXmlDeclaration` `false` (varsayılan).

Varsayılan olarak, LINQ to XML sürümü "1,0" olarak ayarlar ve kodlamayı "UTF-8" olarak ayarlar.

## <a name="use-xelement-without-xdocument"></a>XDocument olmadan XElement kullanma

Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XElement> sınıfı LINQ to XML programlama arabirimindeki ana sınıftır. Çoğu durumda, uygulamanız bir belge oluşturmanızı gerektirmez. Sınıfını kullanarak şunları <xref:System.Xml.Linq.XElement> yapabilirsiniz:

- Bir XML ağacı oluşturun.
- Buna başka XML ağaçları ekleyin.
- XML ağacını değiştirin.
- Kaydedin.

## <a name="use-xdocument"></a>XDocument kullanma

Oluşturmak için <xref:System.Xml.Linq.XDocument> , nesneleri oluşturmak için yaptığınız gibi işlevsel oluşturma kullanın <xref:System.Xml.Linq.XElement> .

Aşağıdaki örnek bir <xref:System.Xml.Linq.XDocument> nesnesi ve ilişkili içerilen nesnelerini oluşturur.

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

Örnek bu çıktıyı test.xml üretir:

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

- [LINQ to XML genel bakış](linq-xml-overview.md)

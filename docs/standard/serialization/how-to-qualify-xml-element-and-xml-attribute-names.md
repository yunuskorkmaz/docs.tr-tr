---
title: XML öğesi ve XML öznitelik adlarını nitelendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: db0795dd83cc96aba49dd435c875e98a9a6c18cb
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159877"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a>XML öğesi ve XML öznitelik adlarını nitelendirme

<xref:System.Xml.Serialization.XmlSerializerNamespaces> sınıfının örneklerinin içerdiği XML ad alanları, [XML 'de ad alanları](https://www.w3.org/TR/REC-xml-names/)adı verilen world WIDE Web KONSORSIYUMU (W3C) belirtimine uymalıdır.

XML ad alanları, XML öğelerinin ve XML belgelerinin XML özniteliklerinin adlarını nitelemek için bir yöntem sağlar. Tam adı bir önek ve virgül ile ayrılmış bir yerel ad oluşur. Önek yalnızca bir yer tutucu olarak işlev görür; bir ad alanı belirten bir URI ile eşleşir. Evrensel yönetilen URI ad alanı ve yerel adı birleşimi evrensel benzersiz olması garanti bir ad oluşturur.

Öğesinin bir örneğini oluşturarak `XmlSerializerNamespaces` ve ad alanı çiftleri nesnesine ekleniyor, XML belgesinde kullanılan öneklerini belirtebilirsiniz.

## <a name="to-create-qualified-names-in-an-xml-document"></a>Bir XML belgesinde tam adları oluşturmak için

1. Öğesinin bir örneğini oluşturur `XmlSerializerNamespaces` sınıfı.

2. Tüm öneklerine ve ad alanı çiftleri için Ekle `XmlSerializerNamespaces`.

3. <xref:System.Xml.Serialization.XmlSerializer> bir XML belgesine seri hale getirmek için gereken her üyeye veya sınıfa uygun `System.Xml.Serialization` özniteliğini uygulayın.

    Kullanılabilir öznitelikler şunlardır: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>ve <xref:System.Xml.Serialization.XmlTypeAttribute>.

4. Her bir özniteliğin `Namespace` özelliğini `XmlSerializerNamespaces`ad alanı değerlerinden birine ayarlayın.

5. Geçiş `XmlSerializerNamespaces` için `Serialize` yöntemi `XmlSerializer`.

## <a name="example"></a>Örnek

Aşağıdaki örnek, oluşturur bir `XmlSerializerNamespaces`, ve iki önek ve ad alanı çiftleri nesneye ekler. Kod oluşturur bir `XmlSerializer` örneğini serileştirmek için kullanılan `Books` sınıfı. Kod çağrıları `Serialize` yöntemiyle `XmlSerializerNamespaces`, önekli ad alanları içeren XML izin verme.

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Module Program

    Public Sub Main()
        SerializeObject("XmlNamespaces.xml")
    End Sub

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Module

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book
    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Program
{
    public static void Main()
    {
        SerializeObject("XmlNamespaces.xml");
    }

    public static void SerializeObject(string filename)
    {
        var mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        var myNamespaces = new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        var myBook = new Book();
        myBook.TITLE = "A Book Title";
        var myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        var myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter, myBooks, myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}

public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSerializer>
- [XML Şema Tanımı Aracı ve XML Serileştirme](the-xml-schema-definition-tool-and-xml-serialization.md)
- [XML Serileştirmeye Giriş](introducing-xml-serialization.md)
- [XmlSerializer sınıfı](xref:System.Xml.Serialization.XmlSerializer)
- [XML Serileştirmeyi Denetleyen Öznitelikler](attributes-that-control-xml-serialization.md)
- [Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)

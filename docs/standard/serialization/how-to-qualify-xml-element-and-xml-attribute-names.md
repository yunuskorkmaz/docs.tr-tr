---
title: 'Nasıl yapılır: XML öğesi ve XML öznitelik adlarını niteleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 1f79caf6ff295d793c615b17d387cdd165e440e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353094"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="4aef0-102">Nasıl yapılır: XML öğesi ve XML öznitelik adlarını niteleme</span><span class="sxs-lookup"><span data-stu-id="4aef0-102">How to: Qualify XML Element and XML Attribute Names</span></span>

<span data-ttu-id="4aef0-103"><xref:System.Xml.Serialization.XmlSerializerNamespaces> sınıfının örneklerinin içerdiği XML ad alanları, [XML 'de ad alanları](https://www.w3.org/TR/REC-xml-names/)adı verilen world WIDE Web KONSORSIYUMU (W3C) belirtimine uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="4aef0-103">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="4aef0-104">XML ad alanları, XML öğelerinin ve XML belgelerinin XML özniteliklerinin adlarını nitelemek için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="4aef0-104">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="4aef0-105">Tam adı bir önek ve virgül ile ayrılmış bir yerel ad oluşur.</span><span class="sxs-lookup"><span data-stu-id="4aef0-105">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="4aef0-106">Önek yalnızca bir yer tutucu olarak işlev görür; bir ad alanı belirten bir URI ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="4aef0-106">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="4aef0-107">Evrensel yönetilen URI ad alanı ve yerel adı birleşimi evrensel benzersiz olması garanti bir ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aef0-107">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="4aef0-108">Öğesinin bir örneğini oluşturarak `XmlSerializerNamespaces` ve ad alanı çiftleri nesnesine ekleniyor, XML belgesinde kullanılan öneklerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aef0-108">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="4aef0-109">Bir XML belgesinde tam adları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4aef0-109">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="4aef0-110">Öğesinin bir örneğini oluşturur `XmlSerializerNamespaces` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4aef0-110">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="4aef0-111">Tüm öneklerine ve ad alanı çiftleri için Ekle `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="4aef0-111">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="4aef0-112"><xref:System.Xml.Serialization.XmlSerializer> bir XML belgesine seri hale getirmek için gereken her üyeye veya sınıfa uygun `System.Xml.Serialization` özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4aef0-112">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

    <span data-ttu-id="4aef0-113">Kullanılabilir öznitelikler şunlardır: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>ve <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4aef0-113">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="4aef0-114">Her bir özniteliğin `Namespace` özelliğini `XmlSerializerNamespaces`ad alanı değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4aef0-114">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="4aef0-115">Geçiş `XmlSerializerNamespaces` için `Serialize` yöntemi `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="4aef0-115">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="4aef0-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4aef0-116">Example</span></span>

<span data-ttu-id="4aef0-117">Aşağıdaki örnek, oluşturur bir `XmlSerializerNamespaces`, ve iki önek ve ad alanı çiftleri nesneye ekler.</span><span class="sxs-lookup"><span data-stu-id="4aef0-117">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="4aef0-118">Kod oluşturur bir `XmlSerializer` örneğini serileştirmek için kullanılan `Books` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4aef0-118">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="4aef0-119">Kod çağrıları `Serialize` yöntemiyle `XmlSerializerNamespaces`, önekli ad alanları içeren XML izin verme.</span><span class="sxs-lookup"><span data-stu-id="4aef0-119">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

<!-- TODO: THE FOLLOWING VB SNIPPET ISN'T CORRECT!! -->
```vb
Option Explicit
public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}

Option Strict

Imports System
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Class Run

    Public Shared Sub Main()
        Dim test As New Run()
        test.SerializeObject("XmlNamespaces.xml")
    End Sub 'Main

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
End Class

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class 'Books

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
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _
        price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Run
{
    public static void Main()
    {
        Run test = new Run();
        test.SerializeObject("XmlNamespaces.xml");
    }
    public void SerializeObject(string filename)
    {
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        XmlSerializerNamespaces myNamespaces =
        new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        Book myBook = new Book();
        myBook.TITLE = "A Book Title";
        Price myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        Books myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);
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
```

## <a name="see-also"></a><span data-ttu-id="4aef0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aef0-120">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="4aef0-121">XML Şema Tanımı Aracı ve XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="4aef0-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="4aef0-122">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="4aef0-122">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="4aef0-123">XmlSerializer sınıfı</span><span class="sxs-lookup"><span data-stu-id="4aef0-123">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="4aef0-124">XML Serileştirmeyi Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4aef0-124">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="4aef0-125">Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme</span><span class="sxs-lookup"><span data-stu-id="4aef0-125">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="4aef0-126">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="4aef0-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="4aef0-127">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="4aef0-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)

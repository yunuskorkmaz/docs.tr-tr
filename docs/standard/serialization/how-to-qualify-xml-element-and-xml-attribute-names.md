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
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="89e34-102">XML öğesi ve XML öznitelik adlarını nitelendirme</span><span class="sxs-lookup"><span data-stu-id="89e34-102">How to qualify XML element and XML attribute names</span></span>

<span data-ttu-id="89e34-103"><xref:System.Xml.Serialization.XmlSerializerNamespaces> Sınıfının ÖRNEKLERININ içerdiği xml ad ALANLARı, [XML 'de ad alanları](https://www.w3.org/TR/REC-xml-names/)adı verilen World Wide Web Konsorsiyumu (W3C) belirtimine uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="89e34-103">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="89e34-104">XML ad alanları, XML öğelerinin ve XML belgelerinin XML özniteliklerinin adlarını nitelemek için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="89e34-104">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="89e34-105">Tam adı bir önek ve virgül ile ayrılmış bir yerel ad oluşur.</span><span class="sxs-lookup"><span data-stu-id="89e34-105">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="89e34-106">Önek yalnızca bir yer tutucu olarak işlev görür; bir ad alanı belirten bir URI ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="89e34-106">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="89e34-107">Evrensel yönetilen URI ad alanı ve yerel adı birleşimi evrensel benzersiz olması garanti bir ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89e34-107">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="89e34-108">Öğesinin bir örneğini oluşturarak `XmlSerializerNamespaces` ve ad alanı çiftleri nesnesine ekleniyor, XML belgesinde kullanılan öneklerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89e34-108">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="89e34-109">Bir XML belgesinde tam adları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="89e34-109">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="89e34-110">Öğesinin bir örneğini oluşturur `XmlSerializerNamespaces` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="89e34-110">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="89e34-111">Tüm öneklerine ve ad alanı çiftleri için Ekle `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="89e34-111">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="89e34-112">Bir XML belgesine `System.Xml.Serialization` seri hale getirilecek her üyeye veya sınıfa <xref:System.Xml.Serialization.XmlSerializer> uygun özniteliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="89e34-112">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

    <span data-ttu-id="89e34-113">Kullanılabilir <xref:System.Xml.Serialization.XmlAnyElementAttribute>öznitelikler şunlardır:, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, ve. <xref:System.Xml.Serialization.XmlTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="89e34-113">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="89e34-114">Her bir `Namespace` özniteliğin özelliğini öğesinden ad alanı değerlerinden birine ayarlayın `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="89e34-114">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="89e34-115">Geçiş `XmlSerializerNamespaces` için `Serialize` yöntemi `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="89e34-115">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="89e34-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="89e34-116">Example</span></span>

<span data-ttu-id="89e34-117">Aşağıdaki örnek, oluşturur bir `XmlSerializerNamespaces`, ve iki önek ve ad alanı çiftleri nesneye ekler.</span><span class="sxs-lookup"><span data-stu-id="89e34-117">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="89e34-118">Kod oluşturur bir `XmlSerializer` örneğini serileştirmek için kullanılan `Books` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="89e34-118">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="89e34-119">Kod çağrıları `Serialize` yöntemiyle `XmlSerializerNamespaces`, önekli ad alanları içeren XML izin verme.</span><span class="sxs-lookup"><span data-stu-id="89e34-119">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="89e34-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89e34-120">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="89e34-121">XML Şema Tanımı Aracı ve XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="89e34-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="89e34-122">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="89e34-122">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="89e34-123">XmlSerializer sınıfı</span><span class="sxs-lookup"><span data-stu-id="89e34-123">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="89e34-124">XML serileştirme denetleyen öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89e34-124">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="89e34-125">Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme</span><span class="sxs-lookup"><span data-stu-id="89e34-125">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="89e34-126">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="89e34-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="89e34-127">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="89e34-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)

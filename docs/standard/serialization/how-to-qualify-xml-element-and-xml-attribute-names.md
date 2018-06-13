---
title: 'Nasıl yapılır: XML öğesi ve XML öznitelik adları nitelemek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 95b99bb093282352b6f8e2b9f04cba773e64259d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585720"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="e89f3-102">Nasıl yapılır: XML öğesi ve XML öznitelik adları nitelemek</span><span class="sxs-lookup"><span data-stu-id="e89f3-102">How to: Qualify XML Element and XML Attribute Names</span></span>
[<span data-ttu-id="e89f3-103">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="e89f3-103">Code Example</span></span>](#cpconworkingwithxmlnamespacesanchor1)  
  
 <span data-ttu-id="e89f3-104">XML ad alanları örneklerini tarafından bulunan <xref:System.Xml.Serialization.XmlSerializerNamespaces> sınıfı "Ad alanları XML." adlı World Wide Web Consortium (www.w3.org) belirtimine uyması gerekir</span><span class="sxs-lookup"><span data-stu-id="e89f3-104">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (www.w3.org) specification called "Namespaces in XML."</span></span>  
  
 <span data-ttu-id="e89f3-105">XML ad alanları nitelikli adlar XML öğeleri ve XML belgelerini XML öznitelikleri için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e89f3-105">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="e89f3-106">Tam adı bir önek ve virgül ile ayrılmış bir yerel ad oluşur.</span><span class="sxs-lookup"><span data-stu-id="e89f3-106">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="e89f3-107">Önek yalnızca bir yer tutucu olarak işlev görür; bir ad alanı belirten bir URI ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e89f3-107">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="e89f3-108">Evrensel yönetilen URI ad alanı ve yerel adı birleşimi evrensel benzersiz olması garanti bir ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e89f3-108">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>  
  
 <span data-ttu-id="e89f3-109">Öğesinin bir örneğini oluşturarak `XmlSerializerNamespaces` ve ad alanı çiftleri nesnesine ekleniyor, XML belgesinde kullanılan öneklerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e89f3-109">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>  
  
### <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="e89f3-110">Bir XML belgesinde tam adları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e89f3-110">To create qualified names in an XML document</span></span>  
  
1.  <span data-ttu-id="e89f3-111">Öğesinin bir örneğini oluşturur `XmlSerializerNamespaces` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e89f3-111">Create an instance of the `XmlSerializerNamespaces` class.</span></span>  
  
2.  <span data-ttu-id="e89f3-112">Tüm öneklerine ve ad alanı çiftleri için Ekle `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="e89f3-112">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>  
  
3.  <span data-ttu-id="e89f3-113">Uygun uygulamak `System.Xml.Serialization` özniteliği her üyesine ya da bu sınıf <xref:System.Xml.Serialization.XmlSerializer> XML belgesine seri hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="e89f3-113">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>  
  
     <span data-ttu-id="e89f3-114">Kullanılabilir öznitelikleri: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, ve <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e89f3-114">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>  
  
4.  <span data-ttu-id="e89f3-115">Ayarlama `Namespace` her özniteliği özelliğini ad alanı değerlerinden birine `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="e89f3-115">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>  
  
5.  <span data-ttu-id="e89f3-116">Geçiş `XmlSerializerNamespaces` için `Serialize` yöntemi `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="e89f3-116">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e89f3-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e89f3-117">Example</span></span>  
 <span data-ttu-id="e89f3-118">Aşağıdaki örnek, oluşturur bir `XmlSerializerNamespaces`, ve iki önek ve ad alanı çiftleri nesneye ekler.</span><span class="sxs-lookup"><span data-stu-id="e89f3-118">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="e89f3-119">Kod oluşturur bir `XmlSerializer` örneğini serileştirmek için kullanılan `Books` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e89f3-119">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="e89f3-120">Kod çağrıları `Serialize` yöntemiyle `XmlSerializerNamespaces`, önekli ad alanları içeren XML izin verme.</span><span class="sxs-lookup"><span data-stu-id="e89f3-120">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e89f3-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e89f3-121">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="e89f3-122">XML Şema Tanımı Aracı ve XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e89f3-122">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 [<span data-ttu-id="e89f3-123">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="e89f3-123">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="e89f3-124">XmlSerializer sınıfı</span><span class="sxs-lookup"><span data-stu-id="e89f3-124">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)  
 [<span data-ttu-id="e89f3-125">XML Serileştirmeyi Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e89f3-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [<span data-ttu-id="e89f3-126">Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme</span><span class="sxs-lookup"><span data-stu-id="e89f3-126">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [<span data-ttu-id="e89f3-127">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e89f3-127">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="e89f3-128">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="e89f3-128">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

---
title: 'Nasıl yapılır: XML Stream için alternatif öğe adı belirtin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
ms.openlocfilehash: 8cb6a66f9fc7a67ae99574e783fd889537b9b11a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131730"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a><span data-ttu-id="8c59c-102">Nasıl yapılır: XML Stream için alternatif öğe adı belirtin</span><span class="sxs-lookup"><span data-stu-id="8c59c-102">How to: Specify an Alternate Element Name for an XML Stream</span></span>
[<span data-ttu-id="8c59c-103">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="8c59c-103">Code Example</span></span>](#cpconoverridingserializationofclasseswithxmlattributeoverridesclassanchor1)  
  
 <span data-ttu-id="8c59c-104">Kullanarak [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), aynı sınıfları kümesi ile birden fazla XML akışı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c59c-104">Using the [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), you can generate more than one XML stream with the same set of classes.</span></span> <span data-ttu-id="8c59c-105">İki farklı XML Web Hizmetleri aynı temel bilgileri, yalnızca küçük farkları gerektirdiğinden bunu isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c59c-105">You might want to do this because two different XML Web services require the same basic information, with only slight differences.</span></span> <span data-ttu-id="8c59c-106">Örneğin, siparişler books için işlemi iki XML Web Hizmetleri varsayalım ve bu nedenle her ikisi de ISBN numaraları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8c59c-106">For example, imagine two XML Web services that process orders for books, and thus both require ISBN numbers.</span></span> <span data-ttu-id="8c59c-107">Bir hizmet etiketi kullanır \<ISBN > Etiket ikinci kullanırken \<Bookıd >.</span><span class="sxs-lookup"><span data-stu-id="8c59c-107">One service uses the tag \<ISBN> while the second uses the tag \<BookID>.</span></span> <span data-ttu-id="8c59c-108">Adlı bir sınıf sahip `Book` adında bir alan içeren `ISBN`.</span><span class="sxs-lookup"><span data-stu-id="8c59c-108">You have a class named `Book` that contains a field named `ISBN`.</span></span> <span data-ttu-id="8c59c-109">Örneği, `Book` sınıf serileştirildiği, varsayılan olarak, üye adı (ISBN) etiket öğe adı kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="8c59c-109">When an instance of the `Book` class is serialized, it will, by default, use the member name (ISBN) as the tag element name.</span></span> <span data-ttu-id="8c59c-110">İlk XML Web hizmeti için beklendiği gibi budur.</span><span class="sxs-lookup"><span data-stu-id="8c59c-110">For the first XML Web service, this is as expected.</span></span> <span data-ttu-id="8c59c-111">Ancak etiketin öğe adı böylece XML akışı ikinci XML Web hizmetine göndermek için serileştirme geçersiz kılmanız gerekir `BookID`.</span><span class="sxs-lookup"><span data-stu-id="8c59c-111">But to send the XML stream to the second XML Web service, you must override the serialization so that the tag's element name is `BookID`.</span></span>  
  
### <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a><span data-ttu-id="8c59c-112">Bir alternatif öğe adı bir XML akışı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8c59c-112">To create an XML stream with an alternate element name</span></span>  
  
1.  <span data-ttu-id="8c59c-113">Öğesinin bir örneğini oluşturur <xref:System.Xml.Serialization.XmlElementAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c59c-113">Create an instance of the <xref:System.Xml.Serialization.XmlElementAttribute> class.</span></span>  
  
2.  <span data-ttu-id="8c59c-114">Ayarlama <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> , <xref:System.Xml.Serialization.XmlElementAttribute> "BookID" için.</span><span class="sxs-lookup"><span data-stu-id="8c59c-114">Set the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> of the <xref:System.Xml.Serialization.XmlElementAttribute> to "BookID".</span></span>  
  
3.  <span data-ttu-id="8c59c-115">Öğesinin bir örneğini oluşturur <xref:System.Xml.Serialization.XmlAttributes> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c59c-115">Create an instance of the <xref:System.Xml.Serialization.XmlAttributes> class.</span></span>  
  
4.  <span data-ttu-id="8c59c-116">Ekle `XmlElementAttribute` nesnesini aracılığıyla erişilebilen koleksiyonuna <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> özelliği <xref:System.Xml.Serialization.XmlAttributes> .</span><span class="sxs-lookup"><span data-stu-id="8c59c-116">Add the `XmlElementAttribute` object to the collection accessed through the <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> property of <xref:System.Xml.Serialization.XmlAttributes> .</span></span>  
  
5.  <span data-ttu-id="8c59c-117">Öğesinin bir örneğini oluşturur <xref:System.Xml.Serialization.XmlAttributeOverrides> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c59c-117">Create an instance of the <xref:System.Xml.Serialization.XmlAttributeOverrides> class.</span></span>  
  
6.  <span data-ttu-id="8c59c-118">Ekle `XmlAttributes` için <xref:System.Xml.Serialization.XmlAttributeOverrides>, geçersiz kılmak için nesne türü ve kılınmasını üyenin adını geçirerek.</span><span class="sxs-lookup"><span data-stu-id="8c59c-118">Add the `XmlAttributes` to the <xref:System.Xml.Serialization.XmlAttributeOverrides>, passing the type of the object to override and the name of the member being overridden.</span></span>  
  
7.  <span data-ttu-id="8c59c-119">Öğesinin bir örneğini oluşturur `XmlSerializer` ile `XmlAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="8c59c-119">Create an instance of the `XmlSerializer` class with `XmlAttributeOverrides`.</span></span>  
  
8.  <span data-ttu-id="8c59c-120">Öğesinin bir örneğini oluşturur `Book` sınıfının ve serileştirmek veya bu seri.</span><span class="sxs-lookup"><span data-stu-id="8c59c-120">Create an instance of the `Book` class, and serialize or deserialize it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c59c-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c59c-121">Example</span></span>  
  
```vb  
Public Class SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public class SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 <span data-ttu-id="8c59c-122">XML akışı aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="8c59c-122">The XML stream might resemble the following.</span></span>  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c59c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c59c-123">See also</span></span>

- <xref:System.Xml.Serialization.XmlElementAttribute>  
- <xref:System.Xml.Serialization.XmlAttributes>  
- <xref:System.Xml.Serialization.XmlAttributeOverrides>  
- [<span data-ttu-id="8c59c-124">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c59c-124">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [<span data-ttu-id="8c59c-125">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="8c59c-125">XmlSerializer</span></span>](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)  
- [<span data-ttu-id="8c59c-126">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="8c59c-126">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [<span data-ttu-id="8c59c-127">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="8c59c-127">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [<span data-ttu-id="8c59c-128">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="8c59c-128">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

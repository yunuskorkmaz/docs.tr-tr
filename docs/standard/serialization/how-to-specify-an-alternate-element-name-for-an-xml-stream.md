---
title: 'Nasıl yapılır: Bir XML Stream için alternatif öğe adı belirtin'
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
ms.openlocfilehash: f2dd56111bbc0ace76c2b71d208f1b753a2119b8
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415097"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a>Nasıl yapılır: Bir XML Stream için alternatif öğe adı belirtin
  
Kullanarak [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), aynı sınıfları kümesi ile birden fazla XML akışı oluşturabilirsiniz. İki farklı XML Web Hizmetleri aynı temel bilgileri, yalnızca küçük farkları gerektirdiğinden bunu isteyebilirsiniz. Örneğin, siparişler books için işlemi iki XML Web Hizmetleri varsayalım ve bu nedenle her ikisi de ISBN numaraları gerektirir. Bir hizmet etiketi kullanır \<ISBN > Etiket ikinci kullanırken \<Bookıd >. Adlı bir sınıf sahip `Book` adında bir alan içeren `ISBN`. Örneği, `Book` sınıf serileştirildiği, varsayılan olarak, üye adı (ISBN) etiket öğe adı kullanacağız. İlk XML Web hizmeti için beklendiği gibi budur. Ancak etiketin öğe adı böylece XML akışı ikinci XML Web hizmetine göndermek için serileştirme geçersiz kılmanız gerekir `BookID`.  
  
## <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a>Bir alternatif öğe adı bir XML akışı oluşturmak için  
  
1.  Öğesinin bir örneğini oluşturur <xref:System.Xml.Serialization.XmlElementAttribute> sınıfı.  
  
2.  Ayarlama <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> , <xref:System.Xml.Serialization.XmlElementAttribute> "BookID" için.  
  
3.  Öğesinin bir örneğini oluşturur <xref:System.Xml.Serialization.XmlAttributes> sınıfı.  
  
4.  Ekle `XmlElementAttribute` nesnesini aracılığıyla erişilebilen koleksiyonuna <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> özelliği <xref:System.Xml.Serialization.XmlAttributes> .  
  
5.  Öğesinin bir örneğini oluşturur <xref:System.Xml.Serialization.XmlAttributeOverrides> sınıfı.  
  
6.  Ekle `XmlAttributes` için <xref:System.Xml.Serialization.XmlAttributeOverrides>, geçersiz kılmak için nesne türü ve kılınmasını üyenin adını geçirerek.  
  
7.  Öğesinin bir örneğini oluşturur `XmlSerializer` ile `XmlAttributeOverrides`.  
  
8.  Öğesinin bir örneğini oluşturur `Book` sınıfının ve serileştirmek veya bu seri.  
  
## <a name="example"></a>Örnek  
  
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
  
 XML akışı aşağıdakine benzer.  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlElementAttribute>  
- <xref:System.Xml.Serialization.XmlAttributes>  
- <xref:System.Xml.Serialization.XmlAttributeOverrides>  
- [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)  
- [Nasıl yapılır: Bir nesneyi serileştirmek](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [Nasıl yapılır: Bir nesneyi seri durumdan çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [Nasıl yapılır: Bir nesneyi seri durumdan çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

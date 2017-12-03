---
title: "Nasıl yapılır: bir XML akışı için bir diğer öğe adı belirtin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f52aeb8cdb2ed8af3e3f45a27ec5dadb6afd7de2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a>Nasıl yapılır: bir XML akışı için bir diğer öğe adı belirtin
[Kod örneği](#cpconoverridingserializationofclasseswithxmlattributeoverridesclassanchor1)  
  
 Kullanarak [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), birden fazla XML akışı sınıfların aynı kümesi oluşturabilirsiniz. İki farklı XML Web Hizmetleri aynı temel bilgileri, yalnızca küçük farkları gerektirdiğinden bunu isteyebilirsiniz. Örneğin, siparişler books için işlemi iki XML Web Hizmetleri varsayalım ve bu nedenle her ikisi de ISBN numaraları gerektirir. Bir hizmet etiket kullanır \<ISBN > etiketi ikinci kullanıyor, ancak \<BookID >. Adlı bir sınıf sahip `Book` adında bir alan içeren `ISBN`. Örneği, `Book` sınıf serileştirildiği, varsayılan olarak, üye adı (ISBN) etiket öğe adı kullanacağız. İlk XML Web hizmeti için beklendiği gibi budur. Ancak etiketin öğe adı böylece XML akışı ikinci XML Web hizmetine göndermek için seri hale getirme kılmalıdır `BookID`.  
  
### <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a>Bir diğer öğe adı ile bir XML akışı oluşturmak için  
  
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
  
 XML akışı şöyle olabilir.  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Serialization.XmlElementAttribute>  
 <xref:System.Xml.Serialization.XmlAttributes>  
 <xref:System.Xml.Serialization.XmlAttributeOverrides>  
 [XML ve SOAP seri hale getirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)  
 [Nasıl yapılır: bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [Nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

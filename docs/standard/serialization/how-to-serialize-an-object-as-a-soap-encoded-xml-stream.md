---
title: 'Nasıl yapılır: SOAP kodlu XML Stream olarak bir nesneyi serileştirmek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: cdfa2c8c7a27806873217495ac09f7f20e82b6bc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209309"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Nasıl yapılır: SOAP kodlu XML Stream olarak bir nesneyi serileştirmek
  
 XML, kullanarak bir SOAP ileti inşa edildiğinden <xref:System.Xml.Serialization.XmlSerializer> sınıfı sınıfları seri hale getirmek ve kodlanmış SOAP iletilerini oluşturmak için kullanılabilir. Elde edilen XML uyan ["Basit Nesne Erişim Protokolü (SOAP) 1.1" World Wide Web Consortium belgesinin 5 bölümüne](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). SOAP iletilerini iletişim kuran bir XML Web hizmeti oluştururken, sınıflar ve sınıf üyeleri için özel SOAP öznitelikleri kümesi uygulayarak XML akışı özelleştirebilirsiniz. Öznitelikler listesi için bkz. [öznitelikleri emin denetim kodlanmış SOAP serileştirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>SOAP kodlu XML akışı olarak bir nesneyi serileştirmek için  
  
1.  Sınıfını kullanarak oluşturmak [XML şema tanımı Aracı (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
2.  Bir uygulama veya daha fazla özel öznitelik bulunan `System.Xml.Serialization`. "Öznitelikler bu denetim kodlanan SOAP serileştirme." listesinde bakın  
  
3.  Oluşturma bir `XmlTypeMapping` yeni bir oluşturarak `SoapReflectionImporter`ve çağırma `ImportTypeMapping` sahip serileştirilmiş sınıf türü yöntemi.  
  
     Aşağıdaki kod örneği çağrıları `ImportTypeMapping` yöntemi `SoapReflectionImporter` sınıfı oluşturmak için bir `XmlTypeMapping`.  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4.  Bir örneğini oluşturmak `XmlSerializer` geçirerek sınıf `XmlTypeMapping` için <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> Oluşturucusu.  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  Arama `Serialize` veya `Deserialize` yöntemi.  
  
## <a name="example"></a>Örnek  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
- [XML Web Hizmetleri ile XML Serileştirme](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
- [Nasıl yapılır: Nesne Serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)

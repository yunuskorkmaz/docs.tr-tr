---
title: 'Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: bfbdda0861a6f2867a2e7003dd7054129fd343b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018027"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme
  
 SOAP iletisi XML kullanılarak oluşturulduğundan, <xref:System.Xml.Serialization.XmlSerializer> sınıfı sınıfları seri hale getirmek ve kodlanmış SOAP iletileri oluşturmak için kullanılabilir. Elde edilen XML, ["basit nesne erişim Protokolü (SOAP) 1,1" World Wide Web Konsorsiyumu belgesinin 5. bölümüne](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512)uygundur. SOAP iletileri aracılığıyla iletişim kuran bir XML Web hizmeti oluştururken, sınıflara ve sınıfların üyelerine bir dizi özel SOAP özniteliği uygulayarak XML akışını özelleştirebilirsiniz. Özniteliklerin bir listesi için bkz. [KODLANMıŞ SOAP serileştirmesini denetleyen öznitelikler](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Bir nesneyi SOAP kodlu XML akışı olarak seri hale getirmek için  
  
1. [XML şema tanımı aracını (xsd. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)kullanarak sınıfı oluşturun.  
  
2. İçinde `System.Xml.Serialization`bulunan özel özniteliklerin birini veya birkaçını uygulayın. "Kodlanmış SOAP serileştirmesini denetleyen öznitelikler" içindeki listeye bakın.  
  
3. Oluşturma bir `XmlTypeMapping` yeni bir oluşturarak `SoapReflectionImporter`ve çağırma `ImportTypeMapping` sahip serileştirilmiş sınıf türü yöntemi.  
  
     Aşağıdaki kod örneği, oluşturmak için `ImportTypeMapping` `SoapReflectionImporter` sınıfının yöntemini çağırır `XmlTypeMapping`.  
  
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
  
4. Oluşturucuyu oluşturucuya geçirerek `XmlSerializer` `XmlTypeMapping` sınıfın bir örneğini oluşturun. <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. Arama `Serialize` veya `Deserialize` yöntemi.  
  
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

- [XML ve SOAP serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [Kodlanmış SOAP serileştirmesini denetleyen öznitelikler](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [XML Web hizmetleriyle XML serileştirme](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [Nasıl yapılır: Nesne Serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)

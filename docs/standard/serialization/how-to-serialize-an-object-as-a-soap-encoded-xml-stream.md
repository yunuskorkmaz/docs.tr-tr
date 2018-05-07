---
title: 'Nasıl yapılır: bir SOAP kodlanmış XML akışı olarak bir nesneyi serileştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: 20cd4488062095f7b10cc62943a67b434caa2b5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Nasıl yapılır: bir SOAP kodlanmış XML akışı olarak bir nesneyi serileştirme
  
 Bir SOAP iletisi XML kullanarak oluşturulduğundan <xref:System.Xml.Serialization.XmlSerializer> sınıfı, sınıfları seri hale getirmek ve kodlanmış SOAP iletileri oluşturmak için kullanılabilir. Sonuçta elde edilen XML uyan [5 World Wide Web Konsorsiyumu belgenin "Basit Nesne Erişim Protokolü (SOAP) 1.1" bölümünde](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). SOAP iletilerine iletişim kuran XML Web hizmeti oluştururken, sınıflar ve sınıf üyeleri için özel SOAP öznitelikler kümesi uygulayarak XML akışı özelleştirebilirsiniz. Öznitelikler listesi için bkz: [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>SOAP kodlanmış XML akışı bir nesneyi serileştirme  
  
1.  Sınıfını kullanarak oluşturmak [XML şema tanımı aracını (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).  
  
2.  Bir uygulama veya daha fazla özel öznitelikleri bulunan `System.Xml.Serialization`. "Öznitelikleri bu denetim kodlanmış SOAP seri hale getirme." listesinde bakın  
  
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
  
4.  Bir örneğini oluşturmak `XmlSerializer` geçirerek sınıfı `XmlTypeMapping` için <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> Oluşturucusu.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [XML Web Hizmetleri ile XML Serileştirme](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 [Nasıl yapılır: Nesne Serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)

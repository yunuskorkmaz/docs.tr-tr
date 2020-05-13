---
title: 'Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme'
description: Bir nesneyi SOAP kodlu XML akışı olarak serileştirmek hakkında bilgi edinin. XmlSerializer sınıfı, sınıfları seri hale getirmek ve kodlanmış SOAP iletileri oluşturmak için kullanılabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: 09f1431d05248ef3ac3fdcf24bca35ff5cc2e22b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378395"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme
  
 SOAP iletisi XML kullanılarak oluşturulduğundan, <xref:System.Xml.Serialization.XmlSerializer> sınıfı sınıfları seri hale getirmek ve KODLANMıŞ SOAP iletileri oluşturmak için kullanılabilir. Elde edilen XML, ["basit nesne erişim Protokolü (SOAP) 1,1" World Wide Web Konsorsiyumu belgesinin 5. bölümüne](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512)uygundur. SOAP iletileri aracılığıyla iletişim kuran bir XML Web hizmeti oluştururken, sınıflara ve sınıfların üyelerine bir dizi özel SOAP özniteliği uygulayarak XML akışını özelleştirebilirsiniz. Özniteliklerin bir listesi için bkz. [KODLANMıŞ SOAP serileştirmesini denetleyen öznitelikler](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Bir nesneyi SOAP kodlu XML akışı olarak seri hale getirmek için  
  
1. [XML şema tanımı aracını (xsd. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)kullanarak sınıfı oluşturun.  
  
2. İçinde bulunan özel özniteliklerin birini veya birkaçını uygulayın `System.Xml.Serialization` . "Kodlanmış SOAP serileştirmesini denetleyen öznitelikler" içindeki listeye bakın.  
  
3. Oluşturma bir `XmlTypeMapping` yeni bir oluşturarak `SoapReflectionImporter`ve çağırma `ImportTypeMapping` sahip serileştirilmiş sınıf türü yöntemi.  
  
     Aşağıdaki kod örneği, `ImportTypeMapping` `SoapReflectionImporter` oluşturmak için sınıfının yöntemini çağırır `XmlTypeMapping` .  
  
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
  
4. `XmlSerializer`Oluşturucuyu oluşturucuya geçirerek sınıfın bir örneğini oluşturun `XmlTypeMapping` <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> .  
  
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

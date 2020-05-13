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
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="eb76a-104">Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme</span><span class="sxs-lookup"><span data-stu-id="eb76a-104">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="eb76a-105">SOAP iletisi XML kullanılarak oluşturulduğundan, <xref:System.Xml.Serialization.XmlSerializer> sınıfı sınıfları seri hale getirmek ve KODLANMıŞ SOAP iletileri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb76a-105">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="eb76a-106">Elde edilen XML, ["basit nesne erişim Protokolü (SOAP) 1,1" World Wide Web Konsorsiyumu belgesinin 5. bölümüne](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512)uygundur.</span><span class="sxs-lookup"><span data-stu-id="eb76a-106">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="eb76a-107">SOAP iletileri aracılığıyla iletişim kuran bir XML Web hizmeti oluştururken, sınıflara ve sınıfların üyelerine bir dizi özel SOAP özniteliği uygulayarak XML akışını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb76a-107">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="eb76a-108">Özniteliklerin bir listesi için bkz. [KODLANMıŞ SOAP serileştirmesini denetleyen öznitelikler](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="eb76a-108">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="eb76a-109">Bir nesneyi SOAP kodlu XML akışı olarak seri hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="eb76a-109">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="eb76a-110">[XML şema tanımı aracını (xsd. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)kullanarak sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb76a-110">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="eb76a-111">İçinde bulunan özel özniteliklerin birini veya birkaçını uygulayın `System.Xml.Serialization` .</span><span class="sxs-lookup"><span data-stu-id="eb76a-111">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="eb76a-112">"Kodlanmış SOAP serileştirmesini denetleyen öznitelikler" içindeki listeye bakın.</span><span class="sxs-lookup"><span data-stu-id="eb76a-112">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="eb76a-113">Oluşturma bir `XmlTypeMapping` yeni bir oluşturarak `SoapReflectionImporter`ve çağırma `ImportTypeMapping` sahip serileştirilmiş sınıf türü yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eb76a-113">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="eb76a-114">Aşağıdaki kod örneği, `ImportTypeMapping` `SoapReflectionImporter` oluşturmak için sınıfının yöntemini çağırır `XmlTypeMapping` .</span><span class="sxs-lookup"><span data-stu-id="eb76a-114">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4. <span data-ttu-id="eb76a-115">`XmlSerializer`Oluşturucuyu oluşturucuya geçirerek sınıfın bir örneğini oluşturun `XmlTypeMapping` <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> .</span><span class="sxs-lookup"><span data-stu-id="eb76a-115">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="eb76a-116">Arama `Serialize` veya `Deserialize` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eb76a-116">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb76a-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb76a-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb76a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb76a-118">See also</span></span>

- [<span data-ttu-id="eb76a-119">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="eb76a-119">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [<span data-ttu-id="eb76a-120">Kodlanmış SOAP serileştirmesini denetleyen öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eb76a-120">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="eb76a-121">XML Web hizmetleriyle XML serileştirme</span><span class="sxs-lookup"><span data-stu-id="eb76a-121">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="eb76a-122">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="eb76a-122">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="eb76a-123">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="eb76a-123">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="eb76a-124">Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="eb76a-124">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)

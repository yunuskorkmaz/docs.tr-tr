---
title: "Nasıl yapılır: bir SOAP kodlanmış XML akışı olarak bir nesneyi serileştirme"
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
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 863c79b36cd51b2e1e747169fd15a2358a1e6fee
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="c375d-102">Nasıl yapılır: bir SOAP kodlanmış XML akışı olarak bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="c375d-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="c375d-103">Bir SOAP iletisi XML kullanarak oluşturulduğundan <xref:System.Xml.Serialization.XmlSerializer> sınıfı, sınıfları seri hale getirmek ve kodlanmış SOAP iletileri oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c375d-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="c375d-104">Sonuçta elde edilen XML uyan [5 World Wide Web Konsorsiyumu belgenin "Basit Nesne Erişim Protokolü (SOAP) 1.1" bölümünde](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="c375d-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="c375d-105">SOAP iletilerine iletişim kuran XML Web hizmeti oluştururken, sınıflar ve sınıf üyeleri için özel SOAP öznitelikler kümesi uygulayarak XML akışı özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c375d-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="c375d-106">Öznitelikler listesi için bkz: [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="c375d-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="c375d-107">SOAP kodlanmış XML akışı bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="c375d-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1.  <span data-ttu-id="c375d-108">Sınıfını kullanarak oluşturmak [XML şema tanımı aracını (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c375d-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2.  <span data-ttu-id="c375d-109">Bir uygulama veya daha fazla özel öznitelikleri bulunan `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="c375d-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="c375d-110">"Öznitelikleri bu denetim kodlanmış SOAP seri hale getirme." listesinde bakın</span><span class="sxs-lookup"><span data-stu-id="c375d-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3.  <span data-ttu-id="c375d-111">Oluşturma bir `XmlTypeMapping` yeni bir oluşturarak `SoapReflectionImporter`ve çağırma `ImportTypeMapping` sahip serileştirilmiş sınıf türü yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c375d-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="c375d-112">Aşağıdaki kod örneği çağrıları `ImportTypeMapping` yöntemi `SoapReflectionImporter` sınıfı oluşturmak için bir `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="c375d-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4.  <span data-ttu-id="c375d-113">Bir örneğini oluşturmak `XmlSerializer` geçirerek sınıfı `XmlTypeMapping` için <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="c375d-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  <span data-ttu-id="c375d-114">Arama `Serialize` veya `Deserialize` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c375d-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c375d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c375d-115">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c375d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c375d-116">See Also</span></span>  
 [<span data-ttu-id="c375d-117">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c375d-117">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="c375d-118">Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c375d-118">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [<span data-ttu-id="c375d-119">XML Web Hizmetleri ile XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c375d-119">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 [<span data-ttu-id="c375d-120">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c375d-120">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="c375d-121">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="c375d-121">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="c375d-122">Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="c375d-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)

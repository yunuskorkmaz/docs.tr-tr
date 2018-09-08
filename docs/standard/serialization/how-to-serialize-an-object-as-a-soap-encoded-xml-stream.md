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
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="2dcb0-102">Nasıl yapılır: SOAP kodlu XML Stream olarak bir nesneyi serileştirmek</span><span class="sxs-lookup"><span data-stu-id="2dcb0-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="2dcb0-103">XML, kullanarak bir SOAP ileti inşa edildiğinden <xref:System.Xml.Serialization.XmlSerializer> sınıfı sınıfları seri hale getirmek ve kodlanmış SOAP iletilerini oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2dcb0-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="2dcb0-104">Elde edilen XML uyan ["Basit Nesne Erişim Protokolü (SOAP) 1.1" World Wide Web Consortium belgesinin 5 bölümüne](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="2dcb0-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="2dcb0-105">SOAP iletilerini iletişim kuran bir XML Web hizmeti oluştururken, sınıflar ve sınıf üyeleri için özel SOAP öznitelikleri kümesi uygulayarak XML akışı özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dcb0-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="2dcb0-106">Öznitelikler listesi için bkz. [öznitelikleri emin denetim kodlanmış SOAP serileştirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="2dcb0-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="2dcb0-107">SOAP kodlu XML akışı olarak bir nesneyi serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="2dcb0-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1.  <span data-ttu-id="2dcb0-108">Sınıfını kullanarak oluşturmak [XML şema tanımı Aracı (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2dcb0-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2.  <span data-ttu-id="2dcb0-109">Bir uygulama veya daha fazla özel öznitelik bulunan `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="2dcb0-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="2dcb0-110">"Öznitelikler bu denetim kodlanan SOAP serileştirme." listesinde bakın</span><span class="sxs-lookup"><span data-stu-id="2dcb0-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3.  <span data-ttu-id="2dcb0-111">Oluşturma bir `XmlTypeMapping` yeni bir oluşturarak `SoapReflectionImporter`ve çağırma `ImportTypeMapping` sahip serileştirilmiş sınıf türü yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2dcb0-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="2dcb0-112">Aşağıdaki kod örneği çağrıları `ImportTypeMapping` yöntemi `SoapReflectionImporter` sınıfı oluşturmak için bir `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="2dcb0-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4.  <span data-ttu-id="2dcb0-113">Bir örneğini oluşturmak `XmlSerializer` geçirerek sınıf `XmlTypeMapping` için <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="2dcb0-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  <span data-ttu-id="2dcb0-114">Arama `Serialize` veya `Deserialize` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2dcb0-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dcb0-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dcb0-115">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2dcb0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dcb0-116">See also</span></span>

- [<span data-ttu-id="2dcb0-117">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2dcb0-117">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [<span data-ttu-id="2dcb0-118">Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2dcb0-118">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
- [<span data-ttu-id="2dcb0-119">XML Web Hizmetleri ile XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2dcb0-119">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
- [<span data-ttu-id="2dcb0-120">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2dcb0-120">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [<span data-ttu-id="2dcb0-121">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="2dcb0-121">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [<span data-ttu-id="2dcb0-122">Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="2dcb0-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)

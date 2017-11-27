---
title: "Kodlanmış SOAP serileştirme denetim öznitelikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 052996bedcb10494cb2fee1ccf3ba7b5a083356b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="712b7-102">Kodlanmış SOAP serileştirme denetim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="712b7-102">Attributes That Control Encoded SOAP Serialization</span></span> 
<span data-ttu-id="712b7-103">"Basit Nesne Erişim Protokolü (SOAP) 1.1" adlı World Wide Web Konsorsiyumu (www.w3.org) belgenin nasıl SOAP parametreleri kodlanmış açıklayan isteğe bağlı bir bölüm (Bölüm 5) içerir.</span><span class="sxs-lookup"><span data-stu-id="712b7-103">The World Wide Web Consortium (www.w3.org) document named "Simple Object Access Protocol (SOAP) 1.1" contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="712b7-104">Belirtimi 5 bölümüne uygun olması için bir özel bulunan öznitelikler kümesi kullanın <xref:System.Xml.Serialization> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="712b7-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="712b7-105">Bu öznitelik sınıfları ve sınıf üyeleri için uygun şekilde uygulayın ve ardından <xref:System.Xml.Serialization.XmlSerializer> sınıflar ve sınıf örneklerini serileştirmek için.</span><span class="sxs-lookup"><span data-stu-id="712b7-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>  
  
 <span data-ttu-id="712b7-106">Aşağıdaki tabloda, bunlar uygulanabileceği, öznitelikleri ve ne yaptıklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="712b7-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="712b7-107">Bu öznitelikler denetimine XML serileştirme kullanma hakkında daha fazla bilgi için bkz [nasıl yapılır: bir SOAP olarak bir nesneyi serileştirme-kodlanmış XML akışı](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) ve [nasıl yapılır: Kodlanmış SOAP XML serileştirme geçersiz kılma](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="712b7-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span></span>  
  
 <span data-ttu-id="712b7-108">Öznitelikler hakkında daha fazla bilgi için bkz: [öznitelikleri](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="712b7-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>  
  
|<span data-ttu-id="712b7-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="712b7-109">Attribute</span></span>|<span data-ttu-id="712b7-110">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="712b7-110">Applies to</span></span>|<span data-ttu-id="712b7-111">Belirler</span><span class="sxs-lookup"><span data-stu-id="712b7-111">Specifies</span></span>|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="712b7-112">Ortak alan, özelliği, parameTRe veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="712b7-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="712b7-113">Sınıf üyesi bir XML özniteliği olarak seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="712b7-113">The class member will be serialized as an XML attribute.</span></span>|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="712b7-114">Ortak alan, özelliği, parameTRe veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="712b7-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="712b7-115">Sınıf bir XML öğesi olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="712b7-115">The class will be serialized as an XML element.</span></span>|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="712b7-116">Bir numaralandırma tanımlayıcı ortak alan.</span><span class="sxs-lookup"><span data-stu-id="712b7-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="712b7-117">Numaralandırma üyesi öğe adı.</span><span class="sxs-lookup"><span data-stu-id="712b7-117">The element name of an enumeration member.</span></span>|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="712b7-118">Ortak özellikler ve alanları.</span><span class="sxs-lookup"><span data-stu-id="712b7-118">Public properties and fields.</span></span>|<span data-ttu-id="712b7-119">Kapsayan sınıfı serileştirilmiş olduğunda özellik veya alan yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="712b7-119">The property or field should be ignored when the containing class is serialized.</span></span>|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="712b7-120">Genel türetilmiş sınıf bildirimleri ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri için ortak yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="712b7-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="712b7-121">Türü (serileştirilmiş olduğunda tanınması için) şemalar oluşturulurken dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="712b7-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="712b7-122">Ortak sınıf bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="712b7-122">Public class declarations.</span></span>|<span data-ttu-id="712b7-123">Sınıf bir XML türü olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="712b7-123">The class should be serialized as an XML type.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="712b7-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="712b7-124">See Also</span></span>  
 [<span data-ttu-id="712b7-125">XML ve SOAP seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="712b7-125">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="712b7-126">Nasıl yapılır: bir SOAP kodlanmış XML akışı olarak bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="712b7-126">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [<span data-ttu-id="712b7-127">Nasıl yapılır: Kodlanmış SOAP XML serileştirmesi için geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="712b7-127">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [<span data-ttu-id="712b7-128">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="712b7-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="712b7-129">Nasıl yapılır: bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="712b7-129">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="712b7-130">Nasıl yapılır: bir nesne seri durumdan</span><span class="sxs-lookup"><span data-stu-id="712b7-130">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

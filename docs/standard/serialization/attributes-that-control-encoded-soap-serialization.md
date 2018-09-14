---
title: Kodlanmış SOAP serileştirmesini denetleyen öznitelikler
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 7b5a48003ff9bfb398c05c8d70a9076d49ad83d6
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515437"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="37d91-102">Kodlanmış SOAP serileştirmesini denetleyen öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37d91-102">Attributes That Control Encoded SOAP Serialization</span></span>

<span data-ttu-id="37d91-103">Adlı World Wide Web Consortium (W3C) belgenin [Basit Nesne Erişim Protokolü (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) nasıl SOAP parametreleri kodlanmış açıklayan isteğe bağlı bir bölüm (Bölüm 5) içerir.</span><span class="sxs-lookup"><span data-stu-id="37d91-103">The World Wide Web Consortium (W3C) document named [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="37d91-104">Belirtiminin 5 bölümüne uymak için özel öznitelikler bulundu kümesi kullanmak <xref:System.Xml.Serialization> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="37d91-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="37d91-105">Özniteliklerle sınıfları ve sınıf üyeleri için uygun olarak uygulayın ve ardından <xref:System.Xml.Serialization.XmlSerializer> sınıf veya sınıfların örneklerini serileştirmek için.</span><span class="sxs-lookup"><span data-stu-id="37d91-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>

<span data-ttu-id="37d91-106">Aşağıdaki tablo nerede bunlar uygulanabilir, öznitelikleri ve neler yaptığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="37d91-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="37d91-107">Denetim XML serileştirme için bu öznitelikleri kullanmayla ilgili daha fazla bilgi için bkz. [nasıl yapılır: bir SOAP olarak bir nesneyi serileştirip-kodlanmış XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) ve [nasıl yapılır: Kodlanmış SOAP XML serileştirme geçersiz kılma](how-to-override-encoded-soap-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="37d91-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](how-to-override-encoded-soap-xml-serialization.md).</span></span>

<span data-ttu-id="37d91-108">Öznitelikler hakkında daha fazla bilgi için bkz. [öznitelikleri](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="37d91-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>

|<span data-ttu-id="37d91-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37d91-109">Attribute</span></span>|<span data-ttu-id="37d91-110">Uygulandığı öğe:</span><span class="sxs-lookup"><span data-stu-id="37d91-110">Applies to</span></span>|<span data-ttu-id="37d91-111">Belirler</span><span class="sxs-lookup"><span data-stu-id="37d91-111">Specifies</span></span>|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="37d91-112">Ortak alan, özelliği, parameTRe veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="37d91-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="37d91-113">Sınıf üyesi bir XML özniteliği olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="37d91-113">The class member will be serialized as an XML attribute.</span></span>|
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="37d91-114">Ortak alan, özelliği, parameTRe veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="37d91-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="37d91-115">Sınıf bir XML öğesi olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="37d91-115">The class will be serialized as an XML element.</span></span>|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="37d91-116">Bir numaralandırma tanımlayıcı ortak alan.</span><span class="sxs-lookup"><span data-stu-id="37d91-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="37d91-117">Numaralandırma üyesi öğe adı.</span><span class="sxs-lookup"><span data-stu-id="37d91-117">The element name of an enumeration member.</span></span>|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="37d91-118">Ortak özellikler ve alanları.</span><span class="sxs-lookup"><span data-stu-id="37d91-118">Public properties and fields.</span></span>|<span data-ttu-id="37d91-119">Kapsayan sınıfı serileştirilmiş olduğunda özellik veya alan yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="37d91-119">The property or field should be ignored when the containing class is serialized.</span></span>|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="37d91-120">Genel türetilmiş sınıf bildirimleri ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri için ortak yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="37d91-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="37d91-121">Türü (serileştirilmiş olduğunda tanınması için) şemalar oluşturulurken dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="37d91-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="37d91-122">Ortak sınıf bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="37d91-122">Public class declarations.</span></span>|<span data-ttu-id="37d91-123">Sınıf bir XML türü olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="37d91-123">The class should be serialized as an XML type.</span></span>|

## <a name="see-also"></a><span data-ttu-id="37d91-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37d91-124">See also</span></span>

- [<span data-ttu-id="37d91-125">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="37d91-125">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
- [<span data-ttu-id="37d91-126">Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme</span><span class="sxs-lookup"><span data-stu-id="37d91-126">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
- [<span data-ttu-id="37d91-127">Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="37d91-127">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)  
- [<span data-ttu-id="37d91-128">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37d91-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [<span data-ttu-id="37d91-129">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="37d91-129">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)  
- [<span data-ttu-id="37d91-130">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="37d91-130">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)

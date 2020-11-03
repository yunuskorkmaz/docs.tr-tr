---
title: Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler
description: Bu makalede, System.Xml bulunan özel bir öznitelik kümesi listelenir. SOAP belirtimine uyması için serileştirme ad alanı gerekiyor.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 69a9d1c8734a393b576cf87e7e05ef92c10120c8
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282037"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="31152-103">Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31152-103">Attributes That Control Encoded SOAP Serialization</span></span>

<span data-ttu-id="31152-104">[Basit nesne erişim Protokolü (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) adlı World WIDE Web KONSORSIYUMU (W3C) BELGESI, SOAP parametrelerinin nasıl kodlandığını açıklayan isteğe bağlı bir bölüm (5. bölüm) içerir.</span><span class="sxs-lookup"><span data-stu-id="31152-104">The World Wide Web Consortium (W3C) document named [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="31152-105">Belirtimin 5. bölümüne uymak için, ad alanında bulunan özel bir öznitelik kümesi kullanmanız gerekir <xref:System.Xml.Serialization> .</span><span class="sxs-lookup"><span data-stu-id="31152-105">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="31152-106">Bu öznitelikleri sınıflar ve sınıfların üyelerine uygun şekilde uygulayın ve ardından <xref:System.Xml.Serialization.XmlSerializer> sınıfı veya sınıfların örneklerini seri hale getirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="31152-106">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>

<span data-ttu-id="31152-107">Aşağıdaki tabloda öznitelikleri, nerede uygulanabileceğini ve ne yaptığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31152-107">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="31152-108">XML serileştirmesini denetlemek için bu öznitelikleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir nesneyi SOAP-Encoded XML akışı olarak serileştirme](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) ve [nasıl yapılır: kodlanmış SOAP XML serileştirmesini geçersiz kılma](how-to-override-encoded-soap-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="31152-108">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](how-to-override-encoded-soap-xml-serialization.md).</span></span>

<span data-ttu-id="31152-109">Öznitelikler hakkında daha fazla bilgi için bkz. [öznitelikler](../attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="31152-109">For more information about attributes, see [Attributes](../attributes/index.md).</span></span>

|<span data-ttu-id="31152-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31152-110">Attribute</span></span>|<span data-ttu-id="31152-111">Şunlara uygulanır</span><span class="sxs-lookup"><span data-stu-id="31152-111">Applies to</span></span>|<span data-ttu-id="31152-112">Belirler</span><span class="sxs-lookup"><span data-stu-id="31152-112">Specifies</span></span>|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="31152-113">Ortak alan, özelliği, parameTRe veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="31152-113">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="31152-114">Sınıf üyesi bir XML özniteliği olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="31152-114">The class member will be serialized as an XML attribute.</span></span>|
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="31152-115">Ortak alan, özelliği, parameTRe veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="31152-115">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="31152-116">Sınıf bir XML öğesi olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="31152-116">The class will be serialized as an XML element.</span></span>|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="31152-117">Bir numaralandırma tanımlayıcı ortak alan.</span><span class="sxs-lookup"><span data-stu-id="31152-117">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="31152-118">Numaralandırma üyesi öğe adı.</span><span class="sxs-lookup"><span data-stu-id="31152-118">The element name of an enumeration member.</span></span>|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="31152-119">Ortak özellikler ve alanları.</span><span class="sxs-lookup"><span data-stu-id="31152-119">Public properties and fields.</span></span>|<span data-ttu-id="31152-120">Kapsayan sınıfı serileştirilmiş olduğunda özellik veya alan yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="31152-120">The property or field should be ignored when the containing class is serialized.</span></span>|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="31152-121">Genel türetilmiş sınıf bildirimleri ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri için ortak yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="31152-121">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="31152-122">Türü (serileştirilmiş olduğunda tanınması için) şemalar oluşturulurken dahil edilecek.</span><span class="sxs-lookup"><span data-stu-id="31152-122">The type should be included when generating schemas (to be recognized when serialized).</span></span>|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="31152-123">Ortak sınıf bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="31152-123">Public class declarations.</span></span>|<span data-ttu-id="31152-124">Sınıf bir XML türü olarak seri hale.</span><span class="sxs-lookup"><span data-stu-id="31152-124">The class should be serialized as an XML type.</span></span>|

## <a name="see-also"></a><span data-ttu-id="31152-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31152-125">See also</span></span>

- [<span data-ttu-id="31152-126">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="31152-126">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="31152-127">Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme</span><span class="sxs-lookup"><span data-stu-id="31152-127">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [<span data-ttu-id="31152-128">Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="31152-128">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
- [<span data-ttu-id="31152-129">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31152-129">Attributes</span></span>](../attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="31152-130">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="31152-130">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="31152-131">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="31152-131">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)

---
title: XML ve SOAP seri hale getirme
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
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 006727e70c58834a4e628f584a28302a62363844
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="c3de4-102">XML ve SOAP seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="c3de4-102">XML and SOAP Serialization</span></span>
<span data-ttu-id="c3de4-103">XML serileştirme dönüştürür (serileştiren) genel alanlar ve bir nesne veya özelliklerini parametreler ve dönüş değerleri için belirli bir XML Şeması Tanım Dili (XSD) belge uyan bir XML akışı içine yöntemlerin.</span><span class="sxs-lookup"><span data-stu-id="c3de4-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="c3de4-104">XML serileştirme kesin türü belirtilmiş sınıfları genel özellikleri ve bir seri biçiminde (Bu durumda, XML) depolama veya taşıma için dönüştürülür alanları ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c3de4-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>  
  
 <span data-ttu-id="c3de4-105">XML açık bir standart olduğundan, XML akışı gerektiğinde platformundan bağımsız olarak herhangi bir uygulama tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c3de4-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="c3de4-106">XML Web Hizmetleri gibi ASP.NET kullanım kullanılarak oluşturulan <xref:System.Xml.Serialization.XmlSerializer> internet veya intranet üzerinde XML Web hizmeti uygulamalar arasında veri iletmek XML akışlar oluşturmak üzere sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c3de4-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="c3de4-107">Buna karşılık, seri durumdan çıkarma gibi bir XML akışı alır ve nesneyi yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3de4-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>  
  
 <span data-ttu-id="c3de4-108">XML serileştirme, SOAP belirtimine uygun XML akışları içine nesneleri seri hale getirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3de4-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="c3de4-109">SOAP, özellikle XML kullanarak yordam çağrıları taşımak için tasarlanmış XML, tabanlı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="c3de4-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>  
  
 <span data-ttu-id="c3de4-110">Serileştirmek veya seri durumdan nesneleri için kullanmak <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c3de4-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="c3de4-111">Serileştirilecek sınıflar oluşturmak için XML şema tanımı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3de4-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3de4-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c3de4-112">In This Section</span></span>  
 [<span data-ttu-id="c3de4-113">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="c3de4-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 <span data-ttu-id="c3de4-114">Genel bir tanımı serileştirme, özellikle XML serileştirme için sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-114">Provides a general definition of serialization, particularly XML serialization.</span></span>  
  
 [<span data-ttu-id="c3de4-115">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c3de4-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 <span data-ttu-id="c3de4-116">Nesneyi serileştirmek için adım adım yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-116">Provides step-by-step instructions for serializing an object.</span></span>  
  
 [<span data-ttu-id="c3de4-117">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="c3de4-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 <span data-ttu-id="c3de4-118">Bir nesne seri durumdan çıkarmak için adım adım yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-118">Provides step-by-step instructions for deserializing an object.</span></span>  
  
 [<span data-ttu-id="c3de4-119">XML Serileştirme Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c3de4-119">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 <span data-ttu-id="c3de4-120">XML serileştirme temelleri gösteren örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-120">Provides examples that demonstrate the basics of XML serialization.</span></span>  
  
 [<span data-ttu-id="c3de4-121">XML Şema Tanımı Aracı ve XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c3de4-121">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 <span data-ttu-id="c3de4-122">XML şema tanımı araç, belirli bir XML şeması tanım dili (XSD) şeması uyması sınıflar oluşturmak için veya bir .dll dosyasından bir XML şeması oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>  
  
 [<span data-ttu-id="c3de4-123">Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme</span><span class="sxs-lookup"><span data-stu-id="c3de4-123">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 <span data-ttu-id="c3de4-124">Serileştirme özniteliklerini kullanarak denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-124">Describes how to control serialization by using attributes.</span></span>  
  
 [<span data-ttu-id="c3de4-125">XML Serileştirmeyi Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c3de4-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 <span data-ttu-id="c3de4-126">XML serileştirme denetlemek için kullanılan öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c3de4-126">Lists the attributes that are used to control XML serialization.</span></span>  
  
 [<span data-ttu-id="c3de4-127">Nasıl yapılır: XML Akışı için Alternatif Öğe Adı Belirtme</span><span class="sxs-lookup"><span data-stu-id="c3de4-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 <span data-ttu-id="c3de4-128">Seri hale getirme geçersiz kılarak birden çok XML akışı oluşturmak nasıl gösteren Gelişmiş bir senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3de4-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>  
  
 [<span data-ttu-id="c3de4-129">Nasıl yapılır: Türetilen Sınıfların Serileştirmesini Denetleme</span><span class="sxs-lookup"><span data-stu-id="c3de4-129">How to: Control Serialization of Derived Classes</span></span>](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 <span data-ttu-id="c3de4-130">Türetilen sınıflar serileştirmek denetlemek nasıl bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-130">Provides an example of how to control the serialization of derived classes.</span></span>  
  
 [<span data-ttu-id="c3de4-131">Nasıl yapılır: XML Öğesini ve XML Öznitelik Adlarını Niteleme</span><span class="sxs-lookup"><span data-stu-id="c3de4-131">How to: Qualify XML Element and XML Attribute Names</span></span>](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 <span data-ttu-id="c3de4-132">Tanımlamak ve XML akışında kullanılan hangi XML ad alanları şeklini denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>  
  
 [<span data-ttu-id="c3de4-133">XML Web Hizmetleri ile XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c3de4-133">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 <span data-ttu-id="c3de4-134">XML serileştirme XML Web hizmetleri nasıl kullanıldığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3de4-134">Explains how XML serialization is used in XML Web services.</span></span>  
  
 [<span data-ttu-id="c3de4-135">Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c3de4-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 <span data-ttu-id="c3de4-136">Nasıl kullanılacağını açıklar <xref:System.Xml.Serialization.XmlSerializer> "Basit Nesne Erişim Protokolü (SOAP) 1.1." başlıklı bölüme World Wide Web Konsorsiyumu (www.w3.org) belgenin 5 uygun kodlanmış SOAP XML akışlar oluşturmak üzere sınıfı</span><span class="sxs-lookup"><span data-stu-id="c3de4-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1."</span></span>  
  
 [<span data-ttu-id="c3de4-137">Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="c3de4-137">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 <span data-ttu-id="c3de4-138">Nesneleri serileştirmek XML SOAP iletilerini olarak geçersiz kılma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>  
  
 [<span data-ttu-id="c3de4-139">Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c3de4-139">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 <span data-ttu-id="c3de4-140">SOAP kodlanmış serileştirme denetlemek için kullanılan öznitelikleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c3de4-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>  
  
 [<span data-ttu-id="c3de4-141">\<dizileştirme mekanizmasını System.xml.Serialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="c3de4-141">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 <span data-ttu-id="c3de4-142">XML serileştirme denetlemek için üst düzey yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c3de4-142">The top-level configuration element for controlling XML serialization.</span></span>  
  
 [<span data-ttu-id="c3de4-143">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="c3de4-143">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 <span data-ttu-id="c3de4-144">Seri hale getirme modunu denetimleri <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c3de4-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 [<span data-ttu-id="c3de4-145">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="c3de4-145">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 <span data-ttu-id="c3de4-146">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c3de4-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
 [<span data-ttu-id="c3de4-147">\<Ekle > öğesi için \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="c3de4-147">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 <span data-ttu-id="c3de4-148">Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c3de4-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c3de4-149">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c3de4-149">Related Sections</span></span>  
 [<span data-ttu-id="c3de4-150">Gelişmiş geliştirme teknolojileri</span><span class="sxs-lookup"><span data-stu-id="c3de4-150">Advanced Development Technologies</span></span>](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 <span data-ttu-id="c3de4-151">Gelişmiş geliştirme görevlerini ve .NET Framework teknikleri hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-151">Provides links to more information on sophisticated development tasks and techniques in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="c3de4-152">ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="c3de4-152">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="c3de4-153">Açıklayan ve ASP.NET kullanarak XML Web Hizmetleri program açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3de4-153">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3de4-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3de4-154">See Also</span></span>  
 [<span data-ttu-id="c3de4-155">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="c3de4-155">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)

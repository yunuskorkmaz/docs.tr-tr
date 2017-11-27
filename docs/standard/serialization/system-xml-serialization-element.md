---
title: "&lt;dizileştirme mekanizmasını System.xml.Serialization&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfc2b38eba68a8c7f9ddab4a6ee941f6faee7c02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="dde28-102">&lt;dizileştirme mekanizmasını System.xml.Serialization&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="dde28-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="dde28-103">XML serileştirme denetleme en üst düzey öğesi.</span><span class="sxs-lookup"><span data-stu-id="dde28-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="dde28-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="dde28-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="dde28-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="dde28-105">\<configuration></span></span>  
<span data-ttu-id="dde28-106">\<dizileştirme mekanizmasını System.xml.Serialization ></span><span class="sxs-lookup"><span data-stu-id="dde28-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde28-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dde28-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dde28-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dde28-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dde28-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dde28-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dde28-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dde28-110">Attributes</span></span>  
 <span data-ttu-id="dde28-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="dde28-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dde28-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dde28-112">Child Elements</span></span>  
  
|<span data-ttu-id="dde28-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="dde28-113">Element</span></span>|<span data-ttu-id="dde28-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dde28-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dde28-115">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="dde28-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="dde28-116">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="dde28-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="dde28-117">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="dde28-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="dde28-118">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="dde28-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dde28-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dde28-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dde28-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="dde28-120">Element</span></span>|<span data-ttu-id="dde28-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dde28-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dde28-122">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="dde28-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="dde28-123">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="dde28-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dde28-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="dde28-124">Example</span></span>  
 <span data-ttu-id="dde28-125">Aşağıdaki kod örneğinde serileştirme modunu belirtme gösterilmektedir bir <xref:System.DateTime> nesne ve tarafından kullanılan türlerinin eklenmesi <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türleri için .NET Framework türleri eşlerken.</span><span class="sxs-lookup"><span data-stu-id="dde28-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dde28-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dde28-126">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="dde28-127">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="dde28-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="dde28-128">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="dde28-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="dde28-129">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="dde28-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [<span data-ttu-id="dde28-130">\<Ekle > öğesi için \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="dde28-130">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)

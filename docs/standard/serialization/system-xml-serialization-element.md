---
title: <system.xml.serialization> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f41e3811fc6bab8a354f75f46b0ac79c0ce42f99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018092"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="5b6bc-102">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="5b6bc-102">\<system.xml.serialization> Element</span></span>
<span data-ttu-id="5b6bc-103">XML serileştirme denetlemek için üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="5b6bc-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b6bc-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="5b6bc-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5b6bc-105">\<configuration></span></span>  
<span data-ttu-id="5b6bc-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="5b6bc-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b6bc-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b6bc-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b6bc-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b6bc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5b6bc-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b6bc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b6bc-110">Attributes</span></span>  
 <span data-ttu-id="5b6bc-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b6bc-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b6bc-112">Child Elements</span></span>  
  
|<span data-ttu-id="5b6bc-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b6bc-113">Element</span></span>|<span data-ttu-id="5b6bc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b6bc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b6bc-115">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="5b6bc-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="5b6bc-116">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|[<span data-ttu-id="5b6bc-117">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="5b6bc-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="5b6bc-118">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b6bc-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b6bc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5b6bc-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b6bc-120">Element</span></span>|<span data-ttu-id="5b6bc-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b6bc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b6bc-122">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="5b6bc-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="5b6bc-123">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b6bc-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b6bc-124">Example</span></span>  
 <span data-ttu-id="5b6bc-125">Aşağıdaki kod örneğinde serileştirme modunu belirtmek verilmektedir bir <xref:System.DateTime> nesnesi ve tarafından kullanılan türlerinin eklenmesi <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türleri için .NET Framework türleri eşlerken.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b6bc-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b6bc-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="5b6bc-127">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="5b6bc-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="5b6bc-128">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="5b6bc-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="5b6bc-129">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="5b6bc-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="5b6bc-130">\<Ekle > öğesi için \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="5b6bc-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)

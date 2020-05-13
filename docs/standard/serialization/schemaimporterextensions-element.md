---
title: <schemaImporterExtensions> Öğesi
description: <schemaImporterExtensions>Öğesi, xsd türlerinin .NET Framework türlerine eşlenmesi Için XmlSchemaImporter tarafından kullanılan türleri içerir.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379799"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="498c0-103">\<SchemaImporterExtensions> öğesi</span><span class="sxs-lookup"><span data-stu-id="498c0-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="498c0-104">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="498c0-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="498c0-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="498c0-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="498c0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="498c0-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="498c0-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="498c0-107">Child Elements</span></span>  
  
|<span data-ttu-id="498c0-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="498c0-108">Element</span></span>|<span data-ttu-id="498c0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="498c0-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="498c0-110">\<\<SchemaImporterExtensions için> öğesi ekleme></span><span class="sxs-lookup"><span data-stu-id="498c0-110">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="498c0-111">Eşlemeleri oluşturmak için tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> .</span><span class="sxs-lookup"><span data-stu-id="498c0-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="498c0-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="498c0-112">Parent Elements</span></span>  
  
|<span data-ttu-id="498c0-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="498c0-113">Element</span></span>|<span data-ttu-id="498c0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="498c0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="498c0-115">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="498c0-115">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="498c0-116">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="498c0-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="498c0-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="498c0-117">Example</span></span>  
 <span data-ttu-id="498c0-118">Aşağıdaki kod örneği, <xref:System.Xml.Serialization.XmlSchemaImporter> .NET Framework TÜRLERINE xsd türleri eşlerken tarafından kullanılan türlerin nasıl ekleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="498c0-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="498c0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="498c0-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="498c0-120">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="498c0-120">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="498c0-121">\<dateTimeSerialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="498c0-121">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="498c0-122">\<\<SchemaImporterExtensions için> öğesi ekleme></span><span class="sxs-lookup"><span data-stu-id="498c0-122">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="498c0-123">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="498c0-123">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)

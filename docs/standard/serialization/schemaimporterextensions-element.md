---
title: <schemaImporterExtensions> Öğesi
description: <schemaImporterExtensions>Öğesi, xsd türlerinin .NET Framework türlerine eşlenmesi Için XmlSchemaImporter tarafından kullanılan türleri içerir.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c46c5cb6e01463723f0f2ce3873fb4a6ec0b4e60
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278408"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="d5656-103">\<schemaImporterExtensions> Öğesi</span><span class="sxs-lookup"><span data-stu-id="d5656-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="d5656-104">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="d5656-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="d5656-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="d5656-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5656-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5656-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="d5656-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5656-107">Child Elements</span></span>  
  
|<span data-ttu-id="d5656-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="d5656-108">Element</span></span>|<span data-ttu-id="d5656-109">Description</span><span class="sxs-lookup"><span data-stu-id="d5656-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5656-110">\<add>İçin öğesi\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d5656-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="d5656-111">Eşlemeleri oluşturmak için tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> .</span><span class="sxs-lookup"><span data-stu-id="d5656-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="d5656-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5656-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d5656-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d5656-113">Element</span></span>|<span data-ttu-id="d5656-114">Description</span><span class="sxs-lookup"><span data-stu-id="d5656-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5656-115">\<system.xml.serialization>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d5656-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="d5656-116">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="d5656-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d5656-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5656-117">Example</span></span>  
 <span data-ttu-id="d5656-118">Aşağıdaki kod örneği, <xref:System.Xml.Serialization.XmlSchemaImporter> .NET Framework TÜRLERINE xsd türleri eşlerken tarafından kullanılan türlerin nasıl ekleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d5656-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5656-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5656-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="d5656-120">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d5656-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="d5656-121">\<dateTimeSerialization>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d5656-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="d5656-122">\<add>İçin öğesi\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="d5656-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="d5656-123">\<system.xml.serialization>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="d5656-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)

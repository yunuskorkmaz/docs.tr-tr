---
title: <schemaImporterExtensions> Öğesi
description: <schemaImporterExtensions>Öğesi, xsd türlerini .net türlerine eşlemek Için XmlSchemaImporter tarafından kullanılan türleri içerir.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 35626618a8dd7c63a7008d10bc3568484836a488
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282270"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="46c29-103">\<schemaImporterExtensions> öğesi</span><span class="sxs-lookup"><span data-stu-id="46c29-103">\<schemaImporterExtensions> element</span></span>

<span data-ttu-id="46c29-104"><xref:System.Xml.Serialization.XmlSchemaImporter>XSD türlerinin .net türlerine eşlenmesi için tarafından kullanılan türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="46c29-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span> <span data-ttu-id="46c29-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="46c29-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c29-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="46c29-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="46c29-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="46c29-107">Child Elements</span></span>  
  
|<span data-ttu-id="46c29-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="46c29-108">Element</span></span>|<span data-ttu-id="46c29-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46c29-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46c29-110">\<add> İçin öğesi \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="46c29-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="46c29-111">Eşlemeleri oluşturmak için tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> .</span><span class="sxs-lookup"><span data-stu-id="46c29-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="46c29-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="46c29-112">Parent Elements</span></span>  
  
|<span data-ttu-id="46c29-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="46c29-113">Element</span></span>|<span data-ttu-id="46c29-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46c29-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46c29-115">\<system.xml.serialization> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="46c29-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="46c29-116">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="46c29-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="46c29-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="46c29-117">Example</span></span>  
 <span data-ttu-id="46c29-118">Aşağıdaki kod örneği, <xref:System.Xml.Serialization.XmlSchemaImporter> xsd türlerini .net türlerine eşlerken tarafından kullanılan türlerin nasıl ekleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="46c29-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46c29-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46c29-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="46c29-120">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="46c29-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="46c29-121">\<dateTimeSerialization> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="46c29-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="46c29-122">\<add> İçin öğesi \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="46c29-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="46c29-123">\<system.xml.serialization> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="46c29-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)

---
title: <schemaImporterExtensions> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 43f8439708c73e8e5241a923360caf549bf09d8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017975"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="03004-102">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="03004-102">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="03004-103">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="03004-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="03004-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="03004-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03004-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03004-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="03004-106">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="03004-106">Child Elements</span></span>  
  
|<span data-ttu-id="03004-107">Öğe</span><span class="sxs-lookup"><span data-stu-id="03004-107">Element</span></span>|<span data-ttu-id="03004-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03004-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03004-109">\<Ekle > öğesi için \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="03004-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="03004-110">Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> eşlemeleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="03004-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="03004-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="03004-111">Parent Elements</span></span>  
  
|<span data-ttu-id="03004-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="03004-112">Element</span></span>|<span data-ttu-id="03004-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03004-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03004-114">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="03004-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="03004-115">XML serileştirme denetlemek için üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="03004-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="03004-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="03004-116">Example</span></span>  
 <span data-ttu-id="03004-117">Aşağıdaki kod örneği tarafından kullanılan türlerinizi eklemek üzere gösterir <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türleri için .NET Framework türleri eşlerken.</span><span class="sxs-lookup"><span data-stu-id="03004-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03004-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03004-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="03004-119">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="03004-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="03004-120">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="03004-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="03004-121">\<Ekle > öğesi için \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="03004-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="03004-122">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="03004-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)

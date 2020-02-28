---
title: <schemaImporterExtensions> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5ed80ac370e34d6b62bb2b601cb7bd978228a302
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159825"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="d9539-102">\<SchemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="d9539-102">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="d9539-103">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="d9539-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="d9539-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9539-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9539-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9539-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="d9539-106">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9539-106">Child Elements</span></span>  
  
|<span data-ttu-id="d9539-107">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9539-107">Element</span></span>|<span data-ttu-id="d9539-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9539-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9539-109">\<SchemaImporterExtensions için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="d9539-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="d9539-110">Eşleme oluşturmak için <xref:System.Xml.Serialization.XmlSchemaImporter> tarafından kullanılan türleri ekler.</span><span class="sxs-lookup"><span data-stu-id="d9539-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="d9539-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9539-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d9539-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9539-112">Element</span></span>|<span data-ttu-id="d9539-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9539-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9539-114">System. xml. Serialization > öğesi \<</span><span class="sxs-lookup"><span data-stu-id="d9539-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="d9539-115">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="d9539-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d9539-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9539-116">Example</span></span>  
 <span data-ttu-id="d9539-117">Aşağıdaki kod örneği, XSD türlerini .NET Framework türlerine eşlerken <xref:System.Xml.Serialization.XmlSchemaImporter> tarafından kullanılan türlerin nasıl ekleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d9539-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9539-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9539-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="d9539-119">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d9539-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="d9539-120">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="d9539-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="d9539-121">\<SchemaImporterExtensions için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="d9539-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="d9539-122">System. xml. Serialization > öğesi \<</span><span class="sxs-lookup"><span data-stu-id="d9539-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)

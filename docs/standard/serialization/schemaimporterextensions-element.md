---
title: "&lt;schemaImporterExtensions&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c7b1e335f03c5558d7680567fe19f3de2f3f8d78
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="3db73-102">&lt;schemaImporterExtensions&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="3db73-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="3db73-103">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="3db73-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="3db73-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="3db73-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db73-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3db73-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="3db73-106">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3db73-106">Child Elements</span></span>  
  
|<span data-ttu-id="3db73-107">Öğe</span><span class="sxs-lookup"><span data-stu-id="3db73-107">Element</span></span>|<span data-ttu-id="3db73-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3db73-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3db73-109">\<Ekle > öğesi için \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="3db73-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="3db73-110">Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> eşlemeleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3db73-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="3db73-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3db73-111">Parent Elements</span></span>  
  
|<span data-ttu-id="3db73-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="3db73-112">Element</span></span>|<span data-ttu-id="3db73-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3db73-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3db73-114">\<dizileştirme mekanizmasını System.xml.Serialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="3db73-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="3db73-115">XML serileştirme denetleme en üst düzey öğesi.</span><span class="sxs-lookup"><span data-stu-id="3db73-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3db73-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3db73-116">Example</span></span>  
 <span data-ttu-id="3db73-117">Aşağıdaki kod örneği tarafından kullanılan türleri ekleme gösterir <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türleri için .NET Framework türleri eşlerken.</span><span class="sxs-lookup"><span data-stu-id="3db73-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3db73-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3db73-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="3db73-119">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="3db73-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="3db73-120">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="3db73-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="3db73-121">\<Ekle > öğesi için \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="3db73-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="3db73-122">\<dizileştirme mekanizmasını System.xml.Serialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="3db73-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)

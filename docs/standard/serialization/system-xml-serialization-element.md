---
title: <system.xml.serialization> Öğesi
description: Bu makalede, XML serileştirmesini denetlemek için en üst düzey öğe olan <system.xml. Serialization> öğesi açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 6291799aadc429e943996f2256d773ac36dd370f
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282392"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="5e4fd-103">\<system.xml.serialization> Öğesi</span><span class="sxs-lookup"><span data-stu-id="5e4fd-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="5e4fd-104">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="5e4fd-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e4fd-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="5e4fd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e4fd-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e4fd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e4fd-107">Attributes and Elements</span></span>

<span data-ttu-id="5e4fd-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e4fd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e4fd-109">Attributes</span></span>

<span data-ttu-id="5e4fd-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e4fd-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e4fd-111">Child Elements</span></span>

|<span data-ttu-id="5e4fd-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e4fd-112">Element</span></span>|<span data-ttu-id="5e4fd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e4fd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e4fd-114">\<dateTimeSerialization> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5e4fd-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="5e4fd-115">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="5e4fd-116">\<schemaImporterExtensions> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5e4fd-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="5e4fd-117"><xref:System.Xml.Serialization.XmlSchemaImporter>XSD türlerinin .net türlerine eşlenmesi için tarafından kullanılan türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5e4fd-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e4fd-118">Parent Elements</span></span>

|<span data-ttu-id="5e4fd-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e4fd-119">Element</span></span>|<span data-ttu-id="5e4fd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e4fd-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e4fd-121">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5e4fd-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="5e4fd-122">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="5e4fd-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e4fd-123">Example</span></span>

<span data-ttu-id="5e4fd-124">Aşağıdaki kod örneği, bir nesnenin serileştirme modunun <xref:System.DateTime> ve tarafından kullanılan türlerin ek olarak, <xref:System.Xml.Serialization.XmlSchemaImporter> xsd türlerini .net türlerine eşlerken nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a><span data-ttu-id="5e4fd-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e4fd-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="5e4fd-126">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="5e4fd-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="5e4fd-127">\<dateTimeSerialization> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5e4fd-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="5e4fd-128">\<schemaImporterExtensions> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5e4fd-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="5e4fd-129">\<add> İçin öğesi \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="5e4fd-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)

---
title: <system.xml.serialization> Öğesi
description: Bu makalede, XML serileştirmesini denetlemek için en üst düzey öğe olan System. xml. Serialization > öğesi < açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f69e80592e9321de64421b977a63b83d8be2ad9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289492"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="79ed2-103">\<system.xml.serialization> Öğesi</span><span class="sxs-lookup"><span data-stu-id="79ed2-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="79ed2-104">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="79ed2-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="79ed2-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="79ed2-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="79ed2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79ed2-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79ed2-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79ed2-107">Attributes and Elements</span></span>

<span data-ttu-id="79ed2-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79ed2-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="79ed2-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79ed2-109">Attributes</span></span>

<span data-ttu-id="79ed2-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="79ed2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79ed2-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79ed2-111">Child Elements</span></span>

|<span data-ttu-id="79ed2-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="79ed2-112">Element</span></span>|<span data-ttu-id="79ed2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79ed2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79ed2-114">\<dateTimeSerialization>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="79ed2-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="79ed2-115">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="79ed2-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="79ed2-116">\<schemaImporterExtensions>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="79ed2-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="79ed2-117">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="79ed2-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="79ed2-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79ed2-118">Parent Elements</span></span>

|<span data-ttu-id="79ed2-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="79ed2-119">Element</span></span>|<span data-ttu-id="79ed2-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79ed2-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79ed2-121">\<configuration>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="79ed2-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="79ed2-122">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="79ed2-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="79ed2-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="79ed2-123">Example</span></span>

<span data-ttu-id="79ed2-124">Aşağıdaki kod örneği, bir nesnenin serileştirme modunun <xref:System.DateTime> ve tarafından kullanılan türlerin <xref:System.Xml.Serialization.XmlSchemaImporter> .NET Framework türlerine ne zaman ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="79ed2-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="79ed2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79ed2-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="79ed2-126">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="79ed2-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="79ed2-127">\<dateTimeSerialization>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="79ed2-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="79ed2-128">\<schemaImporterExtensions>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="79ed2-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="79ed2-129">\<add>İçin öğesi\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="79ed2-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)

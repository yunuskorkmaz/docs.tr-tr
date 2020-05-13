---
title: <system.xml.serialization> Öğesi
description: Bu makalede, XML serileştirmesini denetlemek için en üst düzey öğe olan System. xml. Serialization> öğesi <açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 1e66220004d561f937d03c506e6f30db4ccc635b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380124"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="b0e7e-103">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="b0e7e-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="b0e7e-104">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="b0e7e-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="b0e7e-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="b0e7e-106">\<yapılandırma> </span><span class="sxs-lookup"><span data-stu-id="b0e7e-106">\<configuration></span></span>\
<span data-ttu-id="b0e7e-107">\<System. xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="b0e7e-107">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="b0e7e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0e7e-108">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b0e7e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0e7e-109">Attributes and Elements</span></span>

<span data-ttu-id="b0e7e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0e7e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0e7e-111">Attributes</span></span>

<span data-ttu-id="b0e7e-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b0e7e-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0e7e-113">Child Elements</span></span>

|<span data-ttu-id="b0e7e-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0e7e-114">Element</span></span>|<span data-ttu-id="b0e7e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0e7e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0e7e-116">\<dateTimeSerialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="b0e7e-116">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="b0e7e-117">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-117">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="b0e7e-118">\<SchemaImporterExtensions> öğesi</span><span class="sxs-lookup"><span data-stu-id="b0e7e-118">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="b0e7e-119">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-119">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b0e7e-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0e7e-120">Parent Elements</span></span>

|<span data-ttu-id="b0e7e-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0e7e-121">Element</span></span>|<span data-ttu-id="b0e7e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0e7e-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0e7e-123">\<yapılandırma> öğesi</span><span class="sxs-lookup"><span data-stu-id="b0e7e-123">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="b0e7e-124">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-124">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="b0e7e-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0e7e-125">Example</span></span>

<span data-ttu-id="b0e7e-126">Aşağıdaki kod örneği, bir nesnenin serileştirme modunun <xref:System.DateTime> ve tarafından kullanılan türlerin <xref:System.Xml.Serialization.XmlSchemaImporter> .NET Framework türlerine ne zaman ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-126">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b0e7e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="b0e7e-128">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="b0e7e-128">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="b0e7e-129">\<dateTimeSerialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="b0e7e-129">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="b0e7e-130">\<SchemaImporterExtensions> öğesi</span><span class="sxs-lookup"><span data-stu-id="b0e7e-130">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="b0e7e-131">\<\<SchemaImporterExtensions için> öğesi ekleme></span><span class="sxs-lookup"><span data-stu-id="b0e7e-131">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)

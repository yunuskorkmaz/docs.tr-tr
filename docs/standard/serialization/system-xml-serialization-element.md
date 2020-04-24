---
title: <system.xml.serialization> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 02027a238bc9a2f82963ea841584d2bb3c6446c6
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410541"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="55f60-102">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="55f60-102">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="55f60-103">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="55f60-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="55f60-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="55f60-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="55f60-105">\<yapılandırma> </span><span class="sxs-lookup"><span data-stu-id="55f60-105">\<configuration></span></span>\
<span data-ttu-id="55f60-106">\<System. xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="55f60-106">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="55f60-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55f60-107">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55f60-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55f60-108">Attributes and Elements</span></span>

<span data-ttu-id="55f60-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55f60-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="55f60-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55f60-110">Attributes</span></span>

<span data-ttu-id="55f60-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="55f60-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55f60-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55f60-112">Child Elements</span></span>

|<span data-ttu-id="55f60-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="55f60-113">Element</span></span>|<span data-ttu-id="55f60-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55f60-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55f60-115">\<dateTimeSerialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="55f60-115">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="55f60-116">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="55f60-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="55f60-117">\<SchemaImporterExtensions> öğesi</span><span class="sxs-lookup"><span data-stu-id="55f60-117">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="55f60-118">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.</span><span class="sxs-lookup"><span data-stu-id="55f60-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="55f60-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55f60-119">Parent Elements</span></span>

|<span data-ttu-id="55f60-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="55f60-120">Element</span></span>|<span data-ttu-id="55f60-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55f60-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55f60-122">\<yapılandırma> öğesi</span><span class="sxs-lookup"><span data-stu-id="55f60-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="55f60-123">Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="55f60-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="55f60-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="55f60-124">Example</span></span>

<span data-ttu-id="55f60-125">Aşağıdaki kod örneği, bir <xref:System.DateTime> nesnenin serileştirme modunun ve tarafından kullanılan türlerin .NET Framework türlerine ne <xref:System.Xml.Serialization.XmlSchemaImporter> zaman ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="55f60-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="55f60-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55f60-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="55f60-127">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="55f60-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="55f60-128">\<dateTimeSerialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="55f60-128">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="55f60-129">\<SchemaImporterExtensions> öğesi</span><span class="sxs-lookup"><span data-stu-id="55f60-129">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="55f60-130">\<SchemaImporterExtensions \<Için> öğesi ekleme></span><span class="sxs-lookup"><span data-stu-id="55f60-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)

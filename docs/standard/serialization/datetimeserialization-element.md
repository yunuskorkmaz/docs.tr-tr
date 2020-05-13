---
title: <dateTimeSerialization> Öğesi
description: Bu makalede <dateTimeSerialization> , DateTime nesnelerinin serileştirme modunu belirleyen öğesi açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375819"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="b2bb5-103">\<dateTimeSerialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="b2bb5-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="b2bb5-104">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="b2bb5-105">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="b2bb5-105">\<configuration></span></span>  
<span data-ttu-id="b2bb5-106">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="b2bb5-106">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2bb5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2bb5-107">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2bb5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bb5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b2bb5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2bb5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2bb5-110">Attributes</span></span>  
  
|<span data-ttu-id="b2bb5-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2bb5-111">Attributes</span></span>|<span data-ttu-id="b2bb5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2bb5-112">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="b2bb5-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-113">Optional.</span></span> <span data-ttu-id="b2bb5-114">Serileştirme modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-114">Specifies the serialization mode.</span></span> <span data-ttu-id="b2bb5-115">Birine ayarlayın <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-115">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="b2bb5-116">Varsayılan **gidiş dönüş**'dir.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-116">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2bb5-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bb5-117">Child Elements</span></span>  
 <span data-ttu-id="b2bb5-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2bb5-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2bb5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b2bb5-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2bb5-120">Element</span></span>|<span data-ttu-id="b2bb5-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2bb5-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2bb5-122">dizileştirme mekanizmasını System.xml.Serialization</span><span class="sxs-lookup"><span data-stu-id="b2bb5-122">system.xml.serialization</span></span>|<span data-ttu-id="b2bb5-123">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-123">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2bb5-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2bb5-124">Remarks</span></span>  
 <span data-ttu-id="b2bb5-125">.NET Framework sürüm 1,0, 1,1, 2,0 ve sonraki sürümlerinde, bu özellik **Yerel**olarak ayarlandığında <xref:System.DateTime> nesneler her zaman yerel saat olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-125">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="b2bb5-126">Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-126">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="b2bb5-127">.NET Framework eski sürümleriyle uyumluluğu sağlamak için bu özelliği **Yerel** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-127">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b2bb5-128">Sürüm 2,0 ' de ve bu özelliğe sahip .NET Framework sonraki sürümlerinde, yukarı **dönüş**olarak ayarlanan <xref:System.DateTime> nesneler, yerel, UTC veya belirtilmeyen bir saat diliminde olup olmadıklarını belirleyecek şekilde incelenir.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-128">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="b2bb5-129"><xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-129">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="b2bb5-130">Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-130">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bb5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2bb5-131">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="b2bb5-132">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="b2bb5-132">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="b2bb5-133">\<SchemaImporterExtensions> öğesi</span><span class="sxs-lookup"><span data-stu-id="b2bb5-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="b2bb5-134">\<\<SchemaImporterExtensions için> öğesi ekleme></span><span class="sxs-lookup"><span data-stu-id="b2bb5-134">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="b2bb5-135">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="b2bb5-135">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)

---
title: <dateTimeSerialization> Öğesi
description: Bu makalede <dateTimeSerialization> , DateTime nesnelerinin serileştirme modunu belirleyen öğesi açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 1623517e66955c14b7e738c860ec16086fe30429
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678980"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="291c9-103">\<dateTimeSerialization> Öğesi</span><span class="sxs-lookup"><span data-stu-id="291c9-103">\<dateTimeSerialization> Element</span></span>

<span data-ttu-id="291c9-104">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="291c9-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="291c9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="291c9-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="291c9-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="291c9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="291c9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="291c9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="291c9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="291c9-108">Attributes</span></span>  
  
|<span data-ttu-id="291c9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="291c9-109">Attributes</span></span>|<span data-ttu-id="291c9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="291c9-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="291c9-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="291c9-111">Optional.</span></span> <span data-ttu-id="291c9-112">Serileştirme modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="291c9-112">Specifies the serialization mode.</span></span> <span data-ttu-id="291c9-113">Birine ayarlayın <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="291c9-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="291c9-114">Varsayılan **gidiş dönüş**'dir.</span><span class="sxs-lookup"><span data-stu-id="291c9-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="291c9-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="291c9-115">Child Elements</span></span>  

 <span data-ttu-id="291c9-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="291c9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="291c9-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="291c9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="291c9-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="291c9-118">Element</span></span>|<span data-ttu-id="291c9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="291c9-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="291c9-120">dizileştirme mekanizmasını System.xml.Serialization</span><span class="sxs-lookup"><span data-stu-id="291c9-120">system.xml.serialization</span></span>|<span data-ttu-id="291c9-121">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="291c9-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="291c9-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="291c9-122">Remarks</span></span>  

<span data-ttu-id="291c9-123">Bu özellik **Yerel** olarak ayarlandığında, <xref:System.DateTime> nesneler her zaman yerel saat olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="291c9-123">When this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="291c9-124">Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="291c9-124">That is, local time zone information is always included with the serialized data.</span></span>
  
<span data-ttu-id="291c9-125">Bu özellik **gidiş dönüş** olarak ayarlandığında, <xref:System.DateTime> nesneler yerel, UTC veya belirtilmemiş bir saat diliminde olup olmadığını belirleyecek şekilde incelenir.</span><span class="sxs-lookup"><span data-stu-id="291c9-125">When this property is set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="291c9-126"><xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="291c9-126">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="291c9-127">Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.</span><span class="sxs-lookup"><span data-stu-id="291c9-127">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291c9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="291c9-128">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="291c9-129">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="291c9-129">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="291c9-130">\<schemaImporterExtensions> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="291c9-130">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="291c9-131">\<add> İçin öğesi \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="291c9-131">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="291c9-132">\<system.xml.serialization> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="291c9-132">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)

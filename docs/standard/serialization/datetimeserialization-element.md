---
title: <dateTimeSerialization> Öğesi
description: Bu makalede <dateTimeSerialization> , DateTime nesnelerinin serileştirme modunu belirleyen öğesi açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289648"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="72673-103">\<dateTimeSerialization> Öğesi</span><span class="sxs-lookup"><span data-stu-id="72673-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="72673-104">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="72673-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="72673-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72673-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72673-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="72673-106">Attributes and Elements</span></span>  
 <span data-ttu-id="72673-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72673-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72673-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="72673-108">Attributes</span></span>  
  
|<span data-ttu-id="72673-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="72673-109">Attributes</span></span>|<span data-ttu-id="72673-110">Description</span><span class="sxs-lookup"><span data-stu-id="72673-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="72673-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="72673-111">Optional.</span></span> <span data-ttu-id="72673-112">Serileştirme modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="72673-112">Specifies the serialization mode.</span></span> <span data-ttu-id="72673-113">Birine ayarlayın <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="72673-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="72673-114">Varsayılan **gidiş dönüş**'dir.</span><span class="sxs-lookup"><span data-stu-id="72673-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72673-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="72673-115">Child Elements</span></span>  
 <span data-ttu-id="72673-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="72673-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72673-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="72673-117">Parent Elements</span></span>  
  
|<span data-ttu-id="72673-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="72673-118">Element</span></span>|<span data-ttu-id="72673-119">Description</span><span class="sxs-lookup"><span data-stu-id="72673-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72673-120">dizileştirme mekanizmasını System.xml.Serialization</span><span class="sxs-lookup"><span data-stu-id="72673-120">system.xml.serialization</span></span>|<span data-ttu-id="72673-121">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="72673-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72673-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72673-122">Remarks</span></span>  
 <span data-ttu-id="72673-123">.NET Framework sürüm 1,0, 1,1, 2,0 ve sonraki sürümlerinde, bu özellik **Yerel**olarak ayarlandığında <xref:System.DateTime> nesneler her zaman yerel saat olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="72673-123">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="72673-124">Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="72673-124">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="72673-125">.NET Framework eski sürümleriyle uyumluluğu sağlamak için bu özelliği **Yerel** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72673-125">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="72673-126">Sürüm 2,0 ' de ve bu özelliğe sahip .NET Framework sonraki sürümlerinde, yukarı **dönüş**olarak ayarlanan <xref:System.DateTime> nesneler, yerel, UTC veya belirtilmeyen bir saat diliminde olup olmadıklarını belirleyecek şekilde incelenir.</span><span class="sxs-lookup"><span data-stu-id="72673-126">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="72673-127"><xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="72673-127">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="72673-128">Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.</span><span class="sxs-lookup"><span data-stu-id="72673-128">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72673-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72673-129">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="72673-130">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="72673-130">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="72673-131">\<schemaImporterExtensions>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="72673-131">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="72673-132">\<add>İçin öğesi\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="72673-132">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="72673-133">\<system.xml.serialization>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="72673-133">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)

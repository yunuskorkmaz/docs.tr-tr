---
title: <dateTimeSerialization> Öğesi
description: Bu makalede <dateTimeSerialization> , DateTime nesnelerinin serileştirme modunu belirleyen öğesi açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 90ae911c8942fef7a9e8238921990b0a52a47ca0
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281762"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="6065e-103">\<dateTimeSerialization> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6065e-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="6065e-104">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6065e-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="6065e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6065e-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6065e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6065e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6065e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6065e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6065e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6065e-108">Attributes</span></span>  
  
|<span data-ttu-id="6065e-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6065e-109">Attributes</span></span>|<span data-ttu-id="6065e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6065e-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="6065e-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6065e-111">Optional.</span></span> <span data-ttu-id="6065e-112">Serileştirme modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6065e-112">Specifies the serialization mode.</span></span> <span data-ttu-id="6065e-113">Birine ayarlayın <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="6065e-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="6065e-114">Varsayılan **gidiş dönüş** 'dir.</span><span class="sxs-lookup"><span data-stu-id="6065e-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6065e-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6065e-115">Child Elements</span></span>  
 <span data-ttu-id="6065e-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="6065e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6065e-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6065e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6065e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="6065e-118">Element</span></span>|<span data-ttu-id="6065e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6065e-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6065e-120">dizileştirme mekanizmasını System.xml.Serialization</span><span class="sxs-lookup"><span data-stu-id="6065e-120">system.xml.serialization</span></span>|<span data-ttu-id="6065e-121">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="6065e-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6065e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6065e-122">Remarks</span></span>  

<span data-ttu-id="6065e-123">Bu özellik **Yerel** olarak ayarlandığında, <xref:System.DateTime> nesneler her zaman yerel saat olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6065e-123">When this property is set to **Local** , <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="6065e-124">Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="6065e-124">That is, local time zone information is always included with the serialized data.</span></span>
  
<span data-ttu-id="6065e-125">Bu özellik **gidiş dönüş** olarak ayarlandığında, <xref:System.DateTime> nesneler yerel, UTC veya belirtilmemiş bir saat diliminde olup olmadığını belirleyecek şekilde incelenir.</span><span class="sxs-lookup"><span data-stu-id="6065e-125">When this property is set to **Roundtrip** , <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="6065e-126"><xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="6065e-126">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="6065e-127">Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.</span><span class="sxs-lookup"><span data-stu-id="6065e-127">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6065e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6065e-128">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="6065e-129">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6065e-129">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="6065e-130">\<schemaImporterExtensions> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6065e-130">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="6065e-131">\<add> İçin öğesi \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="6065e-131">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="6065e-132">\<system.xml.serialization> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6065e-132">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)

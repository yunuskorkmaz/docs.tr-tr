---
title: <dateTimeSerialization> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 180a4942dd4b701b56fe4788d5f8cd8607faaedd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459267"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="52bdc-102">\<dateTimeSerialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="52bdc-102">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="52bdc-103">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="52bdc-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="52bdc-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="52bdc-104">\<configuration></span></span>  
<span data-ttu-id="52bdc-105">\<dateTimeSerialization ></span><span class="sxs-lookup"><span data-stu-id="52bdc-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52bdc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52bdc-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52bdc-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="52bdc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="52bdc-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52bdc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52bdc-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52bdc-109">Attributes</span></span>  
  
|<span data-ttu-id="52bdc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52bdc-110">Attributes</span></span>|<span data-ttu-id="52bdc-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52bdc-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="52bdc-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="52bdc-112">Optional.</span></span> <span data-ttu-id="52bdc-113">Serileştirme modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="52bdc-113">Specifies the serialization mode.</span></span> <span data-ttu-id="52bdc-114">Birine ayarlayın <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="52bdc-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="52bdc-115">Varsayılan **gidiş dönüş**'dir.</span><span class="sxs-lookup"><span data-stu-id="52bdc-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52bdc-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="52bdc-116">Child Elements</span></span>  
 <span data-ttu-id="52bdc-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="52bdc-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52bdc-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="52bdc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="52bdc-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="52bdc-119">Element</span></span>|<span data-ttu-id="52bdc-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52bdc-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52bdc-121">dizileştirme mekanizmasını System.xml.Serialization</span><span class="sxs-lookup"><span data-stu-id="52bdc-121">system.xml.serialization</span></span>|<span data-ttu-id="52bdc-122">XML serileştirmesini denetlemek için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="52bdc-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52bdc-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52bdc-123">Remarks</span></span>  
 <span data-ttu-id="52bdc-124">.NET Framework sürüm 1,0, 1,1, 2,0 ve sonraki sürümlerinde, bu özellik **Yerel**olarak ayarlandığında <xref:System.DateTime> nesneleri her zaman yerel saat olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="52bdc-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="52bdc-125">Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="52bdc-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="52bdc-126">.NET Framework eski sürümleriyle uyumluluğu sağlamak için bu özelliği **Yerel** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="52bdc-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="52bdc-127">Sürüm 2,0 ' de ve bu özelliği yukarı **dönüş**olarak ayarlanmış .NET Framework sonraki sürümlerinde, <xref:System.DateTime> nesneleri yerel, UTC veya belirtilmeyen bir saat diliminde olup olmadıklarını belirleyecek şekilde incelenir.</span><span class="sxs-lookup"><span data-stu-id="52bdc-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="52bdc-128"><xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="52bdc-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="52bdc-129">Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.</span><span class="sxs-lookup"><span data-stu-id="52bdc-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52bdc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52bdc-130">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="52bdc-131">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="52bdc-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="52bdc-132">\<SchemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="52bdc-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="52bdc-133">\<SchemaImporterExtensions için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="52bdc-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="52bdc-134">System. xml. Serialization > öğesi \<</span><span class="sxs-lookup"><span data-stu-id="52bdc-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)

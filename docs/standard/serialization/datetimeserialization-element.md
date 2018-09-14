---
title: '&lt;dateTimeSerialization&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: cd275cdbc51c86b1d774058db839c38349b319a6
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515463"
---
# <a name="ltdatetimeserializationgt-element"></a><span data-ttu-id="d879b-102">&lt;dateTimeSerialization&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="d879b-102">&lt;dateTimeSerialization&gt; Element</span></span>
<span data-ttu-id="d879b-103">Serileştirme modu belirler <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d879b-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="d879b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d879b-104">\<configuration></span></span>  
<span data-ttu-id="d879b-105">\<dateTimeSerialization ></span><span class="sxs-lookup"><span data-stu-id="d879b-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d879b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d879b-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d879b-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d879b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d879b-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d879b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d879b-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d879b-109">Attributes</span></span>  
  
|<span data-ttu-id="d879b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d879b-110">Attributes</span></span>|<span data-ttu-id="d879b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d879b-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="d879b-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d879b-112">Optional.</span></span> <span data-ttu-id="d879b-113">Serileştirme modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d879b-113">Specifies the serialization mode.</span></span> <span data-ttu-id="d879b-114">Birine ayarlayın <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="d879b-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="d879b-115">Varsayılan değer **gidiş dönüş**.</span><span class="sxs-lookup"><span data-stu-id="d879b-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d879b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d879b-116">Child Elements</span></span>  
 <span data-ttu-id="d879b-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="d879b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d879b-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d879b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d879b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="d879b-119">Element</span></span>|<span data-ttu-id="d879b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d879b-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d879b-121">dizileştirme mekanizmasını System.xml.Serialization</span><span class="sxs-lookup"><span data-stu-id="d879b-121">system.xml.serialization</span></span>|<span data-ttu-id="d879b-122">XML serileştirme denetlemek için üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="d879b-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d879b-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d879b-123">Remarks</span></span>  
 <span data-ttu-id="d879b-124">Sürümlerinde 1.0, 1.1, 2.0 ve sonraki sürümlerinde bu özelliği ayarlandığında .NET Framework, **yerel**, <xref:System.DateTime> nesneler her zaman yerel saat biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="d879b-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="d879b-125">Diğer bir deyişle, yerel saat dilimi bilgilerini her zaman serileştirilmiş verilerle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="d879b-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="d879b-126">Bu özellik kümesine **yerel** .NET Framework'ün önceki sürümlerle uyumluluk sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d879b-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d879b-127">Sürüm 2.0 ve bu özellik kümesine sahip sonraki sürümlerinde .NET Framework'ün **gidiş dönüş**, <xref:System.DateTime> nesneler incelenebilen yerel, UTC veya belirtilmeyen bir saat dilimi olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="d879b-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="d879b-128"><xref:System.DateTime> Nesneleri sonra bu bilgileri korunur bir şekilde serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="d879b-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="d879b-129">Bu varsayılan davranış ve eski sürümleri framework ile iletişim kuran değil tüm yeni uygulamalar için önerilen davranışı.</span><span class="sxs-lookup"><span data-stu-id="d879b-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d879b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d879b-130">See also</span></span>

- <xref:System.DateTime>  
- <xref:System.Xml.Serialization.XmlSchemaImporter>  
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
- [<span data-ttu-id="d879b-131">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d879b-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="d879b-132">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="d879b-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
- [<span data-ttu-id="d879b-133">\<Ekle > öğesi için \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="d879b-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)  
- [<span data-ttu-id="d879b-134">\<System.xml.Serialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="d879b-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)

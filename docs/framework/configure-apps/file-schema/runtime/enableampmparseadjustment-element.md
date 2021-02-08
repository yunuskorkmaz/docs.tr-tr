---
description: 'Daha fazla bilgi edinin: <EnableAmPmParseAdjustment> öğesi'
title: <EnableAmPmParseAdjustment> Öğesi
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 86fd04ab536f44f0cffdb5a37f4718fc03698485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787064"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="1851c-103">\<EnableAmPmParseAdjustment> Öğesi</span><span class="sxs-lookup"><span data-stu-id="1851c-103">\<EnableAmPmParseAdjustment> Element</span></span>

<span data-ttu-id="1851c-104">Tarih ve saat ayrıştırma yöntemlerinin, gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1851c-104">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="1851c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1851c-105">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1851c-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1851c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1851c-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1851c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1851c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1851c-108">Attributes</span></span>  
  
|<span data-ttu-id="1851c-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1851c-109">Attribute</span></span>|<span data-ttu-id="1851c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1851c-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1851c-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1851c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="1851c-112">Tarih ve saat ayrıştırma yöntemlerinin, yalnızca bir gün, ay, saat ve i/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1851c-112">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="1851c-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1851c-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="1851c-114">Değer</span><span class="sxs-lookup"><span data-stu-id="1851c-114">Value</span></span>|<span data-ttu-id="1851c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1851c-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1851c-116">0</span><span class="sxs-lookup"><span data-stu-id="1851c-116">0</span></span>|<span data-ttu-id="1851c-117">Tarih ve saat ayrıştırma yöntemleri yalnızca gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanan kuralları kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="1851c-117">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="1851c-118">1</span><span class="sxs-lookup"><span data-stu-id="1851c-118">1</span></span>|<span data-ttu-id="1851c-119">Tarih ve saat ayrıştırma yöntemleri yalnızca gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanan kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1851c-119">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1851c-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1851c-120">Child Elements</span></span>  

 <span data-ttu-id="1851c-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="1851c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1851c-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1851c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1851c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="1851c-123">Element</span></span>|<span data-ttu-id="1851c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1851c-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1851c-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1851c-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1851c-126">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1851c-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1851c-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1851c-127">Remarks</span></span>  

 <span data-ttu-id="1851c-128">`<EnableAmPmParseAdjustment>`Öğesi, aşağıdaki yöntemlerin sayısal bir gün ve ay içeren bir tarih dizesini nasıl ayrıştırarak bir saat ve bır har/PM göstergesini ("4/10 6" gibi) denetler:</span><span class="sxs-lookup"><span data-stu-id="1851c-128">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="1851c-129">Başka desenler etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="1851c-129">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="1851c-130">`<EnableAmPmParseAdjustment>`Öğesinin <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> ,, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1851c-130">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1851c-131">.NET Core ve .NET Native 'de, ayarlanan saat/PM ayrıştırma kuralları varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="1851c-131">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="1851c-132">Ayrıştırma ayarlama kuralı etkinleştirilmemişse, dizenin ilk basamak, 12 saatlik saatin saati olarak yorumlanır ve bu dizenin geri kalanı, ı/PM göstergesi hariç sayılır.</span><span class="sxs-lookup"><span data-stu-id="1851c-132">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="1851c-133">Ayrıştırma yöntemi tarafından döndürülen tarih ve saat, geçerli tarih ve Tarih dizesinden çıkarılan günün saati içerir.</span><span class="sxs-lookup"><span data-stu-id="1851c-133">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="1851c-134">Ayrıştırma ayarlama kuralı etkinleştirilirse, ayrıştırma yöntemi geçerli yıla ait günü ve ayı yorumlayıp saati 12 saatlik saatin saati olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="1851c-134">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="1851c-135">Aşağıdaki tabloda, <xref:System.DateTime> <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> yöntemi " `<EnableAmPmParseAdjustment>` `enabled` 0" veya "1" olarak ayarlanan öğenin özelliği Ile "" 4/10 6 har "dizesini ayrıştırmak için kullanılan değerin farkı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1851c-135">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="1851c-136">Bugünün tarihinin 5 Ocak 2017 olduğunu varsayar ve belirtilen kültürün "G" biçim dizesi kullanılarak biçimlendirilip biçimlendirildiğine ilişkin tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1851c-136">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="1851c-137">Kültür adı</span><span class="sxs-lookup"><span data-stu-id="1851c-137">Culture name</span></span>|<span data-ttu-id="1851c-138">etkin = "0"</span><span class="sxs-lookup"><span data-stu-id="1851c-138">enabled="0"</span></span>|<span data-ttu-id="1851c-139">etkin = "1"</span><span class="sxs-lookup"><span data-stu-id="1851c-139">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="1851c-140">en-US</span><span class="sxs-lookup"><span data-stu-id="1851c-140">en-US</span></span>|<span data-ttu-id="1851c-141">1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="1851c-141">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="1851c-142">4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="1851c-142">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="1851c-143">en-GB</span><span class="sxs-lookup"><span data-stu-id="1851c-143">en-GB</span></span>|<span data-ttu-id="1851c-144">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="1851c-144">5/1/2017 6:00:00</span></span>|<span data-ttu-id="1851c-145">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="1851c-145">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1851c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1851c-146">See also</span></span>

- [<span data-ttu-id="1851c-147">\<runtime> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="1851c-147">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="1851c-148">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="1851c-148">\<configuration> Element</span></span>](../configuration-element.md)

---
title: <EnableAmPmParseAdjustment> Öğesi
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 8920e51fcaaca5cb78b80a99ea321163c9b5240f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117365"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="844be-102">\<Enableampmparseayarlaması > öğesi</span><span class="sxs-lookup"><span data-stu-id="844be-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="844be-103">Tarih ve saat ayrıştırma yöntemlerinin, gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="844be-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
<span data-ttu-id="844be-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="844be-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="844be-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="844be-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="844be-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Enableampmparseayarlaması >**</span><span class="sxs-lookup"><span data-stu-id="844be-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="844be-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="844be-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="844be-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="844be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="844be-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="844be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="844be-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="844be-110">Attributes</span></span>  
  
|<span data-ttu-id="844be-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="844be-111">Attribute</span></span>|<span data-ttu-id="844be-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="844be-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="844be-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="844be-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="844be-114">Tarih ve saat ayrıştırma yöntemlerinin, yalnızca bir gün, ay, saat ve i/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="844be-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="844be-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="844be-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="844be-116">Değer</span><span class="sxs-lookup"><span data-stu-id="844be-116">Value</span></span>|<span data-ttu-id="844be-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="844be-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="844be-118">0</span><span class="sxs-lookup"><span data-stu-id="844be-118">0</span></span>|<span data-ttu-id="844be-119">Tarih ve saat ayrıştırma yöntemleri yalnızca gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanan kuralları kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="844be-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="844be-120">1\.</span><span class="sxs-lookup"><span data-stu-id="844be-120">1</span></span>|<span data-ttu-id="844be-121">Tarih ve saat ayrıştırma yöntemleri yalnızca gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanan kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="844be-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="844be-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="844be-122">Child Elements</span></span>  
 <span data-ttu-id="844be-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="844be-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="844be-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="844be-124">Parent Elements</span></span>  
  
|<span data-ttu-id="844be-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="844be-125">Element</span></span>|<span data-ttu-id="844be-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="844be-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="844be-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="844be-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="844be-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="844be-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="844be-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="844be-129">Remarks</span></span>  
 <span data-ttu-id="844be-130">`<EnableAmPmParseAdjustment>` öğesi, aşağıdaki yöntemlerin sayısal bir gün ve ay içeren bir tarih dizesini nasıl ayrıştırarak bir saat ve bir har/PM göstergesini ("4/10 6" gibi) denetler:</span><span class="sxs-lookup"><span data-stu-id="844be-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="844be-131">Başka desenler etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="844be-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="844be-132">`<EnableAmPmParseAdjustment>` öğesinin <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="844be-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="844be-133">.NET Core ve .NET Native 'de, ayarlanan saat/PM ayrıştırma kuralları varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="844be-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="844be-134">Ayrıştırma ayarlama kuralı etkinleştirilmemişse, dizenin ilk basamak, 12 saatlik saatin saati olarak yorumlanır ve bu dizenin geri kalanı, ı/PM göstergesi hariç sayılır.</span><span class="sxs-lookup"><span data-stu-id="844be-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="844be-135">Ayrıştırma yöntemi tarafından döndürülen tarih ve saat, geçerli tarih ve Tarih dizesinden çıkarılan günün saati içerir.</span><span class="sxs-lookup"><span data-stu-id="844be-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="844be-136">Ayrıştırma ayarlama kuralı etkinleştirilirse, ayrıştırma yöntemi geçerli yıla ait günü ve ayı yorumlayıp saati 12 saatlik saatin saati olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="844be-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="844be-137">Aşağıdaki tabloda, `<EnableAmPmParseAdjustment>` öğenin `enabled` özelliği "0" veya "1" olarak ayarlanmış "" 4/10 6 "dizesini ayrıştırmak için <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> yöntemi kullanıldığında <xref:System.DateTime> değerindeki fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="844be-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="844be-138">Bugünün tarihinin 5 Ocak 2017 olduğunu varsayar ve belirtilen kültürün "G" biçim dizesi kullanılarak biçimlendirilip biçimlendirildiğine ilişkin tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="844be-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="844be-139">Kültür adı</span><span class="sxs-lookup"><span data-stu-id="844be-139">Culture name</span></span>|<span data-ttu-id="844be-140">etkin = "0"</span><span class="sxs-lookup"><span data-stu-id="844be-140">enabled="0"</span></span>|<span data-ttu-id="844be-141">etkin = "1"</span><span class="sxs-lookup"><span data-stu-id="844be-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="844be-142">en-US</span><span class="sxs-lookup"><span data-stu-id="844be-142">en-US</span></span>|<span data-ttu-id="844be-143">1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="844be-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="844be-144">4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="844be-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="844be-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="844be-145">en-GB</span></span>|<span data-ttu-id="844be-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="844be-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="844be-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="844be-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="844be-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="844be-148">See also</span></span>

- [<span data-ttu-id="844be-149">\<Runtime > öğesi</span><span class="sxs-lookup"><span data-stu-id="844be-149">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="844be-150">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="844be-150">\<configuration> Element</span></span>](../configuration-element.md)

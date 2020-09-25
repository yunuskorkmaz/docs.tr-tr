---
title: <EnableAmPmParseAdjustment> Öğesi
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: f935f213e1bca8dac7a5401970bc6183575e2301
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167242"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="afb46-102">\<EnableAmPmParseAdjustment> Öğesi</span><span class="sxs-lookup"><span data-stu-id="afb46-102">\<EnableAmPmParseAdjustment> Element</span></span>

<span data-ttu-id="afb46-103">Tarih ve saat ayrıştırma yöntemlerinin, gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="afb46-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="afb46-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="afb46-104">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afb46-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="afb46-105">Attributes and Elements</span></span>  

 <span data-ttu-id="afb46-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="afb46-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afb46-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="afb46-107">Attributes</span></span>  
  
|<span data-ttu-id="afb46-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="afb46-108">Attribute</span></span>|<span data-ttu-id="afb46-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afb46-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="afb46-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="afb46-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="afb46-111">Tarih ve saat ayrıştırma yöntemlerinin, yalnızca bir gün, ay, saat ve i/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="afb46-111">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="afb46-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="afb46-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="afb46-113">Değer</span><span class="sxs-lookup"><span data-stu-id="afb46-113">Value</span></span>|<span data-ttu-id="afb46-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afb46-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="afb46-115">0</span><span class="sxs-lookup"><span data-stu-id="afb46-115">0</span></span>|<span data-ttu-id="afb46-116">Tarih ve saat ayrıştırma yöntemleri yalnızca gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanan kuralları kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="afb46-116">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="afb46-117">1</span><span class="sxs-lookup"><span data-stu-id="afb46-117">1</span></span>|<span data-ttu-id="afb46-118">Tarih ve saat ayrıştırma yöntemleri yalnızca gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanan kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="afb46-118">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afb46-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="afb46-119">Child Elements</span></span>  

 <span data-ttu-id="afb46-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="afb46-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afb46-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="afb46-121">Parent Elements</span></span>  
  
|<span data-ttu-id="afb46-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="afb46-122">Element</span></span>|<span data-ttu-id="afb46-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afb46-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="afb46-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="afb46-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="afb46-125">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="afb46-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afb46-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afb46-126">Remarks</span></span>  

 <span data-ttu-id="afb46-127">`<EnableAmPmParseAdjustment>`Öğesi, aşağıdaki yöntemlerin sayısal bir gün ve ay içeren bir tarih dizesini nasıl ayrıştırarak bir saat ve bır har/PM göstergesini ("4/10 6" gibi) denetler:</span><span class="sxs-lookup"><span data-stu-id="afb46-127">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="afb46-128">Başka desenler etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="afb46-128">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="afb46-129">`<EnableAmPmParseAdjustment>`Öğesinin <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> ,, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="afb46-129">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="afb46-130">.NET Core ve .NET Native 'de, ayarlanan saat/PM ayrıştırma kuralları varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="afb46-130">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="afb46-131">Ayrıştırma ayarlama kuralı etkinleştirilmemişse, dizenin ilk basamak, 12 saatlik saatin saati olarak yorumlanır ve bu dizenin geri kalanı, ı/PM göstergesi hariç sayılır.</span><span class="sxs-lookup"><span data-stu-id="afb46-131">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="afb46-132">Ayrıştırma yöntemi tarafından döndürülen tarih ve saat, geçerli tarih ve Tarih dizesinden çıkarılan günün saati içerir.</span><span class="sxs-lookup"><span data-stu-id="afb46-132">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="afb46-133">Ayrıştırma ayarlama kuralı etkinleştirilirse, ayrıştırma yöntemi geçerli yıla ait günü ve ayı yorumlayıp saati 12 saatlik saatin saati olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="afb46-133">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="afb46-134">Aşağıdaki tabloda, <xref:System.DateTime> <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> yöntemi " `<EnableAmPmParseAdjustment>` `enabled` 0" veya "1" olarak ayarlanan öğenin özelliği Ile "" 4/10 6 har "dizesini ayrıştırmak için kullanılan değerin farkı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="afb46-134">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="afb46-135">Bugünün tarihinin 5 Ocak 2017 olduğunu varsayar ve belirtilen kültürün "G" biçim dizesi kullanılarak biçimlendirilip biçimlendirildiğine ilişkin tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="afb46-135">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="afb46-136">Kültür adı</span><span class="sxs-lookup"><span data-stu-id="afb46-136">Culture name</span></span>|<span data-ttu-id="afb46-137">etkin = "0"</span><span class="sxs-lookup"><span data-stu-id="afb46-137">enabled="0"</span></span>|<span data-ttu-id="afb46-138">etkin = "1"</span><span class="sxs-lookup"><span data-stu-id="afb46-138">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="afb46-139">tr-TR</span><span class="sxs-lookup"><span data-stu-id="afb46-139">en-US</span></span>|<span data-ttu-id="afb46-140">1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="afb46-140">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="afb46-141">4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="afb46-141">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="afb46-142">en-GB</span><span class="sxs-lookup"><span data-stu-id="afb46-142">en-GB</span></span>|<span data-ttu-id="afb46-143">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="afb46-143">5/1/2017 6:00:00</span></span>|<span data-ttu-id="afb46-144">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="afb46-144">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afb46-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afb46-145">See also</span></span>

- [<span data-ttu-id="afb46-146">\<runtime> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="afb46-146">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="afb46-147">\<configuration> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="afb46-147">\<configuration> Element</span></span>](../configuration-element.md)

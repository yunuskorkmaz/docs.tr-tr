---
title: '&lt;EnableAmPmParseAdjustment&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf56a2720ab407d05b8356280913445c15a17020
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611080"
---
# <a name="ltenableampmparseadjustmentgt-element"></a><span data-ttu-id="f867e-102">&lt;EnableAmPmParseAdjustment&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="f867e-102">&lt;EnableAmPmParseAdjustment&gt; Element</span></span>
<span data-ttu-id="f867e-103">Tarih ve saat yöntemleri ayrıştırma ayarlanmış bir kural kümesi bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırılacak kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f867e-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="f867e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f867e-104">\<configuration></span></span>  
 <span data-ttu-id="f867e-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="f867e-105">\<runtime></span></span>  
<span data-ttu-id="f867e-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="f867e-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f867e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f867e-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f867e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f867e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f867e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f867e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f867e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f867e-110">Attributes</span></span>  
  
|<span data-ttu-id="f867e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f867e-111">Attribute</span></span>|<span data-ttu-id="f867e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f867e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f867e-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f867e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f867e-114">Tarih ve saat yöntemleri ayrıştırma ayarlanmış bir kural kümesi yalnızca bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırılacak kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f867e-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="f867e-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f867e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f867e-116">Değer</span><span class="sxs-lookup"><span data-stu-id="f867e-116">Value</span></span>|<span data-ttu-id="f867e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f867e-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f867e-118">0</span><span class="sxs-lookup"><span data-stu-id="f867e-118">0</span></span>|<span data-ttu-id="f867e-119">Tarih ve saat yöntemleri ayrıştırma düzeltilen kurallar yalnızca bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırma için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="f867e-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="f867e-120">1.</span><span class="sxs-lookup"><span data-stu-id="f867e-120">1</span></span>|<span data-ttu-id="f867e-121">Tarih ve saat yöntemleri ayrıştırma yalnızca bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırma için ayarlanmış kuralları kullanın.</span><span class="sxs-lookup"><span data-stu-id="f867e-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f867e-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f867e-122">Child Elements</span></span>  
 <span data-ttu-id="f867e-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="f867e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f867e-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f867e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f867e-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="f867e-125">Element</span></span>|<span data-ttu-id="f867e-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f867e-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f867e-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f867e-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f867e-128">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f867e-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f867e-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f867e-129">Remarks</span></span>  
 <span data-ttu-id="f867e-130">`<EnableAmPmParseAdjustment>` Öğe denetimleri nasıl aşağıdaki yöntemlerden bir sayısal günlük ve aylık bir saat ve bir AM/PM göstergesi (örneğin, "4/10 6 AM") içeren bir tarih dizesi ayrıştırılamıyor:</span><span class="sxs-lookup"><span data-stu-id="f867e-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f867e-131">Herhangi bir desen etkilenir.</span><span class="sxs-lookup"><span data-stu-id="f867e-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="f867e-132">`<EnableAmPmParseAdjustment>` Öğesi hiçbir etkiye sahiptir <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f867e-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f867e-133">.NET Core ve .NET Native, ayarlanan AM/PM ayrıştırma kurallarını varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="f867e-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="f867e-134">Ayrıştırma ayarlama kuralı etkin değilse, dizenin ilk basamak 12 saatlik düzende saatlik yorumlanır ve AM/PM göstergesi dışında dizenin geri kalanı göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f867e-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="f867e-135">Ayrıştırma yöntem tarafından döndürülen saat ve tarihi geçerli tarih ve saat ve tarih dizesindeki ayıklanan oluşur.</span><span class="sxs-lookup"><span data-stu-id="f867e-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="f867e-136">Yöntemi ayrıştırma ayrıştırma ayarlama kuralı etkinleştirilirse, ait geçerli yıl, ay ve günü yorumlar ve saati 12 saatlik düzende saatlik olarak yorumlayın.</span><span class="sxs-lookup"><span data-stu-id="f867e-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="f867e-137">Aşağıdaki tabloda, fark gösterilmektedir <xref:System.DateTime> değeri <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> dizeyi ayrıştırmak için kullanılan yöntemi "" 4/10 6 AM"ile `<EnableAmPmParseAdjustment>` öğenin `enabled` özelliği"0"veya"1"olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f867e-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="f867e-138">Bu, bugünün tarihi 5 Ocak 2017 ve gibi belirtilen kültürün "G" biçim dizesi kullanılarak biçimlendirilir tarihi görüntüler varsayar.</span><span class="sxs-lookup"><span data-stu-id="f867e-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="f867e-139">Kültür adı</span><span class="sxs-lookup"><span data-stu-id="f867e-139">Culture name</span></span>|<span data-ttu-id="f867e-140">Etkin = "0"</span><span class="sxs-lookup"><span data-stu-id="f867e-140">enabled="0"</span></span>|<span data-ttu-id="f867e-141">Etkin = "1"</span><span class="sxs-lookup"><span data-stu-id="f867e-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="f867e-142">en-US</span><span class="sxs-lookup"><span data-stu-id="f867e-142">en-US</span></span>|<span data-ttu-id="f867e-143">1/5/2017 4:00: 00'DA</span><span class="sxs-lookup"><span data-stu-id="f867e-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="f867e-144">4/10/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="f867e-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="f867e-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="f867e-145">en-GB</span></span>|<span data-ttu-id="f867e-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="f867e-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="f867e-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="f867e-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f867e-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f867e-148">See Also</span></span>  
- [<span data-ttu-id="f867e-149">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="f867e-149">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
- [<span data-ttu-id="f867e-150">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="f867e-150">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)

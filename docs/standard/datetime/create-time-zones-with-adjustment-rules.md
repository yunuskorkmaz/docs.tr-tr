---
title: "Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75e1867e810090bf35a0dfc7def5785747f94382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="9934d-102">Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="9934d-102">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="9934d-103">Bir uygulama tarafından istenen kesin saat dilimi bilgilerini çeşitli nedenlerle belirli bir sistemde mevcut değil:</span><span class="sxs-lookup"><span data-stu-id="9934d-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="9934d-104">Saat dilimi yerel sistemin kayıt defterinde hiçbir zaman tanımlamıştır.</span><span class="sxs-lookup"><span data-stu-id="9934d-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="9934d-105">Saat dilimi hakkındaki verileri değiştirilemiyor veya kayıt defteri anahtarından kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="9934d-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="9934d-106">Saat dilimi, belirli bir geçmiş dönem için saat dilimi düzeltmeleri hakkında doğru bilgileri yok.</span><span class="sxs-lookup"><span data-stu-id="9934d-106">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="9934d-107">Bu durumlarda, çağırabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanızın gerektirdiği saat dilimi tanımlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9934d-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="9934d-108">Bu yöntem aşırı ile veya ayarlama kuralları olmadan saat dilimi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9934d-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="9934d-109">Saat diliminin gün ışığından yararlanma saati destekliyorsa, ayarlamalar ya da sabit veya değişken ayarlama kuralları ile tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9934d-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="9934d-110">(Bu koşulları tanımları için "Saat dilimi terminolojisi" bölümüne bakın [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="9934d-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9934d-111">Özel saat dilimlerini çağrılarak oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kayıt defterine eklenmedi.</span><span class="sxs-lookup"><span data-stu-id="9934d-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="9934d-112">Bunun yerine, bunlar yalnızca tarafından döndürülen nesne başvurusu aracılığıyla erişilebilen <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="9934d-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="9934d-113">Bu konuda ayarlama kuralları ile saat dilimi oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9934d-113">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="9934d-114">Yaz Saati ayarlama kuralları desteklemeyen bir saat dilimi oluşturmak için bkz: [nasıl yapılır: oluşturmak saat dilimleri olmadan ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="9934d-114">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="9934d-115">Bir saat dilimi ayarlama kuralları kayan oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9934d-115">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="9934d-116">(Yani, her transition from uzağa içindir ve Standart Saati için belirli bir zaman aralığı içinde geri) her ayarlaması için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="9934d-116">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="9934d-117">Saat dilimi ayarlaması için başlangıç geçiş süresi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9934d-117">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="9934d-118">Çağırmalısınız <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> yöntemi ve bu geçirin bir <xref:System.DateTime> geçişi, geçiş ayın tanımlayan bir tamsayı değeri, geçiş oluştuğu, haftanın tanımlayan bir tamsayı değeri süresini tanımlayan değeri ve <xref:System.DayOfWeek> geçiş oluştuğu haftanın gününü tanımlayan değeri.</span><span class="sxs-lookup"><span data-stu-id="9934d-118">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="9934d-119">Bu yöntem çağrısı başlatır bir <xref:System.TimeZoneInfo.TransitionTime> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9934d-119">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="9934d-120">Saat dilimi ayarlaması için bitiş geçiş süresi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9934d-120">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="9934d-121">Bu, başka bir çağrıyı gerektirir <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9934d-121">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9934d-122">Bu yöntem çağrısı ikinci bir örneğini oluşturur <xref:System.TimeZoneInfo.TransitionTime> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9934d-122">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="9934d-123">Çağrı <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> yöntemi ve etkili başlangıç ve bitiş tarihleri ayarlama geçirin bir <xref:System.TimeSpan> süreyi geçişi ve iki tanımlayan nesne <xref:System.TimeZoneInfo.TransitionTime> ne zaman tanımlayan nesneleri gün ışığından gelen ve giden geçişleri zaman oluşur.</span><span class="sxs-lookup"><span data-stu-id="9934d-123">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="9934d-124">Bu yöntem çağrısı başlatır bir <xref:System.TimeZoneInfo.AdjustmentRule> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9934d-124">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="9934d-125">Ata <xref:System.TimeZoneInfo.AdjustmentRule> bir dizi nesneyi <xref:System.TimeZoneInfo.AdjustmentRule> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9934d-125">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="9934d-126">Saat diliminin görünen adı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9934d-126">Define the time zone's display name.</span></span> <span data-ttu-id="9934d-127">Görünen ad saat diliminin uzaklığı gelen Eşgüdümlü Evrensel Saat (UTC) parantez içine alınmış ve saat dilimi, bir veya birkaçı Şehir saat dilimi ya da bir veya daha fazla cou tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izler girişleri veya saat dilimi bölgelerde.</span><span class="sxs-lookup"><span data-stu-id="9934d-127">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="9934d-128">Saat diliminin standart saat adını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9934d-128">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="9934d-129">Genellikle, bu dize saat diliminin tanımlayıcı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9934d-129">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="9934d-130">Saat diliminin gün ışığından yararlanma saati adını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9934d-130">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="9934d-131">Saat diliminin standart adından farklı bir kimlik kullanmak istiyorsanız, saat dilimi tanımlayıcı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9934d-131">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="9934d-132">Örneği bir <xref:System.TimeSpan> UTC saat diliminin uzaklığı tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="9934d-132">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="9934d-133">Saat dilimi UTC sonraki sürelerine sahip bir pozitif uzaklığı vardır.</span><span class="sxs-lookup"><span data-stu-id="9934d-133">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="9934d-134">Saat dilimi UTC önceki sürelerine sahip negatif uzaklık vardır.</span><span class="sxs-lookup"><span data-stu-id="9934d-134">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="9934d-135">Çağrı <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> yeni saat dilimine örneği oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9934d-135">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="9934d-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="9934d-136">Example</span></span>

<span data-ttu-id="9934d-137">Aşağıdaki örnek, bir merkezi standart saat dilimi 1918 zaman aralıkları için mevcut çeşitli ayarlama kuralları içerir Amerika Birleşik Devletleri'nin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9934d-137">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="9934d-138">Bu örnekte oluşturulan saat dilimi birden çok ayarlama kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="9934d-138">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="9934d-139">Geçerli başlangıç ve bitiş tarihleri herhangi bir ayarı kuralın başka bir ayarlama kuralı tarihlerle çakışmadığından emin olmak için dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9934d-139">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="9934d-140">Bir çakışma varsa bir <xref:System.InvalidTimeZoneException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9934d-140">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="9934d-141">Ayarlama kuralları değişken için değeri 5 geçirilir `week` parametresinin <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> geçişi belirli bir ay son haftasında ortaya çıktığını göstermek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9934d-141">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="9934d-142">Dizi oluşturma <xref:System.TimeZoneInfo.AdjustmentRule> kullanmak için nesneleri <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> yöntem çağrısı kodu başlatmak için saat dilimi oluşturulacak ayarlamalar sayısına göre gerekli boyutu diziye.</span><span class="sxs-lookup"><span data-stu-id="9934d-142">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="9934d-143">Bunun yerine, bu kod örneği çağırır <xref:System.Collections.Generic.List%601.Add%2A> her ayarlama kuralı için genel ekleme yöntemi <xref:System.Collections.Generic.List%601> koleksiyonu <xref:System.TimeZoneInfo.AdjustmentRule> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9934d-143">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="9934d-144">Kod sonra çağırır <xref:System.Collections.Generic.List%601.CopyTo%2A> Bu koleksiyonun üyeleri dizisine kopyalamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9934d-144">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="9934d-145">Bu örnek ayrıca kullanır <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> sabit tarih ayarlamaları tanımlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9934d-145">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="9934d-146">Bu arama için benzer <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> yalnızca zaman, ay ve gün geçiş parametrelerden biri olan gerektirir dışında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9934d-146">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="9934d-147">Örnek kod aşağıdaki gibi kullanarak test edilebilir:</span><span class="sxs-lookup"><span data-stu-id="9934d-147">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="9934d-148">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="9934d-148">Compiling the code</span></span>

<span data-ttu-id="9934d-149">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9934d-149">This example requires:</span></span>

* <span data-ttu-id="9934d-150">Bir başvuru System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="9934d-150">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="9934d-151">Şu ad alanlarından alınan olduğunu:</span><span class="sxs-lookup"><span data-stu-id="9934d-151">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="9934d-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9934d-152">See also</span></span>

<span data-ttu-id="9934d-153">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="9934d-153">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span></span>

---
title: "Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma"
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
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 14c5e02ce5af03d063260af19e9dd1a970a93ab6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="7ec1a-102">Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ec1a-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="7ec1a-103">Bir uygulama tarafından istenen kesin saat dilimi bilgilerini çeşitli nedenlerle belirli bir sistemde mevcut değil:</span><span class="sxs-lookup"><span data-stu-id="7ec1a-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="7ec1a-104">Saat dilimi yerel sistemin kayıt defterinde hiçbir zaman tanımlamıştır.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="7ec1a-105">Saat dilimi hakkındaki verileri değiştirilemiyor veya kayıt defteri anahtarından kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="7ec1a-106">Saat dilimi var, ancak belirli bir geçmiş dönem için saat dilimi düzeltmeleri hakkında doğru bilgileri yok.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="7ec1a-107">Bu durumlarda, çağırabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanızın gerektirdiği saat dilimi tanımlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="7ec1a-108">Bu yöntem aşırı ile veya ayarlama kuralları olmadan saat dilimi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="7ec1a-109">Saat diliminin gün ışığından yararlanma saati destekliyorsa, ayarlamalar ya da sabit veya değişken ayarlama kuralları ile tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="7ec1a-110">(Bu koşulları tanımları için "Saat dilimi terminolojisi" bölümüne bakın [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="7ec1a-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ec1a-111">Özel saat dilimlerini çağrılarak oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kayıt defterine eklenmedi.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="7ec1a-112">Bunun yerine, bunlar yalnızca tarafından döndürülen nesne başvurusu aracılığıyla erişilebilen <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="7ec1a-113">Bu konuda ayarlama kuralları olmadan saat dilimi oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="7ec1a-114">Yaz Saati ayarlama kuralları destekleyen bir saat dilimi oluşturmak için bkz: [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="7ec1a-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="7ec1a-115">Ayarlama kuralları olmadan saat dilimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7ec1a-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="7ec1a-116">Saat diliminin görünen adı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="7ec1a-117">Görünen ad saat diliminin uzaklığı gelen Eşgüdümlü Evrensel Saat (UTC) parantez içine alınmış ve saat dilimi, bir veya birkaçı Şehir saat dilimi ya da bir veya daha fazla cou tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izler girişleri veya saat dilimi bölgelerde.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="7ec1a-118">Saat diliminin standart saat adını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="7ec1a-119">Genellikle, bu dize saat diliminin tanımlayıcı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="7ec1a-120">Saat diliminin standart adından farklı bir kimlik kullanmak istiyorsanız, saat dilimi tanımlayıcı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="7ec1a-121">Örneği bir <xref:System.TimeSpan> UTC saat diliminin uzaklığı tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="7ec1a-122">Saat dilimi UTC sonraki sürelerine sahip bir pozitif uzaklığı vardır.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="7ec1a-123">Saat dilimi UTC önceki sürelerine sahip negatif uzaklık vardır.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="7ec1a-124">Çağrı <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> yeni saat dilimine örneği oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="7ec1a-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ec1a-125">Example</span></span>

<span data-ttu-id="7ec1a-126">Aşağıdaki örnek, özel bir saat dilimi Mawson, ayarlama kuralları yok Antarktika tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="7ec1a-127">Atanan dize <xref:System.TimeZoneInfo.DisplayName%2A> özelliği tarafından kolay bir açıklama saat dilimi UTC saat diliminin uzaklığı izlendiği standart bir biçim izler.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="7ec1a-128">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="7ec1a-128">Compiling the code</span></span>

<span data-ttu-id="7ec1a-129">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7ec1a-129">This example requires:</span></span>

* <span data-ttu-id="7ec1a-130">Bir başvuru System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-130">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="7ec1a-131">Şu ad alanlarından alınan olduğunu:</span><span class="sxs-lookup"><span data-stu-id="7ec1a-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="7ec1a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ec1a-132">See also</span></span>

<span data-ttu-id="7ec1a-133">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="7ec1a-133">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span></span>

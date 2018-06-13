---
title: 'Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214e3bca811f87f4b8367b459564449d16e7c289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572908"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="20c74-102">Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="20c74-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="20c74-103">Bir uygulama tarafından istenen kesin saat dilimi bilgilerini çeşitli nedenlerle belirli bir sistemde mevcut değil:</span><span class="sxs-lookup"><span data-stu-id="20c74-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="20c74-104">Saat dilimi yerel sistemin kayıt defterinde hiçbir zaman tanımlamıştır.</span><span class="sxs-lookup"><span data-stu-id="20c74-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="20c74-105">Saat dilimi hakkındaki verileri değiştirilemiyor veya kayıt defteri anahtarından kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="20c74-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="20c74-106">Saat dilimi var, ancak belirli bir geçmiş dönem için saat dilimi düzeltmeleri hakkında doğru bilgileri yok.</span><span class="sxs-lookup"><span data-stu-id="20c74-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="20c74-107">Bu durumlarda, çağırabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanızın gerektirdiği saat dilimi tanımlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="20c74-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="20c74-108">Bu yöntem aşırı ile veya ayarlama kuralları olmadan saat dilimi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20c74-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="20c74-109">Saat diliminin gün ışığından yararlanma saati destekliyorsa, ayarlamalar ya da sabit veya değişken ayarlama kuralları ile tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20c74-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="20c74-110">(Bu koşulları tanımları için "Saat dilimi terminolojisi" bölümüne bakın [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="20c74-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20c74-111">Özel saat dilimlerini çağrılarak oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kayıt defterine eklenmedi.</span><span class="sxs-lookup"><span data-stu-id="20c74-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="20c74-112">Bunun yerine, bunlar yalnızca tarafından döndürülen nesne başvurusu aracılığıyla erişilebilen <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="20c74-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="20c74-113">Bu konuda ayarlama kuralları olmadan saat dilimi oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="20c74-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="20c74-114">Yaz Saati ayarlama kuralları destekleyen bir saat dilimi oluşturmak için bkz: [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="20c74-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="20c74-115">Ayarlama kuralları olmadan saat dilimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20c74-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="20c74-116">Saat diliminin görünen adı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="20c74-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="20c74-117">Görünen ad saat diliminin uzaklığı gelen Eşgüdümlü Evrensel Saat (UTC) parantez içine alınmış ve saat dilimi, bir veya birkaçı Şehir saat dilimi ya da bir veya daha fazla cou tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izler girişleri veya saat dilimi bölgelerde.</span><span class="sxs-lookup"><span data-stu-id="20c74-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="20c74-118">Saat diliminin standart saat adını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="20c74-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="20c74-119">Genellikle, bu dize saat diliminin tanımlayıcı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20c74-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="20c74-120">Saat diliminin standart adından farklı bir kimlik kullanmak istiyorsanız, saat dilimi tanımlayıcı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="20c74-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="20c74-121">Örneği bir <xref:System.TimeSpan> UTC saat diliminin uzaklığı tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="20c74-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="20c74-122">Saat dilimi UTC sonraki sürelerine sahip bir pozitif uzaklığı vardır.</span><span class="sxs-lookup"><span data-stu-id="20c74-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="20c74-123">Saat dilimi UTC önceki sürelerine sahip negatif uzaklık vardır.</span><span class="sxs-lookup"><span data-stu-id="20c74-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="20c74-124">Çağrı <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> yeni saat dilimine örneği oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="20c74-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="20c74-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="20c74-125">Example</span></span>

<span data-ttu-id="20c74-126">Aşağıdaki örnek, özel bir saat dilimi Mawson, ayarlama kuralları yok Antarktika tanımlar.</span><span class="sxs-lookup"><span data-stu-id="20c74-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="20c74-127">Atanan dize <xref:System.TimeZoneInfo.DisplayName%2A> özelliği tarafından kolay bir açıklama saat dilimi UTC saat diliminin uzaklığı izlendiği standart bir biçim izler.</span><span class="sxs-lookup"><span data-stu-id="20c74-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="20c74-128">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="20c74-128">Compiling the code</span></span>

<span data-ttu-id="20c74-129">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="20c74-129">This example requires:</span></span>

* <span data-ttu-id="20c74-130">Bir başvuru System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="20c74-130">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="20c74-131">Şu ad alanlarından alınan olduğunu:</span><span class="sxs-lookup"><span data-stu-id="20c74-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="20c74-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20c74-132">See also</span></span>

<span data-ttu-id="20c74-133">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="20c74-133">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span></span>

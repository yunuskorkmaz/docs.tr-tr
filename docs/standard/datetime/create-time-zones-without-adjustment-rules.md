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
ms.openlocfilehash: 1d8aae1284e9ee9871c6f201c6a00e0b547f95fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278044"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="50799-102">Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="50799-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="50799-103">Bir uygulama için gerekli kesin saat dilimi bilgileri, bazı nedenlerle belirli bir sistemde mevcut olmayabilir:</span><span class="sxs-lookup"><span data-stu-id="50799-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="50799-104">Saat dilimi, yerel sistemin kayıt defterinde hiç tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="50799-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="50799-105">Saat dilimi hakkındaki veriler, kayıt defterinden değiştirilmiş veya kaldırılmış.</span><span class="sxs-lookup"><span data-stu-id="50799-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="50799-106">Saat dilimi var, ancak belirli bir geçmiş dönem için saat dilimi ayarlamaları hakkında doğru bilgilere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="50799-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="50799-107">Bu durumlarda, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanız için gereken saat dilimini tanımlamak için yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50799-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="50799-108">Bu yöntemin aşırı yüklerini, ayarlama kuralları olan veya olmayan bir saat dilimi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50799-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="50799-109">Saat dilimi yaz saati kaydetme süresini destekliyorsa, düzeltilen veya kayan ayarlama kuralları ile ayarlamalar tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50799-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="50799-110">(Bu terimlerin tanımları için, [saat dilimine genel bakış](time-zone-overview.md)konusundaki "saat dilimi terminolojisi" bölümüne bakın.)</span><span class="sxs-lookup"><span data-stu-id="50799-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50799-111">Yöntemi çağırarak oluşturulan özel saat dilimleri <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> kayıt defterine eklenmez.</span><span class="sxs-lookup"><span data-stu-id="50799-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="50799-112">Bunun yerine, yalnızca Yöntem çağrısı tarafından döndürülen nesne başvurusu aracılığıyla erişilebilir <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> .</span><span class="sxs-lookup"><span data-stu-id="50799-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="50799-113">Bu konuda, ayarlama kuralları olmayan bir saat dilimini nasıl oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50799-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="50799-114">Gün ışığından yararlanma zaman ayarlama kurallarını destekleyen bir saat dilimi oluşturmak için bkz. [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="50799-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="50799-115">Ayarlama kuralları olmadan bir saat dilimi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="50799-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="50799-116">Saat diliminin görünen adını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="50799-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="50799-117">Görünen ad, saat diliminin Eşgüdümlü Evrensel Saat (UTC) arasındaki kaydırın parantez içine alındığı ve ardından saat dilimini tanımlayan bir dize, saat diliminizdeki bir veya daha fazla şehir ya da saat dilimindeki ülkelerin veya bölgelerin bir ya da daha fazlasını tanımlayan oldukça standart bir biçim izler.</span><span class="sxs-lookup"><span data-stu-id="50799-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="50799-118">Saat diliminin standart zamanının adını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="50799-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="50799-119">Genellikle, bu dize saat diliminin tanımlayıcısı olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50799-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="50799-120">Saat diliminin standart adından farklı bir tanımlayıcı kullanmak istiyorsanız, saat dilimi tanımlayıcısını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="50799-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="50799-121"><xref:System.TimeSpan>Saat DILIMININ UTC 'den sapmasını tanımlayan bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50799-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="50799-122">UTC 'den sonraki saatlere sahip saat dilimleri pozitif bir uzaklığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="50799-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="50799-123">UTC 'den önceki zamanlarla saat dilimlerinin negatif bir boşluğu vardır.</span><span class="sxs-lookup"><span data-stu-id="50799-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="50799-124"><xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>Yeni saat dilimini oluşturmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="50799-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="50799-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="50799-125">Example</span></span>

<span data-ttu-id="50799-126">Aşağıdaki örnek, hiçbir ayarlama kuralı olmayan Mawson, Antarktika için özel bir saat dilimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50799-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="50799-127">Özelliğe atanan dize, <xref:System.TimeZoneInfo.DisplayName%2A> saat DILIMININ UTC 'ye ait sapmasını ve ardından saat diliminin kolay bir açıklamasını izleyen standart bir biçim izler.</span><span class="sxs-lookup"><span data-stu-id="50799-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="50799-128">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="50799-128">Compiling the code</span></span>

<span data-ttu-id="50799-129">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="50799-129">This example requires:</span></span>

- <span data-ttu-id="50799-130">Aşağıdaki ad alanları içeri aktarılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="50799-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="50799-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50799-131">See also</span></span>

- [<span data-ttu-id="50799-132">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="50799-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="50799-133">Saat dilimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="50799-133">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="50799-134">Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="50799-134">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)

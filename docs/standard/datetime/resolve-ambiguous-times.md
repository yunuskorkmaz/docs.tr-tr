---
title: 'Nasıl yapılır: Belirsiz saatleri çözme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aae3e5145d2fa85cd55fc5b1288ef4aaa0fef48f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796415"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="8b644-102">Nasıl yapılır: Belirsiz saatleri çözme</span><span class="sxs-lookup"><span data-stu-id="8b644-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="8b644-103">Belirsiz bir saat birden fazla Eşgüdümlü Evrensel Saat (UTC için) eşleyen bir zamandır.</span><span class="sxs-lookup"><span data-stu-id="8b644-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="8b644-104">Saatin geri sürede gibi standart saati kendi saat diliminin gün ışığından yararlanma saatine geçiş sırasında ayarlanır oluşur.</span><span class="sxs-lookup"><span data-stu-id="8b644-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="8b644-105">Belirsiz bir saat işlerken, aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b644-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="8b644-106">Saat UTC'ye nasıl eşlendiğini hakkında bir olduğu varsayımını yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="8b644-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="8b644-107">Örneğin, belirsiz bir süre içinde saat diliminin standart saat her zaman gösterilir varsayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b644-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="8b644-108">Bir öğenin kullanıcı tarafından girilen veriler belirsiz saat ise belirsizliği çözmek için kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b644-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="8b644-109">Bu konuda, saat diliminin standart saati temsil ettiği varsayarak belirsiz bir saat olarak çözmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b644-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="8b644-110">Bir saat diliminin Standart Saati için belirsiz bir saat eşlemek için</span><span class="sxs-lookup"><span data-stu-id="8b644-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="8b644-111">Çağrı <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> zaman belirsiz olup olmadığını belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8b644-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="8b644-112">Belirsiz saat ise, saatten çıkar <xref:System.TimeSpan> saat diliminin tarafından döndürülen nesne <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8b644-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="8b644-113">Çağrı `static` (`Shared` Visual Basic. NET'te) <xref:System.DateTime.SpecifyKind%2A> UTC tarih ve saat değerinin ayarlanacak yöntemi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b644-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="8b644-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b644-114">Example</span></span>

<span data-ttu-id="8b644-115">Aşağıdaki örnek, yerel saat diliminin standart saati temsil ettiği varsayarak belirsiz bir saat UTC'ye göre dönüştürmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b644-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="8b644-116">Örnek adlı bir yöntemi oluşur `ResolveAmbiguousTime` belirleyen olmadığını <xref:System.DateTime> geçirilen değer belirsiz.</span><span class="sxs-lookup"><span data-stu-id="8b644-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="8b644-117">Değeri belirsiz ise yöntem döndürür bir <xref:System.DateTime> karşılık gelen UTC saati gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="8b644-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="8b644-118">Yerel saat diliminin değerini çıkararak bu dönüştürme yöntemi işleme <xref:System.TimeZoneInfo.BaseUtcOffset%2A> yerel saatinden özelliği.</span><span class="sxs-lookup"><span data-stu-id="8b644-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="8b644-119">Normalde, belirsiz bir saat çağrılarak gerçekleştirilir <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> dizisini almak için yöntemi <xref:System.TimeSpan> olası belirsiz saatin UTC içeren nesneleri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="8b644-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="8b644-120">Ancak, bu örnek, belirsiz bir saat saat diliminin Standart Saati için her zaman eşlenmelidir rastgele bir varsayım yapmaz.</span><span class="sxs-lookup"><span data-stu-id="8b644-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="8b644-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A> Özelliği, saat diliminin Standart Saati ile UTC arasındaki uzaklığı döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b644-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="8b644-122">Bu örnekte, yerel saat dilimi için tüm başvuruları aracılığıyla yapılan <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği; yerel saati dilimi hiçbir zaman bir nesne değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="8b644-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="8b644-123">Bunun nedeni önerilen uygulama, bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metodu geçersiz kılar, yerel saat dilimi atandığı herhangi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="8b644-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="8b644-124">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="8b644-124">Compiling the code</span></span>

<span data-ttu-id="8b644-125">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8b644-125">This example requires:</span></span>

* <span data-ttu-id="8b644-126">Projeye System.Core.dll öğesine başvuru eklenmesi gerektiğini.</span><span class="sxs-lookup"><span data-stu-id="8b644-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="8b644-127">Olduğunu <xref:System> ad alanı içeri aktarılacak `using` deyimi (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="8b644-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b644-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b644-128">See also</span></span>

- [<span data-ttu-id="8b644-129">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="8b644-129">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="8b644-130">Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine olanak tanır</span><span class="sxs-lookup"><span data-stu-id="8b644-130">How to: Let users resolve ambiguous times</span></span>](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)

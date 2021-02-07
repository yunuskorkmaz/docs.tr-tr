---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: belirsiz zamanları çözme'
title: 'Nasıl yapılır: Belirsiz saatleri çözme'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 743aff3303669efcf20e233b1f5b2d520475d5f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702528"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="fdcc6-103">Nasıl yapılır: Belirsiz saatleri çözme</span><span class="sxs-lookup"><span data-stu-id="fdcc6-103">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="fdcc6-104">Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-104">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="fdcc6-105">Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-105">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="fdcc6-106">Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fdcc6-106">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="fdcc6-107">Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="fdcc6-108">Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="fdcc6-109">Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-109">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="fdcc6-110">Bu konuda, saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın nasıl çözümleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-110">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="fdcc6-111">Belirsiz bir süreyi saat diliminin standart saatine eşlemek için</span><span class="sxs-lookup"><span data-stu-id="fdcc6-111">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="fdcc6-112"><xref:System.TimeZoneInfo.IsAmbiguousTime%2A>Saatin belirsiz olup olmadığını anlamak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="fdcc6-113">Zaman belirsiz ise, saat <xref:System.TimeSpan> dilimi özelliği tarafından döndürülen nesneden saati çıkarın <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="fdcc6-113">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="fdcc6-114">`static` `Shared` <xref:System.DateTime.SpecifyKind%2A> UTC Tarih ve saat değerinin özelliğini olarak ayarlamak için (Visual Basic .net) metodunu çağırın <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fdcc6-114">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="fdcc6-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdcc6-115">Example</span></span>

<span data-ttu-id="fdcc6-116">Aşağıdaki örnek, yerel saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın UTC 'ye nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-116">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="fdcc6-117">Örnek, `ResolveAmbiguousTime` geçirilen değerin belirsiz olup olmadığını belirleyen adlı bir yöntemden oluşur <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="fdcc6-117">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="fdcc6-118">Değer belirsiz ise, yöntemi <xref:System.DateTime> karşılık gelen UTC zamanını temsil eden bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-118">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="fdcc6-119">Yöntemi, yerel saat dilimi özelliğinin değerini yerel saatten çıkararak bu dönüştürmeyi işler <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="fdcc6-119">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="fdcc6-120">Normalde belirsiz bir zaman, <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> <xref:System.TimeSpan> belirsiz zamanın olası UTC uzaklıklarını içeren bir nesne dizisini almak için yöntemini çağırarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-120">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="fdcc6-121">Ancak bu örnek, belirsiz bir saatin, her zaman saat diliminin standart saatine eşlenmesi gereken rastgele varsayımını yapar.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-121">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="fdcc6-122"><xref:System.TimeZoneInfo.BaseUtcOffset%2A>ÖZELLIĞI UTC ve saat diliminin standart saati arasındaki sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-122">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="fdcc6-123">Bu örnekte, yerel saat dilimine yapılan tüm başvurular özelliği aracılığıyla yapılır <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-123">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="fdcc6-124">Bu önerilen bir uygulamadır çünkü yöntemine yapılan bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> , yerel saat diliminin atandığı tüm nesneleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-124">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="fdcc6-125">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="fdcc6-125">Compiling the code</span></span>

<span data-ttu-id="fdcc6-126">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fdcc6-126">This example requires:</span></span>

- <span data-ttu-id="fdcc6-127">Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="fdcc6-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="fdcc6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdcc6-128">See also</span></span>

- [<span data-ttu-id="fdcc6-129">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="fdcc6-129">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="fdcc6-130">Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin verme</span><span class="sxs-lookup"><span data-stu-id="fdcc6-130">How to: Let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)

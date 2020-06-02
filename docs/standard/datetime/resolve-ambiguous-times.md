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
ms.openlocfilehash: ad69c0984a9d8c01ebd2198486cd0f6492a6116e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281511"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="e9ba3-102">Nasıl yapılır: Belirsiz saatleri çözme</span><span class="sxs-lookup"><span data-stu-id="e9ba3-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="e9ba3-103">Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="e9ba3-104">Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="e9ba3-105">Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9ba3-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="e9ba3-106">Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="e9ba3-107">Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="e9ba3-108">Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="e9ba3-109">Bu konuda, saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın nasıl çözümleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="e9ba3-110">Belirsiz bir süreyi saat diliminin standart saatine eşlemek için</span><span class="sxs-lookup"><span data-stu-id="e9ba3-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="e9ba3-111"><xref:System.TimeZoneInfo.IsAmbiguousTime%2A>Saatin belirsiz olup olmadığını anlamak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="e9ba3-112">Zaman belirsiz ise, saat <xref:System.TimeSpan> dilimi özelliği tarafından döndürülen nesneden saati çıkarın <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="e9ba3-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="e9ba3-113">`static` `Shared` <xref:System.DateTime.SpecifyKind%2A> UTC Tarih ve saat değerinin özelliğini olarak ayarlamak için (Visual Basic .net) metodunu çağırın <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9ba3-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="e9ba3-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9ba3-114">Example</span></span>

<span data-ttu-id="e9ba3-115">Aşağıdaki örnek, yerel saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın UTC 'ye nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="e9ba3-116">Örnek, `ResolveAmbiguousTime` geçirilen değerin belirsiz olup olmadığını belirleyen adlı bir yöntemden oluşur <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="e9ba3-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="e9ba3-117">Değer belirsiz ise, yöntemi <xref:System.DateTime> karşılık gelen UTC zamanını temsil eden bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="e9ba3-118">Yöntemi, yerel saat dilimi özelliğinin değerini yerel saatten çıkararak bu dönüştürmeyi işler <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="e9ba3-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="e9ba3-119">Normalde belirsiz bir zaman, <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> <xref:System.TimeSpan> belirsiz zamanın olası UTC uzaklıklarını içeren bir nesne dizisini almak için yöntemini çağırarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="e9ba3-120">Ancak bu örnek, belirsiz bir saatin, her zaman saat diliminin standart saatine eşlenmesi gereken rastgele varsayımını yapar.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="e9ba3-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A>ÖZELLIĞI UTC ve saat diliminin standart saati arasındaki sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="e9ba3-122">Bu örnekte, yerel saat dilimine yapılan tüm başvurular özelliği aracılığıyla yapılır <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="e9ba3-123">Bu önerilen bir uygulamadır çünkü yöntemine yapılan bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> , yerel saat diliminin atandığı tüm nesneleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="e9ba3-124">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="e9ba3-124">Compiling the code</span></span>

<span data-ttu-id="e9ba3-125">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e9ba3-125">This example requires:</span></span>

- <span data-ttu-id="e9ba3-126">Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="e9ba3-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9ba3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9ba3-127">See also</span></span>

- [<span data-ttu-id="e9ba3-128">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="e9ba3-128">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="e9ba3-129">Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver</span><span class="sxs-lookup"><span data-stu-id="e9ba3-129">How to: Let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)

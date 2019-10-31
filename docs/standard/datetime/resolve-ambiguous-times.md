---
title: 'Nasıl yapılır: belirsiz zamanları çözme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 0b5b28c588237fb2f7f069aaef06f3f73d5268bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122244"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="09745-102">Nasıl yapılır: belirsiz zamanları çözme</span><span class="sxs-lookup"><span data-stu-id="09745-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="09745-103">Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir.</span><span class="sxs-lookup"><span data-stu-id="09745-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="09745-104">Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="09745-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="09745-105">Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="09745-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="09745-106">Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="09745-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="09745-107">Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.</span><span class="sxs-lookup"><span data-stu-id="09745-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="09745-108">Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09745-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="09745-109">Bu konuda, saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın nasıl çözümleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="09745-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="09745-110">Belirsiz bir süreyi saat diliminin standart saatine eşlemek için</span><span class="sxs-lookup"><span data-stu-id="09745-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="09745-111">Saatin belirsiz olup olmadığını anlamak için <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="09745-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="09745-112">Zaman belirsiz ise, saat diliminin <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği tarafından döndürülen <xref:System.TimeSpan> nesnesinden saati çıkarın.</span><span class="sxs-lookup"><span data-stu-id="09745-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="09745-113">UTC Tarih ve saat değerinin <xref:System.DateTime.Kind%2A> özelliğini ayarlamak için `static` (Visual Basic .NET 'te`Shared`) <xref:System.DateTime.SpecifyKind%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="09745-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="09745-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="09745-114">Example</span></span>

<span data-ttu-id="09745-115">Aşağıdaki örnek, yerel saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın UTC 'ye nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="09745-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="09745-116">Örnek, geçirilen <xref:System.DateTime> değerinin belirsiz olup olmadığını belirleyen `ResolveAmbiguousTime` adlı bir yöntemden oluşur.</span><span class="sxs-lookup"><span data-stu-id="09745-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="09745-117">Değer belirsiz ise, yöntemi karşılık gelen UTC zamanını temsil eden bir <xref:System.DateTime> değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="09745-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="09745-118">Yöntemi, yerel saat diliminin <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliğinin değerini yerel saatten çıkararak bu dönüştürmeyi işler.</span><span class="sxs-lookup"><span data-stu-id="09745-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="09745-119">Normalde belirsiz bir zaman, belirsiz zamanın olası UTC uzaklıklarını içeren bir dizi <xref:System.TimeSpan> nesne almak için <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> yöntemi çağırarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="09745-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="09745-120">Ancak bu örnek, belirsiz bir saatin, her zaman saat diliminin standart saatine eşlenmesi gereken rastgele varsayımını yapar.</span><span class="sxs-lookup"><span data-stu-id="09745-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="09745-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği UTC ile saat diliminin standart saati arasındaki sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="09745-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="09745-122">Bu örnekte, yerel saat dilimine yapılan tüm başvurular <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yapılır; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz.</span><span class="sxs-lookup"><span data-stu-id="09745-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="09745-123">Bu önerilen bir uygulamadır çünkü <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı, yerel saat diliminin atandığı nesneleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="09745-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="09745-124">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="09745-124">Compiling the code</span></span>

<span data-ttu-id="09745-125">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="09745-125">This example requires:</span></span>

- <span data-ttu-id="09745-126"><xref:System> ad alanı `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="09745-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="09745-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09745-127">See also</span></span>

- [<span data-ttu-id="09745-128">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="09745-128">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="09745-129">Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin verme</span><span class="sxs-lookup"><span data-stu-id="09745-129">How to: Let users resolve ambiguous times</span></span>](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)

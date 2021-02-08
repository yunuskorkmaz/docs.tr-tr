---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver'
title: 'Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin verme'
ms.date: 04/10/2017
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: a64d20080ed021af273a2d114c7558615b8b04e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782487"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="cae7a-103">Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin verme</span><span class="sxs-lookup"><span data-stu-id="cae7a-103">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="cae7a-104">Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir.</span><span class="sxs-lookup"><span data-stu-id="cae7a-104">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="cae7a-105">Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="cae7a-105">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="cae7a-106">Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cae7a-106">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="cae7a-107">Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cae7a-107">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="cae7a-108">Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cae7a-108">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="cae7a-109">Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.</span><span class="sxs-lookup"><span data-stu-id="cae7a-109">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="cae7a-110">Bu konu başlığı altında, kullanıcının belirsiz bir süre çözümlenme yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cae7a-110">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="cae7a-111">Kullanıcının belirsiz bir süre çözmesine izin vermek için</span><span class="sxs-lookup"><span data-stu-id="cae7a-111">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="cae7a-112">Kullanıcı tarafından tarih ve saat girişi al.</span><span class="sxs-lookup"><span data-stu-id="cae7a-112">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="cae7a-113"><xref:System.TimeZoneInfo.IsAmbiguousTime%2A>Saatin belirsiz olup olmadığını anlamak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="cae7a-113">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="cae7a-114">Süre belirsizse, <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> nesne dizisini almak için yöntemini çağırın <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="cae7a-114">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="cae7a-115">Dizideki her öğe, belirsiz saatin eşleyebileceğiniz UTC sapmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="cae7a-115">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="cae7a-116">Kullanıcının istenen sapmayı seçmesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="cae7a-116">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="cae7a-117">Kullanıcı tarafından seçilen sapmayı yerel saatten çıkararak UTC Tarih ve saatini elde edin.</span><span class="sxs-lookup"><span data-stu-id="cae7a-117">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="cae7a-118">`static` `Shared` <xref:System.DateTime.SpecifyKind%2A> UTC Tarih ve saat değerinin özelliğini olarak ayarlamak için (Visual Basic .net) metodunu çağırın <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cae7a-118">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="cae7a-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="cae7a-119">Example</span></span>

<span data-ttu-id="cae7a-120">Aşağıdaki örnek, kullanıcıdan bir tarih ve saat girmesini ister ve belirsiz ise kullanıcının belirsiz saatin eşlendiği UTC saatini seçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cae7a-120">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="cae7a-121">Örnek kodun çekirdeği, <xref:System.TimeSpan> UTC 'den belirsiz sürenin olası uzaklıklarını göstermek için bir nesne dizisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="cae7a-121">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="cae7a-122">Ancak, bu uzaklıklar Kullanıcı için anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="cae7a-122">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="cae7a-123">Kaydırmanın anlamını netleştirmek için, kod ayrıca bir uzaklığın yerel saat diliminin standart saatini mi yoksa gün ışığından yararlanma saatini mi temsil ettiğini de not eder.</span><span class="sxs-lookup"><span data-stu-id="cae7a-123">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="cae7a-124">Kod, değeri özelliğin değeriyle karşılaştırarak hangi zamanın standart olduğunu ve ne zaman günışığından yararlanma olduğunu belirler <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="cae7a-124">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="cae7a-125">Bu özellik UTC ve saat diliminin standart saati arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cae7a-125">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="cae7a-126">Bu örnekte, yerel saat dilimine yapılan tüm başvurular özelliği aracılığıyla yapılır <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz.</span><span class="sxs-lookup"><span data-stu-id="cae7a-126">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="cae7a-127">Bu önerilen bir uygulamadır çünkü yöntemine yapılan bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> , yerel saat diliminin atandığı tüm nesneleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="cae7a-127">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="cae7a-128">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="cae7a-128">Compiling the code</span></span>

<span data-ttu-id="cae7a-129">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cae7a-129">This example requires:</span></span>

- <span data-ttu-id="cae7a-130">Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="cae7a-130">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="cae7a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cae7a-131">See also</span></span>

- [<span data-ttu-id="cae7a-132">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="cae7a-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="cae7a-133">Nasıl yapılır: Belirsiz saatleri çözme</span><span class="sxs-lookup"><span data-stu-id="cae7a-133">How to: Resolve ambiguous times</span></span>](resolve-ambiguous-times.md)

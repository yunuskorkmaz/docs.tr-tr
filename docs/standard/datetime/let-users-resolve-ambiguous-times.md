---
title: 'Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: f988616a4b2a5d8202c87e3be3cb23c7f9f1f130
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122271"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="69201-102">Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver</span><span class="sxs-lookup"><span data-stu-id="69201-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="69201-103">Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir.</span><span class="sxs-lookup"><span data-stu-id="69201-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="69201-104">Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="69201-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="69201-105">Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69201-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="69201-106">Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69201-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="69201-107">Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="69201-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="69201-108">Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.</span><span class="sxs-lookup"><span data-stu-id="69201-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="69201-109">Bu konu başlığı altında, kullanıcının belirsiz bir süre çözümlenme yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="69201-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="69201-110">Kullanıcının belirsiz bir süre çözmesine izin vermek için</span><span class="sxs-lookup"><span data-stu-id="69201-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="69201-111">Kullanıcı tarafından tarih ve saat girişi al.</span><span class="sxs-lookup"><span data-stu-id="69201-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="69201-112">Saatin belirsiz olup olmadığını anlamak için <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="69201-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="69201-113">Zaman belirsiz ise, <xref:System.TimeSpan> nesne dizisini almak için <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="69201-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="69201-114">Dizideki her öğe, belirsiz saatin eşleyebileceğiniz UTC sapmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="69201-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="69201-115">Kullanıcının istenen sapmayı seçmesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="69201-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="69201-116">Kullanıcı tarafından seçilen sapmayı yerel saatten çıkararak UTC Tarih ve saatini elde edin.</span><span class="sxs-lookup"><span data-stu-id="69201-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="69201-117">UTC Tarih ve saat değerinin <xref:System.DateTime.Kind%2A> özelliğini ayarlamak için `static` (Visual Basic .NET 'te`Shared`) <xref:System.DateTime.SpecifyKind%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="69201-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="69201-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="69201-118">Example</span></span>

<span data-ttu-id="69201-119">Aşağıdaki örnek, kullanıcıdan bir tarih ve saat girmesini ister ve belirsiz ise kullanıcının belirsiz saatin eşlendiği UTC saatini seçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="69201-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="69201-120">Örnek kodun çekirdeği, UTC 'den belirsiz sürenin olası uzaklıklarını göstermek için <xref:System.TimeSpan> nesneleri dizisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="69201-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="69201-121">Ancak, bu uzaklıklar Kullanıcı için anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="69201-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="69201-122">Kaydırmanın anlamını netleştirmek için, kod ayrıca bir uzaklığın yerel saat diliminin standart saatini mi yoksa gün ışığından yararlanma saatini mi temsil ettiğini de not eder.</span><span class="sxs-lookup"><span data-stu-id="69201-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="69201-123">Kod, <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliğinin değeriyle SAPMAYı karşılaştırarak hangi zamanın standart olduğunu ve ne zaman gündüz olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="69201-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="69201-124">Bu özellik UTC ve saat diliminin standart saati arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="69201-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="69201-125">Bu örnekte, yerel saat dilimine yapılan tüm başvurular <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yapılır; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz.</span><span class="sxs-lookup"><span data-stu-id="69201-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="69201-126">Bu önerilen bir uygulamadır çünkü <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı, yerel saat diliminin atandığı nesneleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="69201-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="69201-127">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="69201-127">Compiling the code</span></span>

<span data-ttu-id="69201-128">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="69201-128">This example requires:</span></span>

- <span data-ttu-id="69201-129"><xref:System> ad alanı `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="69201-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="69201-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69201-130">See also</span></span>

- [<span data-ttu-id="69201-131">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="69201-131">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="69201-132">Nasıl yapılır: Belirsiz saatleri çözme</span><span class="sxs-lookup"><span data-stu-id="69201-132">How to: Resolve ambiguous times</span></span>](../../../docs/standard/datetime/resolve-ambiguous-times.md)

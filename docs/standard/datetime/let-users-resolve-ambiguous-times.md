---
title: 'Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine olanak tanır'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae6d16bda7a2cd6f2367129b737ec79d8193ebf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502721"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="9e641-102">Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine olanak tanır</span><span class="sxs-lookup"><span data-stu-id="9e641-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="9e641-103">Belirsiz bir saat birden fazla Eşgüdümlü Evrensel Saat (UTC için) eşleyen bir zamandır.</span><span class="sxs-lookup"><span data-stu-id="9e641-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="9e641-104">Saatin geri sürede gibi standart saati kendi saat diliminin gün ışığından yararlanma saatine geçiş sırasında ayarlanır oluşur.</span><span class="sxs-lookup"><span data-stu-id="9e641-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="9e641-105">Belirsiz bir saat işlerken, aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e641-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="9e641-106">Bir öğenin kullanıcı tarafından girilen veriler belirsiz saat ise belirsizliği çözmek için kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e641-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="9e641-107">Saat UTC'ye nasıl eşlendiğini hakkında bir olduğu varsayımını yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="9e641-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="9e641-108">Örneğin, belirsiz bir süre içinde saat diliminin standart saat her zaman gösterilir varsayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e641-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="9e641-109">Bu konuda, bir kullanıcının belirsiz bir saat çözmek olanak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e641-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="9e641-110">Belirsiz bir saat çözmek kullanıcı izin vermek için</span><span class="sxs-lookup"><span data-stu-id="9e641-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="9e641-111">Tarih ve saat tarafından kullanıcı girişi alın.</span><span class="sxs-lookup"><span data-stu-id="9e641-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="9e641-112">Çağrı <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> zaman belirsiz olup olmadığını belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9e641-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="9e641-113">Zaman belirsiz ise, çağrı <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> dizisini almak için yöntemi <xref:System.TimeSpan> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9e641-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="9e641-114">Belirsiz saat eşleyebilirsiniz bir UTC farkı dizideki her öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="9e641-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="9e641-115">Kullanıcı Seç istenen uzaklığı olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9e641-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="9e641-116">UTC tarihi ve saati yerel saate kullanıcı tarafından seçilen uzaklığı çıkararak alın.</span><span class="sxs-lookup"><span data-stu-id="9e641-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="9e641-117">Çağrı `static` (`Shared` Visual Basic. NET'te) <xref:System.DateTime.SpecifyKind%2A> UTC tarih ve saat değerinin ayarlanacak yöntemi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e641-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="9e641-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e641-118">Example</span></span>

<span data-ttu-id="9e641-119">Aşağıdaki örnek bir tarih ve saat girmesini ister ve belirsiz ise belirsiz saat eşlendiği UTC saati seçmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9e641-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="9e641-120">Örnek kod setinin bir dizi kullanan <xref:System.TimeSpan> belirsiz saat UTC olası uzaklıklarını belirtmek için nesnelerdeki.</span><span class="sxs-lookup"><span data-stu-id="9e641-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="9e641-121">Ancak, bu uzaklıkları kullanıcıya anlamlı olması pek olası değildir.</span><span class="sxs-lookup"><span data-stu-id="9e641-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="9e641-122">Uzaklık anlamını açıklamak için bir uzaklık yerel saat diliminin standart saat veya kendi yaz saati temsil edip etmediğini kod da notlar.</span><span class="sxs-lookup"><span data-stu-id="9e641-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="9e641-123">Kodu, hangi zaman standart belirler ve hangi zaman Yaz uzaklık değeri ile karşılaştırarak <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9e641-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="9e641-124">Bu özellik, saat diliminin Standart Saati ile UTC arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e641-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="9e641-125">Bu örnekte, yerel saat dilimi için tüm başvuruları aracılığıyla yapılan <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği; yerel saati dilimi hiçbir zaman bir nesne değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="9e641-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="9e641-126">Bunun nedeni önerilen uygulama, bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metodu geçersiz kılar, yerel saat dilimi atandığı herhangi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="9e641-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="9e641-127">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="9e641-127">Compiling the code</span></span>

<span data-ttu-id="9e641-128">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9e641-128">This example requires:</span></span>

* <span data-ttu-id="9e641-129">Projeye System.Core.dll öğesine başvuru eklenmesi gerektiğini.</span><span class="sxs-lookup"><span data-stu-id="9e641-129">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="9e641-130">Olduğunu <xref:System> ad alanı içeri aktarılacak `using` deyimi (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="9e641-130">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e641-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e641-131">See also</span></span>

- [<span data-ttu-id="9e641-132">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="9e641-132">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="9e641-133">Nasıl yapılır: Belirsiz saatleri çözme</span><span class="sxs-lookup"><span data-stu-id="9e641-133">How to: Resolve ambiguous times</span></span>](../../../docs/standard/datetime/resolve-ambiguous-times.md)

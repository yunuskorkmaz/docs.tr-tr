---
title: "Nasıl yapılır: belirsiz saatleri çözme"
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
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3706747848dbcd29d4ed2e81d5b7447a127a653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="3d2a5-102">Nasıl yapılır: belirsiz saatleri çözme</span><span class="sxs-lookup"><span data-stu-id="3d2a5-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="3d2a5-103">Belirsiz saat birden fazla Eşgüdümlü Evrensel Saat (UTC için) eşleşen bir zamandır.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="3d2a5-104">Saatin geçmişe, gibi standart saati bir saat diliminin gün ışığından yararlanma saati geçiş sırasında ayarlanır oluşur.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="3d2a5-105">Belirsiz saat işlerken, aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d2a5-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="3d2a5-106">Saat UTC'ye nasıl eşlendiğini hakkında bir olduğu varsayımını yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="3d2a5-107">Örneğin, belirsiz bir süre içinde saat diliminin Standart Saati her zaman gösterilir varsayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="3d2a5-108">Belirsiz saat öğenin kullanıcı tarafından girilen verilerin ise, karışıklığı çözmek için kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="3d2a5-109">Bu konu, saat diliminin standart saati temsil eden varsayılarak tarafından belirsiz bir süre çözmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="3d2a5-110">Belirsiz saat saat diliminin Standart Saati için eşlemek için</span><span class="sxs-lookup"><span data-stu-id="3d2a5-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="3d2a5-111">Çağrı <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> zaman belirsiz olup olmadığını belirlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="3d2a5-112">Saat belirsiz ise zamandan çıkarma <xref:System.TimeSpan> saat diliminin tarafından döndürülen nesne <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="3d2a5-113">Çağrı `static` (`Shared` Visual Basic .NET içinde) <xref:System.DateTime.SpecifyKind%2A> UTC tarihi ve saati değer ayarlamak için yöntemin <xref:System.DateTime.Kind%2A> özelliğine <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="3d2a5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d2a5-114">Example</span></span>

<span data-ttu-id="3d2a5-115">Aşağıdaki örnek, yerel saat diliminin standart saati temsil eden varsayılarak belirsiz bir süre UTC tarafından nasıl dönüştürüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="3d2a5-116">Adlı bir yöntemi örnek oluşur `ResolveAmbiguousTime` belirleyen olup olmadığını <xref:System.DateTime> kendisine geçirilen değerdir belirsiz.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="3d2a5-117">Değeri belirsiz ise, yöntem bir <xref:System.DateTime> karşılık gelen UTC saati gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="3d2a5-118">Yerel saat diliminin değerini çıkararak bu dönüştürme yöntemi işler <xref:System.TimeZoneInfo.BaseUtcOffset%2A> yerel saat özelliğinden.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="3d2a5-119">Belirsiz saat çağırarak normalde, işlenen <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> dizisini almak için yöntemini <xref:System.TimeSpan> belirsiz zaman olası UTC içeren nesneleri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="3d2a5-120">Ancak, bu örnek belirsiz bir saat, saat diliminin Standart Saati için her zaman eşlenmelidir rasgele varsayım yapmaz.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="3d2a5-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A> Özelliği UTC ve saat diliminin standart saat uzaklığı döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="3d2a5-122">Bu örnekte, yerel saat dilimine yönelik tüm başvuruları üzerinden yapılan <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özellik; bölge için bir nesne değişkeninin hiçbir zaman atanmış yerel saat.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="3d2a5-123">Bunun nedeni önerilen bir uygulama, bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemi yerel saat dilimini atandığı herhangi bir nesne geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="3d2a5-124">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="3d2a5-124">Compiling the code</span></span>

<span data-ttu-id="3d2a5-125">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3d2a5-125">This example requires:</span></span>

* <span data-ttu-id="3d2a5-126">Bir başvuru System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="3d2a5-127">Olduğunu <xref:System> ad alanı ile aktarılabilir `using` deyimi (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="3d2a5-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d2a5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d2a5-128">See also</span></span>

<span data-ttu-id="3d2a5-129">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[nasıl yapılır: kullanıcıların belirsiz saatleri çözmek olanak tanır](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="3d2a5-129">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span></span>

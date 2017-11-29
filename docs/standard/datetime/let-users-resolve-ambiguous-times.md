---
title: "Nasıl yapılır: kullanıcıların belirsiz saatleri çözmek olanak tanır"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6409e676944f64931b197fda1a6a7b392c268c97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="f5100-102">Nasıl yapılır: kullanıcıların belirsiz saatleri çözmek olanak tanır</span><span class="sxs-lookup"><span data-stu-id="f5100-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="f5100-103">Belirsiz saat birden fazla Eşgüdümlü Evrensel Saat (UTC için) eşleşen bir zamandır.</span><span class="sxs-lookup"><span data-stu-id="f5100-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="f5100-104">Saatin geçmişe, gibi standart saati bir saat diliminin gün ışığından yararlanma saati geçiş sırasında ayarlanır oluşur.</span><span class="sxs-lookup"><span data-stu-id="f5100-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="f5100-105">Belirsiz saat işlerken, aşağıdakilerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5100-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="f5100-106">Belirsiz saat öğenin kullanıcı tarafından girilen verilerin ise, karışıklığı çözmek için kullanıcıya bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5100-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="f5100-107">Saat UTC'ye nasıl eşlendiğini hakkında bir olduğu varsayımını yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="f5100-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="f5100-108">Örneğin, belirsiz bir süre içinde saat diliminin Standart Saati her zaman gösterilir varsayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5100-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="f5100-109">Bu konuda belirsiz bir zamana çözmek bir kullanıcının olanak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5100-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="f5100-110">Belirsiz saat çözmek kullanıcı izin vermek için</span><span class="sxs-lookup"><span data-stu-id="f5100-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="f5100-111">Tarih ve saat tarafından kullanıcı girişi alın.</span><span class="sxs-lookup"><span data-stu-id="f5100-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="f5100-112">Çağrı <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> zaman belirsiz olup olmadığını belirlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="f5100-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="f5100-113">Saat belirsiz ise çağrı <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> dizisini almak için yöntemini <xref:System.TimeSpan> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f5100-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="f5100-114">Dizideki her öğe belirsiz saat eşleyebilirsiniz UTC uzaklık içerir.</span><span class="sxs-lookup"><span data-stu-id="f5100-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="f5100-115">Kullanıcı Seç istenen uzaklık olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f5100-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="f5100-116">UTC tarihi ve saati yerel saate kullanıcı tarafından seçilen uzaklığı çıkarılmasıyla alın.</span><span class="sxs-lookup"><span data-stu-id="f5100-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="f5100-117">Çağrı `static` (`Shared` Visual Basic .NET içinde) <xref:System.DateTime.SpecifyKind%2A> UTC tarihi ve saati değer ayarlamak için yöntemin <xref:System.DateTime.Kind%2A> özelliğine <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f5100-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="f5100-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5100-118">Example</span></span>

<span data-ttu-id="f5100-119">Aşağıdaki örnekte bir tarih ve saat girmesini ister ve belirsiz, varsa kullanıcının belirsiz saat eşlendiği UTC saati seçmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f5100-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="f5100-120">Bir dizi örnek kod çekirdek kullanan <xref:System.TimeSpan> belirsiz saati UTC olası uzaklıklarını belirtmek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f5100-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="f5100-121">Ancak, bu uzaklıkları kullanıcıya anlamlı olması olası değildir.</span><span class="sxs-lookup"><span data-stu-id="f5100-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="f5100-122">Uzaklık anlamını açıklamak için bir uzaklık yerel saat diliminin standart saat veya kendi yaz saati temsil edip etmediğini kod ayrıca notlar.</span><span class="sxs-lookup"><span data-stu-id="f5100-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="f5100-123">Kodu belirler hangi zaman standarttır ve hangi zamanı gün ışığından yararlanma uzaklık değeriyle karşılaştırarak <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f5100-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="f5100-124">Bu özellik, UTC saat diliminin standart saati arasındaki farkı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5100-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="f5100-125">Bu örnekte, yerel saat dilimine yönelik tüm başvuruları üzerinden yapılan <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özellik; bölge için bir nesne değişkeninin hiçbir zaman atanmış yerel saat.</span><span class="sxs-lookup"><span data-stu-id="f5100-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="f5100-126">Bunun nedeni önerilen bir uygulama, bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemi yerel saat dilimini atandığı herhangi bir nesne geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f5100-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="f5100-127">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="f5100-127">Compiling the code</span></span>

<span data-ttu-id="f5100-128">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f5100-128">This example requires:</span></span>

* <span data-ttu-id="f5100-129">Bir başvuru System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="f5100-129">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="f5100-130">Olduğunu <xref:System> ad alanı ile aktarılabilir `using` deyimi (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="f5100-130">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5100-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5100-131">See also</span></span>

<span data-ttu-id="f5100-132">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[nasıl yapılır: belirsiz saatleri çözme](../../../docs/standard/datetime/resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="f5100-132">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md)</span></span>

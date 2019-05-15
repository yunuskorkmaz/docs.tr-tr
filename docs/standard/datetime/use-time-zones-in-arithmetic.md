---
title: 'Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d504aa9ad7d6e4084192a2434ac408e8fa7a041
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588534"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="8bd1a-102">Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="8bd1a-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="8bd1a-103">Normalde, ne zaman, tarih gerçekleştirmek ve aritmetik kullanarak istediğiniz zaman <xref:System.DateTime> veya <xref:System.DateTimeOffset> değerleri, sonucu herhangi bir saat dilimi ayarlama kurallarını yansıtmıyor.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="8bd1a-104">Bu tarih ve saat değerinin saat dilimi açıkça tanımlanabilen olsa bile geçerlidir (örneğin, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local>).</span><span class="sxs-lookup"><span data-stu-id="8bd1a-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="8bd1a-105">Bu konuda, belirli bir saat dilimine ait tarih ve saat değerlerini aritmetik işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="8bd1a-106">Aritmetik işlemler sonuçlarını, saat diliminin ayarlama kuralları ücreti yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="8bd1a-107">Tarih ve saat aritmetiği ayarlama kuralları uygulamak için</span><span class="sxs-lookup"><span data-stu-id="8bd1a-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="8bd1a-108">Bir tarih ve saat değerini ait olduğu saat dilimi ile yakından eşlenmesiyle bazı yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="8bd1a-109">Örneğin, hem tarih ve saat değeri hem de saat dilimini içeren bir yapıyı bildirme.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="8bd1a-110">Aşağıdaki örnek, bağlamak için bu yaklaşımı kullanır. bir <xref:System.DateTime> kendi saat dilimiyle değeri.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="8bd1a-111">Eşgüdümlü Evrensel Saat (UTC) ya da çağırarak dönüştürün <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> yöntemi veya <xref:System.TimeZoneInfo.ConvertTime%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="8bd1a-112">UTC saati aritmetik işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="8bd1a-113">Saat, çağırarak orijinal zaman ilişkili saat dilimi UTC'den dönüştürmek <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="8bd1a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd1a-114">Example</span></span>

<span data-ttu-id="8bd1a-115">Aşağıdaki örnek iki saat ve otuz dakika 9 Mart 2008'e 1: 30'da ekler.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="8bd1a-116">Merkezi standart saat.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-116">Central Standard Time.</span></span> <span data-ttu-id="8bd1a-117">Gün ışığından yararlanma saat diliminin geçiş otuz dakika sonra 2: 00'da gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="8bd1a-118">9 Mart 2008.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-118">on March 9, 2008.</span></span> <span data-ttu-id="8bd1a-119">Örnek önceki bölümde listelenen dört adımları izler olduğundan, sonuçta elde edilen zaman olarak 5: 00'da doğru şekilde rapor</span><span class="sxs-lookup"><span data-stu-id="8bd1a-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="8bd1a-120">9 Mart 2008.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="8bd1a-121">Her ikisi de <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri ait oldukları tüm zaman dilimine ilişkisi kesilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="8bd1a-122">Tarih ve saat aritmetiği, otomatik olarak bir saat diliminin ayarlama kuralları uygulayan bir şekilde gerçekleştirmek için hangi bir tüm tarih ve saat değerini ait olduğu saat dilimini hemen tanımlanabilen olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="8bd1a-123">Bu, bir tarih ve saat ile ilişkili kendi saat dilimiyle sıkı şekilde bağlı gerekir, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="8bd1a-124">Aşağıdakiler dahil, bunu yapmanın birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="8bd1a-124">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="8bd1a-125">Her zaman bir uygulamada kullanılan belirli bir saat dilimine ait varsayılır.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="8bd1a-126">Bazı durumlarda uygun olsa da bu yaklaşım sınırlı esnekliği ve büyük olasılıkla sınırlı taşınabilirliği sunar.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="8bd1a-127">Bir tarih ve saat ekleyerek ilişkili kendi saat dilimiyle hem türünde alanlar olarak sıkı bir şekilde couples bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="8bd1a-128">Bu yaklaşım, tarih ve saat ve saat dilimi iki üye alanları depolamak için bir yapı tanımlar kod örneğindeki kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="8bd1a-129">Üzerinde aritmetik işlemler gerçekleştirme örnekte gösterildiği <xref:System.DateTime> saat dilimi ayarlama kurallarını sonucu uygulanması değerleri.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="8bd1a-130">Ancak, <xref:System.DateTimeOffset> değerleri bir kolayca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="8bd1a-131">Aşağıdaki örnek nasıl özgün örnek kodu kullanmak için uyarlanmış olabileceği gösterir <xref:System.DateTimeOffset> yerine <xref:System.DateTime> değerleri.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="8bd1a-132">Bu toplama yalnızca gerçekleştirilir gerçekleştiriyorsanız <xref:System.DateTimeOffset> olmadan önce onu UTC'ye dönüştürme, sonucu doğru noktası sürede yansıtır ancak uzaklığı belirtilen saat dilimi, o zaman için yansıtmaz değeri.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="8bd1a-133">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="8bd1a-133">Compiling the code</span></span>

<span data-ttu-id="8bd1a-134">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8bd1a-134">This example requires:</span></span>

* <span data-ttu-id="8bd1a-135">Olduğunu <xref:System> ad alanı içeri aktarılacak `using` deyimi (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="8bd1a-135">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="8bd1a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd1a-136">See also</span></span>

- [<span data-ttu-id="8bd1a-137">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="8bd1a-137">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="8bd1a-138">Tarih ve saatlerle aritmetik işlemler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="8bd1a-138">Performing arithmetic operations with dates and times</span></span>](../../../docs/standard/datetime/performing-arithmetic-operations.md)

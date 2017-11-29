---
title: "Nasıl yapılır: tarih ve saat aritmetiği saat dilimini kullanır"
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
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16f90117353c490b0a6f7b7fe94730d90e797b35
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="f7e19-102">Nasıl yapılır: tarih ve saat aritmetiği saat dilimini kullanır</span><span class="sxs-lookup"><span data-stu-id="f7e19-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="f7e19-103">Normalde, zaman, tarih gerçekleştirmek ve aritmetik kullanarak istediğiniz zaman <xref:System.DateTime> veya <xref:System.DateTimeOffset> değerleri, sonuç tüm saat dilimi ayarlama kuralları yansıtır değil.</span><span class="sxs-lookup"><span data-stu-id="f7e19-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="f7e19-104">Bu tarih ve saat değerinin saat dilimi açıkça tanımlanabilen olsa bile geçerlidir (örneğin, <xref:System.DateTime.Kind%2A> özelliği ayarlanmış <xref:System.DateTimeKind.Local>).</span><span class="sxs-lookup"><span data-stu-id="f7e19-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="f7e19-105">Bu konuda, belirli bir saat dilimine ait tarih ve saat değerleri aritmetik işlemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7e19-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="f7e19-106">Aritmetik işlemler sonuçlarını saat diliminin ayarlama kuralları yansıtır.</span><span class="sxs-lookup"><span data-stu-id="f7e19-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="f7e19-107">Tarih ve saat aritmetiği ayarlama kuralları uygulamak için</span><span class="sxs-lookup"><span data-stu-id="f7e19-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="f7e19-108">Tarih ve saat değeri ait olduğu saat dilimi ile yakından Kuplaj bazı yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f7e19-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="f7e19-109">Örneğin, tarih ve saat değeri ile kendi saat dilimi içeren bir yapıyı bildirme.</span><span class="sxs-lookup"><span data-stu-id="f7e19-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="f7e19-110">Aşağıdaki örnek, bağlamak için bu yaklaşımı kullanır. bir <xref:System.DateTime> değeri, saat dilimi ile.</span><span class="sxs-lookup"><span data-stu-id="f7e19-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="f7e19-111">Bir saat ya da çağırarak Eşgüdümlü Evrensel Saat (UTC) dönüştürmek <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> yöntemi veya <xref:System.TimeZoneInfo.ConvertTime%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7e19-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="f7e19-112">UTC saati aritmetik işlemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="f7e19-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="f7e19-113">Saati UTC özgün zaman ilişkili saat dilimi çağırarak Dönüştür <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f7e19-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="f7e19-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7e19-114">Example</span></span>

<span data-ttu-id="f7e19-115">Aşağıdaki örnek 9 Mart 2008'e iki saat ve otuz dakika, 1: 30'da ekler.</span><span class="sxs-lookup"><span data-stu-id="f7e19-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="f7e19-116">Orta Standart Saati.</span><span class="sxs-lookup"><span data-stu-id="f7e19-116">Central Standard Time.</span></span> <span data-ttu-id="f7e19-117">Saat diliminin gün ışığından yararlanma saati geçiş otuz dakika sonra 2: 00'da gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f7e19-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="f7e19-118">9 Mart 2008'de.</span><span class="sxs-lookup"><span data-stu-id="f7e19-118">on March 9, 2008.</span></span> <span data-ttu-id="f7e19-119">Örnek önceki bölümde listelenen dört adımdan oluşur olduğundan, sonuçta elde edilen zaman olarak 5: 00'da doğru şekilde rapor</span><span class="sxs-lookup"><span data-stu-id="f7e19-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="f7e19-120">9 Mart 2008'de.</span><span class="sxs-lookup"><span data-stu-id="f7e19-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="f7e19-121">Her ikisi de <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri ait oldukları her saat diliminden ilişkisi.</span><span class="sxs-lookup"><span data-stu-id="f7e19-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="f7e19-122">Tarih ve saat aritmetiği bir saat diliminin ayarlama kuralları otomatik olarak uygulanan bir şekilde gerçekleştirmek için hangi bir tüm tarih ve saat değeri ait saat dilimi hemen tanımlanabilen olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7e19-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="f7e19-123">Bu, bir tarih ve saat ve onun ilişkili saat dilimi sıkı şekilde bağlı gerekir, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f7e19-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="f7e19-124">Aşağıdakiler dahil Bunu yapmak için birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="f7e19-124">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="f7e19-125">Her zaman bir uygulamada kullanılan belirli bir saat dilimine ait varsayalım.</span><span class="sxs-lookup"><span data-stu-id="f7e19-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="f7e19-126">Bazı durumlarda uygun olsa da bu yaklaşım sınırlı esneklik ve büyük olasılıkla sınırlı taşınabilirlik sunar.</span><span class="sxs-lookup"><span data-stu-id="f7e19-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="f7e19-127">Bir tarih ve saat ekleyerek ilişkili kendi saat dilimi ile iki tür alanları olarak sıkı bir şekilde couples bir türünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f7e19-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="f7e19-128">Bu yaklaşım, tarih ve saat ve saat dilimi iki üye alanlarında depolamak için bir yapısını tanımlar kod örneğindeki kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7e19-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="f7e19-129">Örnek üzerinde aritmetik işlemler gerçekleştirmek nasıl gösterilmektedir <xref:System.DateTime> saat dilimi ayarlama kuralları sonucu uygulanan böylece değerleri.</span><span class="sxs-lookup"><span data-stu-id="f7e19-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="f7e19-130">Ancak, <xref:System.DateTimeOffset> değerleri kolayca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7e19-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="f7e19-131">Aşağıdaki örnekte, nasıl özgün örnekteki kod kullanmak için uyarlanmış olabileceği gösterilmektedir <xref:System.DateTimeOffset> yerine <xref:System.DateTime> değerleri.</span><span class="sxs-lookup"><span data-stu-id="f7e19-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="f7e19-132">Bu ek yalnızca gerçekleştirilirse unutmayın <xref:System.DateTimeOffset> ilk sonuç doğru noktası zamanında yansıtır UTC'ye dönüştürme, ancak kendi uzaklık belirtilen saat dilimi, o zaman için yansıtmaz olmadan değeri.</span><span class="sxs-lookup"><span data-stu-id="f7e19-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="f7e19-133">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="f7e19-133">Compiling the code</span></span>

<span data-ttu-id="f7e19-134">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f7e19-134">This example requires:</span></span>

* <span data-ttu-id="f7e19-135">Bir başvuru System.Core.dll projeye eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="f7e19-135">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="f7e19-136">Olduğunu <xref:System> ad alanı ile aktarılabilir `using` deyimi (C# kodunda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="f7e19-136">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7e19-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7e19-137">See also</span></span>

<span data-ttu-id="f7e19-138">[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md)</span><span class="sxs-lookup"><span data-stu-id="f7e19-138">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md)</span></span>

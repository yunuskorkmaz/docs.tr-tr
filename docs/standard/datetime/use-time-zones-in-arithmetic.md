---
title: 'Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma'
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
ms.openlocfilehash: 1acd53fad6b0ab173f855850353339190ebdd893
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132535"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="ec782-102">Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="ec782-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="ec782-103">Genellikle, <xref:System.DateTime> veya <xref:System.DateTimeOffset> değerlerini kullanarak tarih ve saat aritmetiği gerçekleştirdiğinizde, sonuç hiçbir saat dilimi ayarlama kuralını yansıtmaz.</span><span class="sxs-lookup"><span data-stu-id="ec782-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="ec782-104">Bu, tarih ve saat değerinin saat dilimi açıkça tanımlanabilir olsa da (örneğin, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local>olarak ayarlandığında) geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ec782-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="ec782-105">Bu konu, belirli bir saat dilimine ait tarih ve saat değerleri üzerinde aritmetik işlemlerin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec782-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="ec782-106">Aritmetik işlemlerin sonuçları, saat diliminin ayarlama kurallarını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="ec782-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="ec782-107">Tarih ve saat aritmetiğinin ayarlama kurallarını uygulamak için</span><span class="sxs-lookup"><span data-stu-id="ec782-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="ec782-108">Bir tarih ve saat değerini, ait olduğu saat dilimiyle bir daha yakından eşlenme yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ec782-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="ec782-109">Örneğin, hem tarih hem de saat değerini ve saat dilimini içeren bir yapı bildirin.</span><span class="sxs-lookup"><span data-stu-id="ec782-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="ec782-110">Aşağıdaki örnek, bir <xref:System.DateTime> değerini saat dilimiyle bağlamak için bu yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ec782-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="ec782-111"><xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> yöntemini ya da <xref:System.TimeZoneInfo.ConvertTime%2A> yöntemini çağırarak bir saati Eşgüdümlü Evrensel Saat (UTC) olarak dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="ec782-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="ec782-112">Aritmetik işlemi UTC saat üzerinde gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="ec782-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="ec782-113"><xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemini çağırarak UTC 'den ilk saatin ilişkili saat dilimine dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="ec782-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="ec782-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec782-114">Example</span></span>

<span data-ttu-id="ec782-115">Aşağıdaki örnek, 9 Mart 2008 ' de saat 1:30 ' de 2 saat ve otuz dakika ekler.</span><span class="sxs-lookup"><span data-stu-id="ec782-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="ec782-116">Merkezi Standart Saati.</span><span class="sxs-lookup"><span data-stu-id="ec782-116">Central Standard Time.</span></span> <span data-ttu-id="ec782-117">Saat diliminin gün ışığından yararlanma saatine geçiş süresi otuz dakika sonra, 2:00 saat</span><span class="sxs-lookup"><span data-stu-id="ec782-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="ec782-118">9 Mart 2008 ' de.</span><span class="sxs-lookup"><span data-stu-id="ec782-118">on March 9, 2008.</span></span> <span data-ttu-id="ec782-119">Örnek, önceki bölümde listelenen dört adımı takip ettiğinden, sonuç süresini 5:00 olarak doğru şekilde bildiriyor</span><span class="sxs-lookup"><span data-stu-id="ec782-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="ec782-120">9 Mart 2008 ' de.</span><span class="sxs-lookup"><span data-stu-id="ec782-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="ec782-121"><xref:System.DateTime> ve <xref:System.DateTimeOffset> değerlerinin, ait oldukları herhangi bir saat diliminden ilişkisi kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ec782-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="ec782-122">Tarih ve saat aritmetiğini otomatik olarak bir saat dilimi ayarlama kuralları uygulayan bir şekilde gerçekleştirmek için, herhangi bir tarih ve saat değerinin ait olduğu saat dilimi hemen tanınabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec782-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="ec782-123">Bu, bir tarih ve saatin ve ilişkili saat diliminin sıkı bir şekilde bağlanmış olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ec782-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="ec782-124">Bunu yapmak için aşağıdakiler dahil olmak üzere çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="ec782-124">There are several ways to do this, which include the following:</span></span>

- <span data-ttu-id="ec782-125">Bir uygulamada kullanılan tüm saatlerin belirli bir saat dilimine ait olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="ec782-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="ec782-126">Bazı durumlarda uygun olsa da, bu yaklaşım sınırlı esneklik ve muhtemelen sınırlı taşınabilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec782-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

- <span data-ttu-id="ec782-127">Her iki türü de dahil olmak üzere, bir tarih ve saati ilişkili saat dilimiyle sıkı bir şekilde birbirine bağlayan bir tür tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ec782-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="ec782-128">Bu yaklaşım, tarih ve saat ve saat dilimini iki üye alanında depolamak için bir yapıyı tanımlayan kod örneğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ec782-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="ec782-129">Örnek, zaman dilimi ayarlama kurallarının sonuca uygulanması için <xref:System.DateTime> değerler üzerinde aritmetik işlemlerin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec782-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="ec782-130">Ancak, <xref:System.DateTimeOffset> değerleri yalnızca kolayca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec782-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="ec782-131">Aşağıdaki örnek, özgün örnekteki kodun <xref:System.DateTime> değerleri yerine <xref:System.DateTimeOffset> kullanmak için nasıl uyarlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec782-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="ec782-132">Bu ekleme işlemi ilk olarak UTC 'ye dönüştürmeden <xref:System.DateTimeOffset> değer üzerinde gerçekleştirildiğinde, sonuç doğru noktayı yansıtır, ancak bu süre için belirlenen saat dilimini göstermez.</span><span class="sxs-lookup"><span data-stu-id="ec782-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="ec782-133">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="ec782-133">Compiling the code</span></span>

<span data-ttu-id="ec782-134">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ec782-134">This example requires:</span></span>

- <span data-ttu-id="ec782-135"><xref:System> ad alanı `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir).</span><span class="sxs-lookup"><span data-stu-id="ec782-135">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec782-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec782-136">See also</span></span>

- [<span data-ttu-id="ec782-137">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="ec782-137">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="ec782-138">Tarih ve saatlerle aritmetik işlemler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ec782-138">Performing arithmetic operations with dates and times</span></span>](../../../docs/standard/datetime/performing-arithmetic-operations.md)

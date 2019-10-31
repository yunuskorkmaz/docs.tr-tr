---
title: 'Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 2e3a58ffe8332e0afec62461f6897d673e1da09f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131999"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="6ae26-102">Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri</span><span class="sxs-lookup"><span data-stu-id="6ae26-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="6ae26-103">Birçok uygulamada, bir tarih ve saat değeri, bir zamanda tek bir noktayı kesin bir şekilde tanımlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ae26-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="6ae26-104">Bu konuda, geri yüklenen değerin kaydedilen değerle aynı zamanı tanımladığı şekilde, bir <xref:System.DateTime> değerini, bir <xref:System.DateTimeOffset> değerini ve saat dilimi bilgileriyle tarih ve saat değerlerini kaydetme ve geri yükleme işlemlerinin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="6ae26-105">Bir DateTime değerini gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="6ae26-105">To round-trip a DateTime value</span></span>

1. <span data-ttu-id="6ae26-106"><xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metodunu "o" biçim belirticisiyle çağırarak <xref:System.DateTime> değerini dize gösterimine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="6ae26-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="6ae26-107"><xref:System.DateTime> değerin dize gösterimini bir dosyaya kaydedin veya bir işlem, uygulama etki alanı veya makine sınırında geçirin.</span><span class="sxs-lookup"><span data-stu-id="6ae26-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="6ae26-108"><xref:System.DateTime> değerini temsil eden dizeyi alın.</span><span class="sxs-lookup"><span data-stu-id="6ae26-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="6ae26-109"><xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi çağırın ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> `styles` parametresinin değeri olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="6ae26-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="6ae26-110">Aşağıdaki örnek, bir <xref:System.DateTime> değerini nasıl yuvarlayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="6ae26-111"><xref:System.DateTime> bir değeri yuvarlayıp, bu teknik tüm yerel ve evrensel zamanlar için saati başarıyla korur.</span><span class="sxs-lookup"><span data-stu-id="6ae26-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="6ae26-112">Örneğin, yerel bir <xref:System.DateTime> değeri ABD Pasifik standart saat dilimindeki bir sisteme kaydedilirse ve ABD Orta standart saat dilimindeki bir sisteme geri yüklenirse, geri yükleme tarihi ve saati özgün saatten iki saat sonra olur iki saat dilimi arasındaki zaman farkını yansıtan.</span><span class="sxs-lookup"><span data-stu-id="6ae26-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="6ae26-113">Ancak, bu teknik belirtilmeyen süreler için doğru değildir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="6ae26-114"><xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified> olan tüm <xref:System.DateTime> değerleri, yerel saatmiş gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="6ae26-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="6ae26-115">Böyle bir durum söz konusu değilse, <xref:System.DateTime> doğru zaman noktasını başarıyla tanımmaz.</span><span class="sxs-lookup"><span data-stu-id="6ae26-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="6ae26-116">Bu sınırlamanın geçici çözümü, kaydetme ve geri yükleme işlemi için saat dilimiyle birlikte bir tarih ve saat değeri sıkı bir şekilde bir tarih ve saat değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="6ae26-117">Bir DateTimeOffset değerini gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="6ae26-117">To round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="6ae26-118"><xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodunu "o" biçim belirticisiyle çağırarak <xref:System.DateTimeOffset> değerini dize gösterimine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="6ae26-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="6ae26-119"><xref:System.DateTimeOffset> değerin dize gösterimini bir dosyaya kaydedin veya bir işlem, uygulama etki alanı veya makine sınırında geçirin.</span><span class="sxs-lookup"><span data-stu-id="6ae26-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="6ae26-120"><xref:System.DateTimeOffset> değerini temsil eden dizeyi alın.</span><span class="sxs-lookup"><span data-stu-id="6ae26-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="6ae26-121"><xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi çağırın ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> `styles` parametresinin değeri olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="6ae26-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="6ae26-122">Aşağıdaki örnek, bir <xref:System.DateTimeOffset> değerini nasıl yuvarlayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="6ae26-123">Bu teknik her zaman kesin olarak bir <xref:System.DateTimeOffset> değerini tek bir zaman noktası olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ae26-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="6ae26-124">Bu değer daha sonra <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi çağırarak Eşgüdümlü Evrensel Saat (UTC) olarak dönüştürülebilir veya <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> veya <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi çağırarak belirli bir saat dilimindeki zamana dönüştürülebilirler.</span><span class="sxs-lookup"><span data-stu-id="6ae26-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6ae26-125">Bu tekniğin önemli sınırlaması, belirli bir saat dilimindeki süreyi temsil eden bir <xref:System.DateTimeOffset> değeri üzerinde gerçekleştirildiğinde tarih ve saat aritmetiği bu saat dilimi için doğru sonuçlar üretmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="6ae26-126">Bunun nedeni, <xref:System.DateTimeOffset> bir değeri örneklendirilirken, onun saat diliminden bir ilişkisi olmasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="6ae26-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="6ae26-127">Bu nedenle, tarih ve saat hesaplamaları gerçekleştirirken bu saat diliminin ayarlama kuralları artık uygulanabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="6ae26-128">Hem tarih hem de saat değeri ile buna eşlik eden saat dilimini içeren özel bir tür tanımlayarak bu soruna geçici bir çözüm bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ae26-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="6ae26-129">Bir tarih ve saat değerini kendi saat dilimiyle gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="6ae26-129">To round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="6ae26-130">İki alan içeren bir sınıf veya yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6ae26-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="6ae26-131">İlk alan bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> nesnesidir ve ikincisi bir <xref:System.TimeZoneInfo> nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="6ae26-132">Aşağıdaki örnek bu tür bir türün basit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="6ae26-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="6ae26-133">Sınıfı <xref:System.SerializableAttribute> özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="6ae26-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="6ae26-134"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> yöntemi kullanılarak nesneyi seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="6ae26-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="6ae26-135"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> yöntemi kullanarak nesneyi geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="6ae26-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="6ae26-136">Seri durumdan çıkarılan C#nesneyi uygun türdeki bir nesneye atama (ın) veya dönüştürme (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6ae26-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="6ae26-137">Aşağıdaki örnek hem tarih hem de saat ve saat dilimi bilgilerini depolayan bir nesneyi nasıl yuvarlayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="6ae26-138">Bu teknik, Birleşik tarih ve saat ve saat dilimi nesnesinin uygulanması tarih değerinin ile eşitlenmemiş hale gelmesine izin vermediğinden, her zaman hem ve sonra hem de kaydedildikten ve geri yüklendikten sonra doğru zaman noktasını yansıtmalıdır. Saat dilimi değeri.</span><span class="sxs-lookup"><span data-stu-id="6ae26-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="6ae26-139">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6ae26-139">Compiling the Code</span></span>

<span data-ttu-id="6ae26-140">Bu örneklerde şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="6ae26-140">These examples require:</span></span>

- <span data-ttu-id="6ae26-141">Aşağıdaki ad alanları `using` deyimlerle veya C# Visual Basic `Imports` deyimleriyle içeri aktarılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="6ae26-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="6ae26-142"><xref:System> (C# yalnızca).</span><span class="sxs-lookup"><span data-stu-id="6ae26-142"><xref:System> (C# only).</span></span>

  - <span data-ttu-id="6ae26-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ae26-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="6ae26-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ae26-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="6ae26-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ae26-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="6ae26-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ae26-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="6ae26-147">`DateInTimeZone` sınıfından başka her kod örneği, yöntemlere kaydırılmış ve `Main` yönteminden çağrılan bir sınıfa veya Visual Basic modülüne eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="6ae26-147">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ae26-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ae26-148">See also</span></span>

- [<span data-ttu-id="6ae26-149">Biçimlendirme İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6ae26-149">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)
- [<span data-ttu-id="6ae26-150">DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="6ae26-150">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)
- [<span data-ttu-id="6ae26-151">Standart Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="6ae26-151">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)

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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131999"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="237ed-102">Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri</span><span class="sxs-lookup"><span data-stu-id="237ed-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="237ed-103">Birçok uygulamada, bir tarih ve saat değeri, zaman içinde tek bir noktayı kesin olarak tanımlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="237ed-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="237ed-104">Bu konu, geri yüklenen <xref:System.DateTime> değerin <xref:System.DateTimeOffset> kaydedilen değerle aynı zamanı tanımlaması için saat dilimi bilgileriyle bir değeri, değeri ve tarih ve saat değerini nasıl kaydedip geri yükleyeceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="237ed-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="237ed-105">Bir DateTime değerini gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="237ed-105">To round-trip a DateTime value</span></span>

1. <span data-ttu-id="237ed-106">Yöntemi <xref:System.DateTime> "o" biçim belirtimi ile çağırarak değeri dize gösterimine dönüştürün. <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="237ed-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="237ed-107">Değerin dize <xref:System.DateTime> temsilini bir dosyaya kaydedin veya bir işlem, uygulama etki alanı veya makine sınırı boyunca geçirin.</span><span class="sxs-lookup"><span data-stu-id="237ed-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="237ed-108">Değeri temsil eden <xref:System.DateTime> dizeyi alın.</span><span class="sxs-lookup"><span data-stu-id="237ed-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="237ed-109">Yöntemi <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> çağırın ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> parametrenin `styles` değeri olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="237ed-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="237ed-110">Aşağıdaki örnekte, bir <xref:System.DateTime> değerin gidiş-dönüş nasıl yapılacağını gösterin.</span><span class="sxs-lookup"><span data-stu-id="237ed-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="237ed-111">Bir <xref:System.DateTime> değeri yuvarlattığında, bu teknik tüm yerel ve evrensel zamanlar için zamanı başarıyla korur.</span><span class="sxs-lookup"><span data-stu-id="237ed-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="237ed-112">Örneğin, yerel <xref:System.DateTime> bir değer ABD Pasifik Standart Saat dilimindeki bir sisteme kaydedilir ve ABD Merkezi Standart Saat dilimindeki bir sistemde geri yüklenirse, geri yüklenen tarih ve saat, iki saat dilimi arasındaki saat farkını yansıtan özgün saatten iki saat sonra olur.</span><span class="sxs-lookup"><span data-stu-id="237ed-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="237ed-113">Ancak, bu teknik mutlaka belirtilmeyen kez doğru değildir.</span><span class="sxs-lookup"><span data-stu-id="237ed-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="237ed-114">Özelliği <xref:System.DateTime> yerel <xref:System.DateTime.Kind%2A> zamanlarmış gibi kabul <xref:System.DateTimeKind.Unspecified> edilen tüm değerler.</span><span class="sxs-lookup"><span data-stu-id="237ed-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="237ed-115">Bu durumda değilse, <xref:System.DateTime> başarıyla zaman içinde doğru noktası tanımlamak olmaz.</span><span class="sxs-lookup"><span data-stu-id="237ed-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="237ed-116">Bu sınırlama için geçici çözüm sıkıca kaydetmek ve işlemi geri yüklemek için saat dilimi ile bir tarih ve saat değeri çift etmektir.</span><span class="sxs-lookup"><span data-stu-id="237ed-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="237ed-117">Bir DateTimeOffset değerini gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="237ed-117">To round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="237ed-118">Yöntemi <xref:System.DateTimeOffset> "o" biçim belirtimi ile çağırarak değeri dize gösterimine dönüştürün. <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="237ed-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="237ed-119">Değerin dize <xref:System.DateTimeOffset> temsilini bir dosyaya kaydedin veya bir işlem, uygulama etki alanı veya makine sınırı boyunca geçirin.</span><span class="sxs-lookup"><span data-stu-id="237ed-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="237ed-120">Değeri temsil eden <xref:System.DateTimeOffset> dizeyi alın.</span><span class="sxs-lookup"><span data-stu-id="237ed-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="237ed-121">Yöntemi <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> çağırın ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> parametrenin `styles` değeri olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="237ed-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="237ed-122">Aşağıdaki örnekte, bir <xref:System.DateTimeOffset> değerin gidiş-dönüş nasıl yapılacağını gösterin.</span><span class="sxs-lookup"><span data-stu-id="237ed-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="237ed-123">Bu teknik her zaman <xref:System.DateTimeOffset> bir değeri zaman içinde tek bir nokta olarak kesin olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="237ed-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="237ed-124">Değer daha sonra <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi çağırarak Eşgüdümlü Evrensel Saat'e (UTC) dönüştürülebilir veya belirli bir saat dilimindeki <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> saate veya yönteme çağrılarek dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="237ed-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="237ed-125">Bu tekniğin en önemli sınırlaması, belirli bir saat dilimindeki zamanı temsil eden bir <xref:System.DateTimeOffset> değer üzerinde gerçekleştirilen tarih ve saat aritmetik, o saat dilimi için doğru sonuçlar üretemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="237ed-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="237ed-126">Bunun nedeni, <xref:System.DateTimeOffset> bir değer anında olduğunda, saat diliminden kopuk olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="237ed-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="237ed-127">Bu nedenle, tarih ve saat hesaplamaları gerçekleştirirken bu saat diliminin ayarlama kuralları artık uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="237ed-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="237ed-128">Hem tarih hem de saat değerini ve beraberindeki saat dilimini içeren özel bir tür tanımlayarak bu sorunu çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="237ed-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="237ed-129">Bir tarih ve saat değerini kendi saat dilimiyle gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="237ed-129">To round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="237ed-130">İki alaniçeren bir sınıf veya yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="237ed-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="237ed-131">İlk alan bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> nesne, ikincisi ise <xref:System.TimeZoneInfo> nesnedir.</span><span class="sxs-lookup"><span data-stu-id="237ed-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="237ed-132">Aşağıdaki örnek, böyle bir türün basit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="237ed-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="237ed-133">Sınıfı öznitelikile <xref:System.SerializableAttribute> işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="237ed-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="237ed-134">Yöntemi kullanarak nesneyi <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> serileştirin.</span><span class="sxs-lookup"><span data-stu-id="237ed-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="237ed-135">Yöntemi kullanarak nesneyi geri yükleyin. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A></span><span class="sxs-lookup"><span data-stu-id="237ed-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="237ed-136">Deserialized nesneyi (C#'da) veya dönüştürme (Visual Basic'te) uygun türdeki bir nesneye dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="237ed-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="237ed-137">Aşağıdaki örnek, hem tarih hem de saat dilimi bilgilerini depolayan bir nesneyi nasıl gidiş-dönüş olarak depoladığını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="237ed-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="237ed-138">Bu teknik, birleştirilmiş tarih ve saat ve saat dilimi nesnesinin uygulanmasının tarih değerinin senkronize olmamasını gerektirmemesi koşuluyla, kaydedilen ve geri yüklendikten sonra her zaman doğru zaman noktasını net bir şekilde yansıtmalıdır. saat dilimi değeri.</span><span class="sxs-lookup"><span data-stu-id="237ed-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="237ed-139">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="237ed-139">Compiling the Code</span></span>

<span data-ttu-id="237ed-140">Bu örnekler şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="237ed-140">These examples require:</span></span>

- <span data-ttu-id="237ed-141">Aşağıdaki ad alanlarının C# `using` ifadeleri veya `Imports` Visual Basic deyimleri ile içe aktarılması:</span><span class="sxs-lookup"><span data-stu-id="237ed-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="237ed-142"><xref:System>(Yalnızca C# ).</span><span class="sxs-lookup"><span data-stu-id="237ed-142"><xref:System> (C# only).</span></span>

  - <span data-ttu-id="237ed-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="237ed-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="237ed-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="237ed-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="237ed-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="237ed-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="237ed-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="237ed-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="237ed-147">`DateInTimeZone` Sınıf dışındaki her kod örneği, bir sınıfa veya Visual Basic modülüne eklenmeli, `Main` yöntemlere sarılmalı ve yöntemden çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="237ed-147">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="237ed-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="237ed-148">See also</span></span>

- [<span data-ttu-id="237ed-149">Biçimlendirme İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="237ed-149">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)
- [<span data-ttu-id="237ed-150">DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim</span><span class="sxs-lookup"><span data-stu-id="237ed-150">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)
- [<span data-ttu-id="237ed-151">Standart Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="237ed-151">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)

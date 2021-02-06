---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: gidiş dönüş Tarih ve saat değerleri'
title: 'Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET], round-trip values
- time zones [.NET], round-trip date and time values
- time [.NET], round-trip values
- formatting strings [.NET], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 66f1ac2e8b51d7117f771a966a3c01cff24b78a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642766"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="29c1c-103">Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri</span><span class="sxs-lookup"><span data-stu-id="29c1c-103">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="29c1c-104">Birçok uygulamada, bir tarih ve saat değeri, bir zamanda tek bir noktayı kesin bir şekilde tanımlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="29c1c-104">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="29c1c-105">Bu makalede <xref:System.DateTime> , <xref:System.DateTimeOffset> geri yüklenen değerin kaydedilen değerle aynı zamanı tanımladığı şekilde, saat dilimi bilgileriyle bir değerin, bir değerin ve Tarih ve saat değerinin nasıl kaydedileceği ve geri yükleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="29c1c-105">This article shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

## <a name="round-trip-a-datetime-value"></a><span data-ttu-id="29c1c-106">Bir tarih saat değeri gidiş dönüş</span><span class="sxs-lookup"><span data-stu-id="29c1c-106">Round-trip a DateTime value</span></span>

1. <span data-ttu-id="29c1c-107"><xref:System.DateTime> <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> Yöntemi "o" biçim belirticisiyle çağırarak değeri dize gösterimine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="29c1c-107">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="29c1c-108">Değerin dize gösterimini <xref:System.DateTime> bir dosyaya kaydedin veya bir işlem, uygulama etki alanı ya da makine sınırı üzerinden geçirin.</span><span class="sxs-lookup"><span data-stu-id="29c1c-108">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="29c1c-109">Değeri temsil eden dizeyi alın <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="29c1c-109">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="29c1c-110">Yöntemini çağırın <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> parametresinin değeri olarak geçirin `styles` .</span><span class="sxs-lookup"><span data-stu-id="29c1c-110">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="29c1c-111">Aşağıdaki örnek, bir değeri nasıl yuvarlayacağını gösterir <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="29c1c-111">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="29c1c-112">Bir değeri yuvarlayıp <xref:System.DateTime> , bu teknik tüm yerel ve evrensel zamanlar için saati başarıyla korur.</span><span class="sxs-lookup"><span data-stu-id="29c1c-112">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="29c1c-113">Örneğin, yerel bir <xref:System.DateTime> değer ABD Pasifik standart saat dilimindeki bir sisteme kaydedilirse ve ABD Orta standart saat dilimindeki bir sisteme geri yüklenirse, geri yükleme tarihi ve saati, ilk zamandan sonraki iki saat sonra olur ve bu da iki saat dilimi arasındaki zaman farkını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="29c1c-113">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="29c1c-114">Ancak, bu teknik belirtilmeyen süreler için doğru değildir.</span><span class="sxs-lookup"><span data-stu-id="29c1c-114">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="29c1c-115"><xref:System.DateTime> <xref:System.DateTime.Kind%2A> Özelliği <xref:System.DateTimeKind.Unspecified> Yerel saatmiş gibi kabul edilen tüm değerler.</span><span class="sxs-lookup"><span data-stu-id="29c1c-115">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="29c1c-116">Yerel bir zaman değilse, <xref:System.DateTime> doğru zaman noktasını başarıyla tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="29c1c-116">If it's not a local time, the <xref:System.DateTime> doesn't successfully identify the correct point in time.</span></span> <span data-ttu-id="29c1c-117">Bu sınırlamanın geçici çözümü, kaydetme ve geri yükleme işlemi için saat dilimiyle birlikte bir tarih ve saat değeri sıkı bir şekilde bir tarih ve saat değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="29c1c-117">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

## <a name="round-trip-a-datetimeoffset-value"></a><span data-ttu-id="29c1c-118">Bir DateTimeOffset değerini gidiş dönüş</span><span class="sxs-lookup"><span data-stu-id="29c1c-118">Round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="29c1c-119"><xref:System.DateTimeOffset> <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> Yöntemi "o" biçim belirticisiyle çağırarak değeri dize gösterimine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="29c1c-119">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="29c1c-120">Değerin dize gösterimini <xref:System.DateTimeOffset> bir dosyaya kaydedin veya bir işlem, uygulama etki alanı ya da makine sınırı üzerinden geçirin.</span><span class="sxs-lookup"><span data-stu-id="29c1c-120">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="29c1c-121">Değeri temsil eden dizeyi alın <xref:System.DateTimeOffset> .</span><span class="sxs-lookup"><span data-stu-id="29c1c-121">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="29c1c-122">Yöntemini çağırın <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> ve <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> parametresinin değeri olarak geçirin `styles` .</span><span class="sxs-lookup"><span data-stu-id="29c1c-122">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="29c1c-123">Aşağıdaki örnek, bir değeri nasıl yuvarlayacağını gösterir <xref:System.DateTimeOffset> .</span><span class="sxs-lookup"><span data-stu-id="29c1c-123">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="29c1c-124">Bu teknik her zaman, bir <xref:System.DateTimeOffset> değeri bir zaman içinde tek bir noktaya kadar kesin olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="29c1c-124">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="29c1c-125">Bu değer, yöntemi çağırarak Eşgüdümlü Evrensel saate (UTC) dönüştürülebilir <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> veya ya da yöntemi çağırarak belirli bir saat dilimindeki zamana dönüştürülebilir <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="29c1c-125">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="29c1c-126">Bu tekniğin önemli sınırlaması, belirli bir saat dilimindeki süreyi temsil eden bir değer üzerinde gerçekleştirildiğinde tarih ve saat aritmetiği bu <xref:System.DateTimeOffset> saat dilimi için doğru sonuçlar üretmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="29c1c-126">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="29c1c-127">Bunun nedeni, bir <xref:System.DateTimeOffset> değer örneklendirilirken, onun saat diliminden bir ilişkisi olmasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="29c1c-127">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="29c1c-128">Bu nedenle, tarih ve saat hesaplamaları gerçekleştirirken bu saat diliminin ayarlama kuralları artık uygulanabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="29c1c-128">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="29c1c-129">Hem tarih hem de saat değeri ile buna eşlik eden saat dilimini içeren özel bir tür tanımlayarak bu soruna geçici bir çözüm bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29c1c-129">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="29c1c-130">Tarih ve saat değerini saat dilimiyle gidiş dönüş</span><span class="sxs-lookup"><span data-stu-id="29c1c-130">Round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="29c1c-131">İki alan içeren bir sınıf veya yapı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="29c1c-131">Define a class or a structure with two fields.</span></span> <span data-ttu-id="29c1c-132">İlk alan bir <xref:System.DateTime> ya da bir <xref:System.DateTimeOffset> nesnedir ve ikincisi bir <xref:System.TimeZoneInfo> nesnedir.</span><span class="sxs-lookup"><span data-stu-id="29c1c-132">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="29c1c-133">Aşağıdaki örnek bu tür bir türün basit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="29c1c-133">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="29c1c-134">Sınıfı özniteliği ile işaretleyin <xref:System.SerializableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="29c1c-134">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="29c1c-135">Yöntemini kullanarak nesneyi seri hale getirme <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="29c1c-135">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="29c1c-136">Yöntemini kullanarak nesneyi geri yükleyin <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> .</span><span class="sxs-lookup"><span data-stu-id="29c1c-136">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="29c1c-137">Atama (C#) veya seri durumdan çıkarılan nesneyi uygun türdeki bir nesneye (Visual Basic) dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="29c1c-137">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="29c1c-138">Aşağıdaki örnek, hem saat dilimini hem de tarih ve saat bilgilerini depolayan bir nesneyi nasıl yuvarlayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29c1c-138">The following example illustrates how to round-trip an object that stores both time zone and date and time information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="29c1c-139">Bu teknik, Birleşik tarih ve saat ve saat dilimi nesnesinin uygulanması tarih değerinin saat dilimi değeriyle eşitlenmesine izin vermediğinden, her zaman hem ve sonra hem de sonrasında doğru zaman noktasını yansıtmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29c1c-139">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="29c1c-140">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="29c1c-140">Compile the code</span></span>

<span data-ttu-id="29c1c-141">Bu örnekler şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="29c1c-141">These examples require that:</span></span>

- <span data-ttu-id="29c1c-142">Aşağıdaki ad alanları C# `using` yönergeleri veya Visual Basic deyimleri ile içeri aktarılır `Imports` :</span><span class="sxs-lookup"><span data-stu-id="29c1c-142">The following namespaces be imported with C# `using` directives or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="29c1c-143"><xref:System> (Yalnızca C#)</span><span class="sxs-lookup"><span data-stu-id="29c1c-143"><xref:System> (C# only)</span></span>

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- <span data-ttu-id="29c1c-144">Sınıf dışındaki her kod örneği, `DateInTimeZone` metotlara kaydırılmış bir sınıfa veya Visual Basic modüle dahil edilir ve `Main` yönteminden çağırılır.</span><span class="sxs-lookup"><span data-stu-id="29c1c-144">Each code example, other than the `DateInTimeZone` class, be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="29c1c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29c1c-145">See also</span></span>

- [<span data-ttu-id="29c1c-146">DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="29c1c-146">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../datetime/choosing-between-datetime.md)
- [<span data-ttu-id="29c1c-147">Standart Tarih ve saat biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="29c1c-147">Standard Date and Time Format Strings</span></span>](standard-date-and-time-format-strings.md)

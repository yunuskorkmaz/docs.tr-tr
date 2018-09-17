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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b16d135449cad8ed489a8a3e21db326be0fae0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668424"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="8e55a-102">Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri</span><span class="sxs-lookup"><span data-stu-id="8e55a-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="8e55a-103">Birçok uygulamada, bir tarih ve saat değerini, tek bir nokta zaman içinde kesin bir şekilde tanımlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8e55a-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="8e55a-104">Bu konuda, kaydetme ve geri yükleme işlemi gösterilmektedir bir <xref:System.DateTime> değeri bir <xref:System.DateTimeOffset> değer ve bir tarih ve saat değeri zaman ile kaydedilen değer aynı zamanda geri yüklenen değeri tanımlar, böylece bilgi bölge.</span><span class="sxs-lookup"><span data-stu-id="8e55a-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="8e55a-105">Bir DateTime değerini gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="8e55a-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="8e55a-106">Dönüştürme <xref:System.DateTime> çağırarak dize gösterimine değerine <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> "o" biçim belirteci ile yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e55a-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="8e55a-107">Dize gösterimini kaydedin <xref:System.DateTime> değeri bir dosyaya veya bir işlem, uygulama etki alanı veya makine sınırı arasında geçirin.</span><span class="sxs-lookup"><span data-stu-id="8e55a-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="8e55a-108">Temsil eden dizeyi almak <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="8e55a-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="8e55a-109">Çağrı <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi ve pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> değeri olarak `styles` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8e55a-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="8e55a-110">Aşağıdaki örnekte gösterilmiştir gidiş dönüşlü hale getirmek için nasıl bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="8e55a-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="8e55a-111">Zaman gidiş dönüşü bir <xref:System.DateTime> değeri, bu tekniği başarıyla yerel ve evrensel sürekli süreyle korur.</span><span class="sxs-lookup"><span data-stu-id="8e55a-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="8e55a-112">Örneğin, bir yerel <xref:System.DateTime> değeri ABD'deki bir sistemde kaydedildi Pasifik Standart saat dilimi ve ABD'deki bir sistemde geri Merkezi standart saat dilimi, geri yüklenen tarih ve saat iki saat dilimlerini arasındaki zaman farkı yansıtır özgün saatinden sonraki iki saat olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8e55a-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="8e55a-113">Ancak, bu tekniği için doğru olmak zorunda değildir kez belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="8e55a-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="8e55a-114">Tüm <xref:System.DateTime> ayarlanmış değerleri <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified> yerel zamanlar oldukları gibi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8e55a-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="8e55a-115">Bu durumda değilse <xref:System.DateTime> başarıyla doğru noktası sürede belirtmez.</span><span class="sxs-lookup"><span data-stu-id="8e55a-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="8e55a-116">Bu sınırlamaya geçici çözümü, sıkı bir şekilde bir tarih ve saat değerini kendi saat dilimiyle kaydetme birleştirin ve geri yükleme işlemi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="8e55a-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="8e55a-117">Bir DateTimeOffset değerini gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="8e55a-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="8e55a-118">Dönüştürme <xref:System.DateTimeOffset> çağırarak dize gösterimine değerine <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> "o" biçim belirteci ile yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e55a-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="8e55a-119">Dize gösterimini kaydedin <xref:System.DateTimeOffset> değeri bir dosyaya veya bir işlem, uygulama etki alanı veya makine sınırı arasında geçirin.</span><span class="sxs-lookup"><span data-stu-id="8e55a-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="8e55a-120">Temsil eden dizeyi almak <xref:System.DateTimeOffset> değeri.</span><span class="sxs-lookup"><span data-stu-id="8e55a-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="8e55a-121">Çağrı <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi ve pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> değeri olarak `styles` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8e55a-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="8e55a-122">Aşağıdaki örnekte gösterilmiştir gidiş dönüşlü hale getirmek için nasıl bir <xref:System.DateTimeOffset> değeri.</span><span class="sxs-lookup"><span data-stu-id="8e55a-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="8e55a-123">Bu yöntem her zaman kesin bir şekilde tanımlayan bir <xref:System.DateTimeOffset> zaman içinde tek bir nokta olarak değeri.</span><span class="sxs-lookup"><span data-stu-id="8e55a-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="8e55a-124">Değer daha sonra Eşgüdümlü Evrensel Saat (UTC) çağırarak dönüştürülebilir <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi veya dönüştürülebilir belirli bir saat dilimindeki saati çağırarak <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> veya <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e55a-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8e55a-125">Bu tekniğe ilişkin önemli sınırlama tarihtir ve gerçekleştirilen, zaman, aritmetik bir <xref:System.DateTimeOffset> belirli bir saat dilimindeki saati gösteren bir değer değil, saat dilimi için doğru sonuçlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="8e55a-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="8e55a-126">Bunun sebebi, bir <xref:System.DateTimeOffset> değer örneği, kendi saat diliminden noktanızla ilişkisi silinir.</span><span class="sxs-lookup"><span data-stu-id="8e55a-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="8e55a-127">Bu nedenle, tarih ve saat hesaplamaları gerçekleştirdiğinizde, saat diliminin ayarlama kuralları artık uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8e55a-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="8e55a-128">Bu sorunu geçici olarak bir tarih ve saat değeri ve kendi eşlik eden saat dilimi içeren özel bir tür tanımlayarak çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="8e55a-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="8e55a-129">Bir tarih ve saat değerini kendi saat dilimiyle gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="8e55a-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="8e55a-130">Bir sınıf ya da iki alan bir yapı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e55a-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="8e55a-131">İlk alanı bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> nesne ve ikinci bir <xref:System.TimeZoneInfo> nesne.</span><span class="sxs-lookup"><span data-stu-id="8e55a-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="8e55a-132">Aşağıdaki örnekte, böyle bir türü basit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="8e55a-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="8e55a-133">Sınıf ile işaretle <xref:System.SerializableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8e55a-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="8e55a-134">Nesnesi kullanarak serileştirme <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e55a-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="8e55a-135">Nesnesini kullanarak geri <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e55a-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="8e55a-136">Atama (C# ') veya (Visual Basic'te) seri durumdan çıkarılmış nesne uygun türde bir nesneye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8e55a-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="8e55a-137">Aşağıdaki örnek nasıl tarih ve saat ve saat dilimi bilgilerini depolayan bir nesne gidiş dönüş için gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e55a-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="8e55a-138">Bu teknik, doğru hem önce ve sonra kaydedilip geri, sağlanan uygulama birleştirilmiş tarih ve saat ve saat dilimi nesnenin tarih değeri ile eşitlenmemiş hale izin vermiyor zaman noktası her zaman kesin bir şekilde yansıtmalıdır saat dilimi değeri.</span><span class="sxs-lookup"><span data-stu-id="8e55a-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e55a-139">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8e55a-139">Compiling the Code</span></span>  
 <span data-ttu-id="8e55a-140">Bu örneği gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8e55a-140">These examples require:</span></span>  
  
-   <span data-ttu-id="8e55a-141">Aşağıdaki ad alanlarını C# ile içe aktarılacağını `using` ifadelerini veya Visual Basic `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="8e55a-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="8e55a-142"><xref:System> (Yalnızca C#).</span><span class="sxs-lookup"><span data-stu-id="8e55a-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="8e55a-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e55a-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="8e55a-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e55a-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="8e55a-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e55a-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="8e55a-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e55a-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="8e55a-147">Bir System.Core.dll başvurusu.</span><span class="sxs-lookup"><span data-stu-id="8e55a-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="8e55a-148">Her örnek, dışındaki kod `DateInTimeZone` sınıfı, bir sınıf veya Visual Basic module'u içinde bulunan yöntemlerdeki sarmalanmış ve çağrılır `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e55a-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e55a-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e55a-149">See also</span></span>

- [<span data-ttu-id="8e55a-150">Biçimlendirme İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="8e55a-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [<span data-ttu-id="8e55a-151">DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim</span><span class="sxs-lookup"><span data-stu-id="8e55a-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
- [<span data-ttu-id="8e55a-152">Standart Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="8e55a-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)

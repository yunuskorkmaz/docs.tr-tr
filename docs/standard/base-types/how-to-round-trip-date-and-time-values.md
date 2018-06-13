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
ms.openlocfilehash: 26a1cafc7ed6e497e5aab9cd33654f3aa3d4d98c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573192"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="02222-102">Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri</span><span class="sxs-lookup"><span data-stu-id="02222-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="02222-103">Birçok uygulamada, tarih ve saat değeri tek bir nokta zaman içinde kesin bir şekilde tanımlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="02222-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="02222-104">Bu konuda kaydetme ve geri yükleme gösterilmektedir bir <xref:System.DateTime> değeri, bir <xref:System.DateTimeOffset> değer ve zaman içeren bir tarih ve saat değeri böylece aynı anda kaydedilen değer olarak geri yüklenen değer tanımlayan bilgileri bölge.</span><span class="sxs-lookup"><span data-stu-id="02222-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="02222-105">Bir DateTime değerini gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="02222-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="02222-106">Dönüştürme <xref:System.DateTime> çağırarak kendi dize gösterimi değerine <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> "o" biçim belirticisi yöntemiyle.</span><span class="sxs-lookup"><span data-stu-id="02222-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="02222-107">Dize gösterimini Kaydet <xref:System.DateTime> değer bir dosyaya veya bir işlem, uygulama etki alanı veya makine sınırı arasında geçirin.</span><span class="sxs-lookup"><span data-stu-id="02222-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="02222-108">Temsil eden dize almak <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="02222-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="02222-109">Çağrı <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi ve geçişi <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> değeri olarak `styles` parametresi.</span><span class="sxs-lookup"><span data-stu-id="02222-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="02222-110">Aşağıdaki örnek gösterilmektedir gidiş nasıl bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="02222-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="02222-111">Zaman gidiş bir <xref:System.DateTime> değeri, bu teknik başarıyla her yerel ve evrensel zaman zaman korur.</span><span class="sxs-lookup"><span data-stu-id="02222-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="02222-112">Örneğin, bir yerel varsa <xref:System.DateTime> değeri ABD sisteminde kaydedilir Pasifik Standart saat dilimi ve ABD sisteminde geri Orta standart saat dilimi, geri yüklenen tarih ve saat iki saat dilimi arasındaki zaman farkı yansıtır özgün zamandan sonra iki saat olacaktır.</span><span class="sxs-lookup"><span data-stu-id="02222-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="02222-113">Ancak, bu teknik için mutlaka tam doğru değildir kez belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="02222-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="02222-114">Tüm <xref:System.DateTime> özelliği değerlerini <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified> iseler yerel saat olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="02222-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="02222-115">Bu durumda, değilse <xref:System.DateTime> başarıyla doğru noktası zamanında belirtmez.</span><span class="sxs-lookup"><span data-stu-id="02222-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="02222-116">Bu sınırlamaya geçici çözümü sıkı bir tarih ve saat değeri kayıt için kendi saat dilimi ile eşleştiği ve geri yükleme işlemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="02222-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="02222-117">Bir DateTimeOffset değerini gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="02222-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="02222-118">Dönüştürme <xref:System.DateTimeOffset> çağırarak kendi dize gösterimi değerine <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> "o" biçim belirticisi yöntemiyle.</span><span class="sxs-lookup"><span data-stu-id="02222-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="02222-119">Dize gösterimini Kaydet <xref:System.DateTimeOffset> değer bir dosyaya veya bir işlem, uygulama etki alanı veya makine sınırı arasında geçirin.</span><span class="sxs-lookup"><span data-stu-id="02222-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="02222-120">Temsil eden dize almak <xref:System.DateTimeOffset> değeri.</span><span class="sxs-lookup"><span data-stu-id="02222-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="02222-121">Çağrı <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi ve geçişi <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> değeri olarak `styles` parametresi.</span><span class="sxs-lookup"><span data-stu-id="02222-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="02222-122">Aşağıdaki örnek gösterilmektedir gidiş nasıl bir <xref:System.DateTimeOffset> değeri.</span><span class="sxs-lookup"><span data-stu-id="02222-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="02222-123">Bu yöntem her zaman kesin bir şekilde tanımlayan bir <xref:System.DateTimeOffset> değeri zaman içinde tek bir nokta olarak.</span><span class="sxs-lookup"><span data-stu-id="02222-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="02222-124">Değer daha sonra Eşgüdümlü Evrensel Saat (UTC) çağırarak dönüştürülebilir <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi veya dönüştürülebilir belirli bir saat dilimi zamanında çağırarak <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> veya <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02222-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="02222-125">Bu teknik önemli sınırlandırılmasıdır tarihidir ve üzerinde gerçekleştirildiğinde aritmetik, zaman bir <xref:System.DateTimeOffset> belirli bir saat diliminde saati gösteren bir değer değil, saat diliminin doğru sonuçlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="02222-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="02222-126">Bunun nedeni, zaman bir <xref:System.DateTimeOffset> değeri örneği, kendi saat diliminden ilişkisi.</span><span class="sxs-lookup"><span data-stu-id="02222-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="02222-127">Bu nedenle, tarih ve saat hesaplamaları gerçekleştirdiğinizde, saat diliminin ayarlama kuralları artık uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="02222-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="02222-128">Bir tarih ve saat değeri ile kendi eşlik eden saat dilimi içeren özel bir tür tanımlayarak bu soruna geçici çözüm bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02222-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="02222-129">Bir tarih ve saat değerini kendi saat dilimiyle gidiş dönüşlü hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="02222-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="02222-130">Bir sınıf veya yapı iki alanlarla tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="02222-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="02222-131">İlk alanı bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> nesne ve ikinci bir <xref:System.TimeZoneInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="02222-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="02222-132">Aşağıdaki örnek, bu tür bir türün basit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="02222-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="02222-133">Sınıfı işaretlemek <xref:System.SerializableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="02222-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="02222-134">Kullanarak nesne seri hale <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02222-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="02222-135">Nesnesini kullanarak geri <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02222-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="02222-136">Atama (C# ') veya (Visual Basic'te) için uygun türde bir nesne seri durumdan çıkarılmış Nesne Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="02222-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="02222-137">Aşağıdaki örnek, nasıl tarih ve saat ve saat dilimi bilgilerini depolar gidiş nesneyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="02222-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="02222-138">Bu teknik her zaman belirsizliğe her ikisi de önce ve sonra kaydedilmiş ve geri, sağlanan birleşik tarih ve saat ve saat dilimi nesne uyarlamasını tarih değeri ile eşitlenmemiş hale gelmesine izin vermez zaman doğru noktası yansıtması gerekir saat dilimi değeri.</span><span class="sxs-lookup"><span data-stu-id="02222-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02222-139">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="02222-139">Compiling the Code</span></span>  
 <span data-ttu-id="02222-140">Bu örnekler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="02222-140">These examples require:</span></span>  
  
-   <span data-ttu-id="02222-141">Şu ad alanlarından C# ile içe aktarılacağını `using` ifadelerini veya Visual Basic `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="02222-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="02222-142"><xref:System> (C# yalnızca).</span><span class="sxs-lookup"><span data-stu-id="02222-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="02222-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02222-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="02222-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02222-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="02222-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02222-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="02222-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02222-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="02222-147">System.Core.dll referansı.</span><span class="sxs-lookup"><span data-stu-id="02222-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="02222-148">Her örnek, dışındaki kod `DateInTimeZone` sınıfı, bir sınıf veya Visual Basic modülü dahil, yöntemleri Sarmalanan ve çağrılır `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="02222-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02222-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02222-149">See Also</span></span>  
 [<span data-ttu-id="02222-150">Biçimlendirme İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="02222-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="02222-151">DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçme</span><span class="sxs-lookup"><span data-stu-id="02222-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [<span data-ttu-id="02222-152">Standart Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="02222-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)

---
title: "Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma"
ms.custom: 
ms.date: 03/30/2017
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
- formatting [.NET Framework], dates
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET Framework], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET Framework], day of week
- Weekday function
- day of week [.NET Framework]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET Framework], day of week
- formatting [.NET Framework], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e0628dfefb8da5c11e9927ab5ec98c2feb3fe89f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a><span data-ttu-id="de3aa-102">Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma</span><span class="sxs-lookup"><span data-stu-id="de3aa-102">How to: Extract the Day of the Week from a Specific Date</span></span>
<span data-ttu-id="de3aa-103">.NET Framework sıralı haftanın belirli bir tarih için belirlemek ve yerelleştirilmiş haftanın günü için belirli bir tarih görünen ad için kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="de3aa-103">The .NET Framework makes it easy to determine the ordinal day of the week for a particular date, and to display the localized weekday name for a particular date.</span></span> <span data-ttu-id="de3aa-104">Belirli bir tarihe kadar karşılık gelen haftanın gününü gösteren bir Enum değeri kullanılabilir <xref:System.DateTime.DayOfWeek%2A> veya <xref:System.DateTimeOffset.DayOfWeek%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="de3aa-104">An enumerated value that indicates the day of the week corresponding to a particular date is available from the <xref:System.DateTime.DayOfWeek%2A> or <xref:System.DateTimeOffset.DayOfWeek%2A> property.</span></span> <span data-ttu-id="de3aa-105">Buna karşılık, haftanın günü adı alınırken tarih ve saat değerinin gibi bir biçimlendirme yöntemini çağırarak gerçekleştirilebilen bir biçimlendirme işlemdir `ToString` yöntemi veya <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-105">In contrast, retrieving the weekday name is a formatting operation that can be performed by calling a formatting method, such as a date and time value's `ToString` method or the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="de3aa-106">Bu konu, bu biçimlendirme işlemlerini gerçekleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="de3aa-106">This topic shows how to perform these formatting operations.</span></span>  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a><span data-ttu-id="de3aa-107">Belirli bir tarihten haftanın gününü gösteren bir sayı ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="de3aa-107">To extract a number indicating the day of the week from a specific date</span></span>  
  
1.  <span data-ttu-id="de3aa-108">Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="de3aa-108">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="de3aa-109">Kullanım <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> almak için özelliğini bir <xref:System.DayOfWeek> haftanın gününü gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="de3aa-109">Use the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve a <xref:System.DayOfWeek> value that indicates the day of the week.</span></span>  
  
3.  <span data-ttu-id="de3aa-110">Gerekirse, atama (C# ') veya (Visual Basic'te) dönüştürmek <xref:System.DayOfWeek> bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="de3aa-110">If necessary, cast (in C#) or convert (in Visual Basic) the <xref:System.DayOfWeek> value to an integer.</span></span>  
  
 <span data-ttu-id="de3aa-111">Aşağıdaki örnek, belirli bir tarihten haftanın gününü temsil eden bir tamsayı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="de3aa-111">The following example displays an integer that represents the day of the week of a specific date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a><span data-ttu-id="de3aa-112">Belirli bir tarihten itibaren kısaltılmış haftanın günü adı ayıklanamıyor</span><span class="sxs-lookup"><span data-stu-id="de3aa-112">To extract the abbreviated weekday name from a specific date</span></span>  
  
1.  <span data-ttu-id="de3aa-113">Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="de3aa-113">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="de3aa-114">Geçerli kültür veya belirli bir kültür kısaltılmış haftanın günü adı ayıklayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="de3aa-114">You can extract the abbreviated weekday name of the current culture or of a specific culture:</span></span>  
  
    1.  <span data-ttu-id="de3aa-115">Geçerli kültür için kısaltılmış haftanın günü ad ayıklamak için tarih ve saat değerinin çağrısı <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemi ve "ggg" dize olarak geçirin `format` parametresi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-115">To extract the abbreviated weekday name for the current culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="de3aa-116">Aşağıdaki örnek çağrısı gösterilmektedir <xref:System.DateTime.ToString%28System.String%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-116">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2.  <span data-ttu-id="de3aa-117">Belirli bir kültür için kısaltılmış haftanın günü ad ayıklamak için tarih ve saat değerinin çağrısı <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-117">To extract the abbreviated weekday name for a specific culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="de3aa-118">Bir dizeyi "ggg" olarak geçirmek `format` parametresi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-118">Pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="de3aa-119">Ya da geçirmek bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.DateTimeFormatInfo> hafta içi adı olarak almak istediğiniz kültür temsil eden nesnesi `provider` parametresi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-119">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="de3aa-120">Aşağıdaki kod bir çağrı gösterilmektedir <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemini kullanarak bir <xref:System.Globalization.CultureInfo> fr-FR kültür temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="de3aa-120">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the fr-FR culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a><span data-ttu-id="de3aa-121">Belirli bir tarihten itibaren tam haftanın günü adı ayıklanamıyor</span><span class="sxs-lookup"><span data-stu-id="de3aa-121">To extract the full weekday name from a specific date</span></span>  
  
1.  <span data-ttu-id="de3aa-122">Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="de3aa-122">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="de3aa-123">Tam haftanın günü adı geçerli kültürü veya belirli bir kültür ayıklayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="de3aa-123">You can extract the full weekday name of the current culture or of a specific culture:</span></span>  
  
    1.  <span data-ttu-id="de3aa-124">Geçerli kültür için haftanın günü ad ayıklamak için tarih ve saat değerinin çağrısı <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemi ve "dddd" dize olarak geçirin `format` parametresi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-124">To extract the weekday name for the current culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="de3aa-125">Aşağıdaki örnek çağrısı gösterilmektedir <xref:System.DateTime.ToString%28System.String%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-125">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2.  <span data-ttu-id="de3aa-126">Belirli bir kültür için haftanın günü ad ayıklamak için tarih ve saat değerinin çağrısı <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-126">To extract the weekday name for a specific culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="de3aa-127">Bir dizeyi "dddd" olarak geçirmek `format` parametresi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-127">Pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="de3aa-128">Ya da geçirmek bir <xref:System.Globalization.CultureInfo> veya <xref:System.Globalization.DateTimeFormatInfo> hafta içi adı olarak almak istediğiniz kültür temsil eden nesnesi `provider` parametresi.</span><span class="sxs-lookup"><span data-stu-id="de3aa-128">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="de3aa-129">Aşağıdaki kod bir çağrı gösterilmektedir <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemini kullanarak bir <xref:System.Globalization.CultureInfo> es-ES kültür temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="de3aa-129">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the es-ES culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="de3aa-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="de3aa-130">Example</span></span>  
 <span data-ttu-id="de3aa-131">Örnek çağrıları gösterir <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> özellikleri ve <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> haftanın, kısaltılmış haftanın günü adını ve tam haftanın günü adını gününü temsil eden sayı almak için yöntemleri bir Belirli tarih.</span><span class="sxs-lookup"><span data-stu-id="de3aa-131">The example illustrates calls to the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> properties and the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> methods to retrieve the number that represents the day of the week, the abbreviated weekday name, and the full weekday name for a particular date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 <span data-ttu-id="de3aa-132">Tek tek dilleri yineleme veya tarafından sağlanan işlevleri tamamlayan işlevselliği sağlayabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de3aa-132">Individual languages may provide functionality that duplicates or supplements the functionality provided by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="de3aa-133">Örneğin, Visual Basic iki tür işlevler içerir:</span><span class="sxs-lookup"><span data-stu-id="de3aa-133">For example, Visual Basic includes two such functions:</span></span>  
  
-   <span data-ttu-id="de3aa-134">`Weekday`, belirli bir tarihten haftanın gününü gösteren bir sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="de3aa-134">`Weekday`, which returns a number that indicates the day of the week of a particular date.</span></span> <span data-ttu-id="de3aa-135">Ancak, biri için haftanın ilk günü sıra değerini dikkate <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> özelliği sıfır olarak dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="de3aa-135">It considers the ordinal value of the first day of the week to be one, whereas the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property considers it to be zero.</span></span>  
  
-   <span data-ttu-id="de3aa-136">`WeekdayName`, döndüğü haftanın adını karşılık gelen geçerli kültürün belirli hafta içi günü sayıya.</span><span class="sxs-lookup"><span data-stu-id="de3aa-136">`WeekdayName`, which returns the name of the week in the current culture that corresponds to a particular weekday number.</span></span>  
  
 <span data-ttu-id="de3aa-137">Aşağıdaki örnek Visual Basic kullanımını göstermektedir `Weekday` ve `WeekdayName` işlevleri.</span><span class="sxs-lookup"><span data-stu-id="de3aa-137">The following example illustrates the use of the Visual Basic `Weekday` and `WeekdayName` functions.</span></span>  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 <span data-ttu-id="de3aa-138">Tarafından döndürülen değer de kullanabilirsiniz <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> belirli bir tarihten haftanın günü adını almak için özellik.</span><span class="sxs-lookup"><span data-stu-id="de3aa-138">You can also use the value returned by the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve the weekday name of a particular date.</span></span> <span data-ttu-id="de3aa-139">Bu sadece bir çağrı gerektirir <xref:System.Enum.ToString%2A> yöntemi <xref:System.DayOfWeek> özellik tarafından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="de3aa-139">This requires only a call to the <xref:System.Enum.ToString%2A> method on the <xref:System.DayOfWeek> value returned by the property.</span></span> <span data-ttu-id="de3aa-140">Ancak, aşağıdaki örnekte gösterildiği gibi bu teknik geçerli kültür için yerelleştirilen hafta içi adı üretmez.</span><span class="sxs-lookup"><span data-stu-id="de3aa-140">However, this technique does not produce a localized weekday name for the current culture, as the following example illustrates.</span></span>  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="de3aa-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de3aa-141">See Also</span></span>  
 [<span data-ttu-id="de3aa-142">Biçimlendirme İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="de3aa-142">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="de3aa-143">Standart Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="de3aa-143">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [<span data-ttu-id="de3aa-144">Özel Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="de3aa-144">Custom Date and Time Format Strings</span></span>](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)

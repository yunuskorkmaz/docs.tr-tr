---
title: Date Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: 32bd0912b0bae3340cffed010fc67431d0efb376
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45515996"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="fcbf1-102">Date Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcbf1-102">Date Data Type (Visual Basic)</span></span>
<span data-ttu-id="fcbf1-103">IEEE 64-bit (8 bayt) 12:00: 00'da (gece yarısı), 1 Ocak 0001-31 Aralık 9999 yılın yılın arasında değişen tarihleri ve saatleri temsil eden bir değer PM 11:59:59.9999999 tutar.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="fcbf1-104">Her artış, Gregoryen takvimindeki 1 yılının 1 Ocak başından beri geçen 100 nanosaniyelik geçen süreyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="fcbf1-105">En yüksek değer 100 nanosaniyelik 10000 yılın 1 Ocak, başlamadan önce temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcbf1-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcbf1-106">Remarks</span></span>  
 <span data-ttu-id="fcbf1-107">Kullanım `Date` tarih değerleri, saat değerleri veya tarih ve saat değerlerini içeren bir veri türü.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>  
  
 <span data-ttu-id="fcbf1-108">Varsayılan değer olan `Date` 0:00:00 (gece yarısı) 1 Ocak 0001.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>  
  
 <span data-ttu-id="fcbf1-109">Geçerli tarih ve saat alabilirsiniz <xref:Microsoft.VisualBasic.DateAndTime> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="fcbf1-110">Biçim gereksinimlerini</span><span class="sxs-lookup"><span data-stu-id="fcbf1-110">Format Requirements</span></span>  
 <span data-ttu-id="fcbf1-111">İçine almalısınız bir `Date` sayı işaretleri içindeki sabit değeri (`# #`).</span><span class="sxs-lookup"><span data-stu-id="fcbf1-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="fcbf1-112">Örneğin a/yyyy biçiminde tarih değeri belirtmelisiniz `#5/31/1993#`, ya da yyyy-aa-gg, örneğin `#1993-5-31#`.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="fcbf1-113">Yılın ilk belirtirken, eğik çizgi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="fcbf1-114">Bu gereksinim, bölgeniz ve bilgisayarınızın tarih ve saat biçimi ayarlarını bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>  
  
 <span data-ttu-id="fcbf1-115">Bu kısıtlamanın nedeni anlamı kodunuzu, uygulamanızın çalıştığı yerel ayara bağlı olarak hiçbir zaman değiştirmelisiniz ' dir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="fcbf1-116">Sabit kodlu varsayalım bir `Date` , değişmez değer `#3/4/1998#` ve ortalama 4 Mart 1998'de istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="fcbf1-117">İstediğiniz gibi aa/gg/yyyy kullanan bir yerel ayarda 3/4/1998'de derler.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="fcbf1-118">Ancak birçok ülkede uygulamanızı dağıtabilmeniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-118">But suppose you deploy your application in many countries.</span></span> <span data-ttu-id="fcbf1-119">Gg/aa/yyyy kullanan bir yerel ayarında, sabit kodlanmış değişmez değeri 3 Nisan 1998 derlenir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="fcbf1-120">Değişmez değer yyyy/aa/gg kullanan bir yerel ayarında geçersiz olur (Nisan 1998 ' 0003) ve bir derleyici hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>  
  
## <a name="workarounds"></a><span data-ttu-id="fcbf1-121">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="fcbf1-121">Workarounds</span></span>  
 <span data-ttu-id="fcbf1-122">Dönüştürülecek bir `Date` bölgeniz biçimi veya özel bir biçim için değişmez değerin değişmez değer sağlamanız <xref:Microsoft.VisualBasic.Strings.Format%2A> işlevi, bir ya da önceden tanımlı veya kullanıcı tanımlı tarih biçimini belirleme.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="fcbf1-123">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-123">The following example demonstrates this.</span></span>  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 <span data-ttu-id="fcbf1-124">Alternatif olarak, aşırı yüklü oluşturucular birini kullanabilirsiniz <xref:System.DateTime> bir tarih ve saat değerini derlemek için yapısı.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="fcbf1-125">Aşağıdaki örnek, 12:14 öğleden sonra 31 Mayıs 1993 temsil etmek için bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a><span data-ttu-id="fcbf1-126">Saat biçimi</span><span class="sxs-lookup"><span data-stu-id="fcbf1-126">Hour Format</span></span>  
 <span data-ttu-id="fcbf1-127">Örneğin 12 saat veya 24 saat biçiminde saat değeri belirtebilirsiniz `#1:15:30 PM#` veya `#13:15:30#`.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="fcbf1-128">Ancak, dakika veya saniye belirtmezseniz, AM veya PM belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>  
  
## <a name="date-and-time-defaults"></a><span data-ttu-id="fcbf1-129">Tarih ve saat Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="fcbf1-129">Date and Time Defaults</span></span>  
 <span data-ttu-id="fcbf1-130">Bir tarihi bir tarih/saat değişmez değer eklemezseniz, Visual Basic değerinin tarih bölümünü 1 Ocak, 0001 ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="fcbf1-131">Bir süre içinde bir tarih değişmez eklemezseniz, Visual Basic değerinin saat bölümünü diğer bir deyişle, gece yarısı güne başlamak için ayarlar. (0: 00:00).</span><span class="sxs-lookup"><span data-stu-id="fcbf1-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="fcbf1-132">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="fcbf1-132">Type Conversions</span></span>  
 <span data-ttu-id="fcbf1-133">Dönüştürürseniz, bir `Date` değerini `String` türü, Visual Basic çalışma zamanı tarafından belirtilen kısa tarih biçimini göre tarih oluşturur ve tarafından belirlenen süre saat biçimini (12 saat veya 24 saat) göre işler çalışma zamanı yerel ayar.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="fcbf1-134">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="fcbf1-134">Programming Tips</span></span>  
  
-   <span data-ttu-id="fcbf1-135">**Birlikte çalışabilirlik değerlendirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="fcbf1-135">**Interop Considerations.**</span></span> <span data-ttu-id="fcbf1-136">Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, tarih/saat türleri diğer ortamlarda unutmayın Visual Basic ile uyumlu değil `Date` türü.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="fcbf1-137">Bir tarih/saat değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `Double` yerine `Date` , yeni bir Visual Basic kod ve dönüştürme yöntemleri kullanın <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> ve <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="fcbf1-138">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="fcbf1-138">**Type Characters.**</span></span> <span data-ttu-id="fcbf1-139">`Date` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="fcbf1-140">Ancak derleyici değişmez değerleri sayı işaretleri alınmış işler (`# #`) olarak `Date`.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>  
  
-   <span data-ttu-id="fcbf1-141">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="fcbf1-141">**Framework Type.**</span></span> <span data-ttu-id="fcbf1-142">.NET Framework içinde karşılık gelen türü <xref:System.DateTime?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcbf1-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcbf1-143">Example</span></span>  
 <span data-ttu-id="fcbf1-144">Bir değişken veya sabiti `Date` tarih ve saat veri türü tutar.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="fcbf1-145">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-145">The following example illustrates this.</span></span>  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcbf1-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcbf1-146">See Also</span></span>  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [<span data-ttu-id="fcbf1-147">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="fcbf1-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="fcbf1-148">Standart Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="fcbf1-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [<span data-ttu-id="fcbf1-149">Özel Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="fcbf1-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [<span data-ttu-id="fcbf1-150">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fcbf1-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="fcbf1-151">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="fcbf1-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="fcbf1-152">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="fcbf1-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

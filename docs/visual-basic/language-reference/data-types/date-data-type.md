---
title: Date Veri Türü
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
ms.openlocfilehash: 972df72874753a0f1213f3a4942468c59e3913ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344022"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="65d94-102">Date Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65d94-102">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="65d94-103">0001 yılının 1 Ocak ayının 9999 31 Aralık 12:00:00 'a kadar (gece yarısı), 11:59:59.9999999 PM arasında değişen tarihleri temsil eden IEEE 64-bit (8 baytlık) değerleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="65d94-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="65d94-104">Her artış, Gregoryen takvimdeki 1 Ocak yılın başından itibaren geçen sürenin 100 nanosaniye süresini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="65d94-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="65d94-105">Maksimum değer 100, 1 Ocak 10000 yılın başından önce nanosaniye 'yi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="65d94-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="65d94-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65d94-106">Remarks</span></span>

<span data-ttu-id="65d94-107">Tarih değerlerini, zaman değerlerini veya tarih ve saat değerlerini içermesi için `Date` veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="65d94-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="65d94-108">`Date` varsayılan değeri 1 Ocak 0001 tarihinde 0:00:00 (gece yarısı) değeridir.</span><span class="sxs-lookup"><span data-stu-id="65d94-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="65d94-109"><xref:Microsoft.VisualBasic.DateAndTime> sınıfından geçerli tarih ve saati alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65d94-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="65d94-110">Biçim gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="65d94-110">Format Requirements</span></span>

<span data-ttu-id="65d94-111">`Date` değişmez değeri sayı işaretleri (`# #`) içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="65d94-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="65d94-112">Tarih değerini M/d/yyyy biçiminde belirtmeniz gerekir, örneğin `#5/31/1993#`veya yyyy-aa-gg, örneğin `#1993-5-31#`.</span><span class="sxs-lookup"><span data-stu-id="65d94-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="65d94-113">Önce yılı belirtirken eğik çizgi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65d94-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="65d94-114">Bu gereksinim, yerel ayarınızı ve bilgisayarınızın tarih ve saat biçimi ayarlarını birbirinden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="65d94-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="65d94-115">Bu kısıtlamanın nedeni, kodunuzun anlamını uygulamanızın çalıştırıldığı yerel ayara bağlı olarak asla değiştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="65d94-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="65d94-116">`Date` bir `#3/4/1998#` sabit kodladığınızı ve 4 Mart 1998 ' den itibaren olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="65d94-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="65d94-117">Aa/gg/yyyy kullanan bir yerel ayarda, 3/4/1998 istediğiniz şekilde derlenir.</span><span class="sxs-lookup"><span data-stu-id="65d94-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="65d94-118">Ancak uygulamanızı birçok ülkede/bölgede dağıttığınız varsayın.</span><span class="sxs-lookup"><span data-stu-id="65d94-118">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="65d94-119">Gg/aa/yyyy kullanan bir yerel ayarda, sabit kodlanmış sabit değer 3 Nisan 1998 ' e derlenir.</span><span class="sxs-lookup"><span data-stu-id="65d94-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="65d94-120">Yyyy/aa/gg kullanan bir yerel ayarda, değişmez değer geçersiz (1998 Nisan, 0003) ve bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="65d94-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="65d94-121">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="65d94-121">Workarounds</span></span>

<span data-ttu-id="65d94-122">Bir `Date` sabit değerini yerel ayarınızdaki biçime veya özel bir biçime dönüştürmek için, önceden tanımlanmış veya Kullanıcı tanımlı bir tarih biçimi belirterek, <xref:Microsoft.VisualBasic.Strings.Format%2A> işlevine değişmez değer sağlayın.</span><span class="sxs-lookup"><span data-stu-id="65d94-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="65d94-123">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="65d94-123">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="65d94-124">Alternatif olarak, bir tarih ve saat değerini birleştirmek için <xref:System.DateTime> yapısının aşırı yüklenmiş oluşturucularından birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65d94-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="65d94-125">Aşağıdaki örnek, öğleden sonra 31 Mayıs 12:14 1993 ' i temsil eden bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65d94-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="65d94-126">Saat biçimi</span><span class="sxs-lookup"><span data-stu-id="65d94-126">Hour Format</span></span>

<span data-ttu-id="65d94-127">Saat değerini 12 saat veya 24 saat biçiminde belirtebilirsiniz, örneğin `#1:15:30 PM#` veya `#13:15:30#`.</span><span class="sxs-lookup"><span data-stu-id="65d94-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="65d94-128">Ancak, dakikalar veya saniyeler belirtmezseniz, har veya PM belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="65d94-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="65d94-129">Tarih ve saat Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="65d94-129">Date and Time Defaults</span></span>

<span data-ttu-id="65d94-130">Tarih/saat değişmez değerinde bir tarih eklemezseniz, Visual Basic değerin tarih bölümünü 1 Ocak 0001 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="65d94-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="65d94-131">Tarih/saat değişmez değerinde bir saat eklemezseniz, Visual Basic değerin saat bölümünü günün başına, yani gece yarısı (0:00:00) olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="65d94-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="65d94-132">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="65d94-132">Type Conversions</span></span>

<span data-ttu-id="65d94-133">Bir `Date` değerini `String` türüne dönüştürürseniz Visual Basic, tarihi çalışma zamanı yerel ayarı tarafından belirtilen kısa tarih biçimine göre işler ve saati çalışma zamanı yerel ayarı tarafından belirtilen saat biçimine (12 saat veya 24 saat) göre işler.</span><span class="sxs-lookup"><span data-stu-id="65d94-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="65d94-134">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="65d94-134">Programming Tips</span></span>

- <span data-ttu-id="65d94-135">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="65d94-135">**Interop Considerations.**</span></span> <span data-ttu-id="65d94-136">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, diğer ortamlardaki tarih/saat türlerinin Visual Basic `Date` türüyle uyumlu olmadığını aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="65d94-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="65d94-137">Böyle bir bileşene bir tarih/saat bağımsız değişkeni geçirdiğinizden, bunu yeni Visual Basic kodunuzda `Date` yerine `Double` olarak bildirin ve <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> ve <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>dönüştürme yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="65d94-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="65d94-138">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="65d94-138">**Type Characters.**</span></span> <span data-ttu-id="65d94-139">`Date` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="65d94-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="65d94-140">Ancak derleyici, sayıları sayı işaretleri (`# #`) içinde `Date`olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="65d94-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="65d94-141">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="65d94-141">**Framework Type.**</span></span> <span data-ttu-id="65d94-142">.NET Framework karşılık gelen tür <xref:System.DateTime?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="65d94-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="65d94-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="65d94-143">Example</span></span>

<span data-ttu-id="65d94-144">`Date` veri türünün bir değişkeni veya sabiti hem tarihi hem de saati tutar.</span><span class="sxs-lookup"><span data-stu-id="65d94-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="65d94-145">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="65d94-145">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="65d94-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65d94-146">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="65d94-147">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="65d94-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="65d94-148">Standart Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="65d94-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="65d94-149">Özel Tarih ve Saat Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="65d94-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="65d94-150">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="65d94-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="65d94-151">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="65d94-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="65d94-152">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="65d94-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

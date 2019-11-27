---
title: Dize İşlevleri
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 2608159e28ee63a0fdb10c82054fd65efe79ac62
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349973"
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="3b6ef-102">Dize İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b6ef-102">String Functions (Visual Basic)</span></span>

<span data-ttu-id="3b6ef-103">Aşağıdaki tabloda, <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> sınıfında dizeleri aramak ve işlemek için Visual Basic sağladığı işlevler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-103">The following table lists the functions that Visual Basic provides in the <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> class to search and manipulate strings.</span></span> <span data-ttu-id="3b6ef-104">Visual Basic iç işlevler olarak kabul edilebilir. diğer bir deyişle, örneklerin gösterdiği gibi, bunları bir sınıfın açık üyeleri olarak çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-104">They can be regarded as Visual Basic intrinsic functions; that is, you do not have to call them as explicit members of a class, as the examples show.</span></span> <span data-ttu-id="3b6ef-105">Ek yöntemler ve bazı durumlarda tamamlayıcı Yöntemler <xref:System.String?displayProperty=nameWithType> sınıfında mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-105">Additional methods, and in some cases complementary methods, are available in the <xref:System.String?displayProperty=nameWithType> class.</span></span>

|<span data-ttu-id="3b6ef-106">.NET Framework yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b6ef-106">.NET Framework method</span></span>|<span data-ttu-id="3b6ef-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b6ef-107">Description</span></span>|
|---------------------------|-----------------|
|<span data-ttu-id="3b6ef-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="3b6ef-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="3b6ef-109">Bir karaktere karşılık gelen karakter kodunu temsil eden bir `Integer` değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-109">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|
|<span data-ttu-id="3b6ef-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="3b6ef-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="3b6ef-111">Belirtilen karakter koduyla ilişkili karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-111">Returns the character associated with the specified character code.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="3b6ef-112">Belirtilen filtre ölçütlerine göre `String` dizisinin bir alt kümesini içeren sıfır tabanlı bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-112">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="3b6ef-113">Biçim `String` ifadesinde bulunan yönergelere göre biçimlendirilen bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-113">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="3b6ef-114">Sistem denetim masasında tanımlanan para birimi simgesini kullanarak para birimi değeri olarak biçimlendirilen bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-114">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="3b6ef-115">Tarih/saat değerini gösteren bir dize ifadesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-115">Returns a string expression representing a date/time value.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="3b6ef-116">Sayı olarak biçimlendirilen bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-116">Returns an expression formatted as a number.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="3b6ef-117">% Karakteriyle bir yüzde (yani, 100 ile çarpılmış) olarak biçimlendirilen bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-117">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="3b6ef-118">Bir dizenin diğeri içindeki ilk örneğinin başlangıç konumunu belirten bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-118">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="3b6ef-119">Dizenin sağ tarafından başlayarak bir dizenin diğeri içindeki ilk oluşumunun konumunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-119">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="3b6ef-120">Bir dizide bulunan bir dizi alt dizenin birleştirilmesiyle oluşturulan bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-120">Returns a string created by joining a number of substrings contained in an array.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="3b6ef-121">Küçük harfe dönüştürülmüş bir dize veya karakter döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-121">Returns a string or character converted to lowercase.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="3b6ef-122">Dizenin sol tarafından belirtilen sayıda karakter içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-122">Returns a string containing a specified number of characters from the left side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="3b6ef-123">Dizedeki karakter sayısını içeren bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-123">Returns an integer that contains the number of characters in a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="3b6ef-124">Belirtilen uzunluğa ayarlanmış belirtilen dizeyi içeren sola hizalanmış bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-124">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="3b6ef-125">Belirtilen dizenin başında boşluk olmayan bir kopyasını içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-125">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="3b6ef-126">Bir dizeden belirtilen sayıda karakter içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-126">Returns a string containing a specified number of characters from a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="3b6ef-127">Belirtilen bir alt dizenin belirtilen sayıda başka bir alt dizeyle değiştirildiği bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-127">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="3b6ef-128">Dizenin sağ tarafından belirtilen sayıda karakter içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-128">Returns a string containing a specified number of characters from the right side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="3b6ef-129">Belirtilen uzunluğa ayarlanmış belirtilen dizeyi içeren sağa hizalanmış bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-129">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="3b6ef-130">Belirtilen dizenin sonunda boşluk olmayan bir kopyasını içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-130">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="3b6ef-131">Belirtilen sayıda boşluktan oluşan bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-131">Returns a string consisting of the specified number of spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="3b6ef-132">Belirtilen sayıda alt dize içeren sıfır tabanlı, tek boyutlu bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-132">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="3b6ef-133">Dize karşılaştırmasının sonucuna bağlı olarak-1, 0 veya 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-133">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="3b6ef-134">Belirtilen şekilde dönüştürülmüş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-134">Returns a string converted as specified.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="3b6ef-135">Belirtilen karakterin belirtilen sayıda yinelenmesinden oluşan bir dize veya nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-135">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="3b6ef-136">Belirtilen dizenin karakter sırasının tersine döndürüldüğü bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-136">Returns a string in which the character order of a specified string is reversed.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="3b6ef-137">Belirtilen dizenin başında veya sonunda boşluk olmayan bir kopyasını içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-137">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="3b6ef-138">Belirtilen dizeyi büyük harfe dönüştürülmüş olarak içeren bir dize veya karakter döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-138">Returns a string or character containing the specified string converted to uppercase.</span></span>|

<span data-ttu-id="3b6ef-139">Dizelerin, sisteminizin yerel ayarında (`Text`) veya karakterlerin iç ikili gösterimlerine (`Binary`) göre belirlenen büyük/küçük harfe duyarsız metin sıralama düzeni kullanarak karşılaştırıldığını ayarlamak için [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-139">You can use the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="3b6ef-140">Varsayılan metin karşılaştırma yöntemi `Binary`.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-140">The default text comparison method is `Binary`.</span></span>

## <a name="example-ucase"></a><span data-ttu-id="3b6ef-141">Örnek: UCase</span><span class="sxs-lookup"><span data-stu-id="3b6ef-141">Example: UCase</span></span>

<span data-ttu-id="3b6ef-142">Bu örnek, bir dizenin büyük bir sürümünü döndürmek için `UCase` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-142">This example uses the `UCase` function to return an uppercase version of a string.</span></span>
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a><span data-ttu-id="3b6ef-143">Örnek: LTrim</span><span class="sxs-lookup"><span data-stu-id="3b6ef-143">Example: LTrim</span></span>

<span data-ttu-id="3b6ef-144">Bu örnek, bir dize değişkeninden sondaki boşlukları atmak için `LTrim` işlevini, baştaki boşlukları ve `RTrim` işlevini eklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-144">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="3b6ef-145">Her iki boşluk türünü de atmak için `Trim` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-145">It uses the `Trim` function to strip both types of spaces.</span></span>

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a><span data-ttu-id="3b6ef-146">Örnek: PARÇAAL</span><span class="sxs-lookup"><span data-stu-id="3b6ef-146">Example: Mid</span></span>

<span data-ttu-id="3b6ef-147">Bu örnek, bir dizeden belirtilen sayıda karakteri döndürmek için `Mid` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-147">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a><span data-ttu-id="3b6ef-148">Örnek: Len</span><span class="sxs-lookup"><span data-stu-id="3b6ef-148">Example: Len</span></span>

<span data-ttu-id="3b6ef-149">Bu örnek, bir dizedeki karakter sayısını döndürmek için `Len` kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-149">This example uses `Len` to return the number of characters in a string.</span></span>

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a><span data-ttu-id="3b6ef-150">Örnek: InStr</span><span class="sxs-lookup"><span data-stu-id="3b6ef-150">Example: InStr</span></span>

<span data-ttu-id="3b6ef-151">Bu örnek, bir dizenin bir diğeri içindeki ilk oluşumunun konumunu döndürmek için `InStr` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-151">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a><span data-ttu-id="3b6ef-152">Örnek: biçim</span><span class="sxs-lookup"><span data-stu-id="3b6ef-152">Example: Format</span></span>

<span data-ttu-id="3b6ef-153">Bu örnek, `String` biçimlerini ve Kullanıcı tanımlı biçimleri kullanarak değerleri biçimlendirmek için `Format` işlevinin çeşitli kullanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-153">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="3b6ef-154">Tarih ayırıcısı (`/`), zaman ayırıcısı (`:`) ve ı/PM göstergeleri (`t` ve `tt`) için, sisteminiz tarafından görünen gerçek biçimli çıktı, kodun kullandığı yerel ayar ayarlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-154">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="3b6ef-155">Geliştirme ortamında saat ve tarihler görüntülendiğinde, kod yerel ayarının kısa saat biçimi ve kısa tarih biçimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-155">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>

> [!NOTE]
> <span data-ttu-id="3b6ef-156">24 saatlik bir saat kullanan yerel ayarlarda, ı/PM göstergeleri (`t` ve `tt`) hiçbir şey görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-156">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a><span data-ttu-id="3b6ef-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b6ef-157">See also</span></span>

- [<span data-ttu-id="3b6ef-158">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="3b6ef-158">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="3b6ef-159">Visual Basic Çalışma Süresi Kitaplık Üyeleri</span><span class="sxs-lookup"><span data-stu-id="3b6ef-159">Visual Basic Runtime Library Members</span></span>](../../../visual-basic/language-reference/runtime-library-members.md)
- [<span data-ttu-id="3b6ef-160">Dize Düzenleme Özeti</span><span class="sxs-lookup"><span data-stu-id="3b6ef-160">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
- [<span data-ttu-id="3b6ef-161">System. String sınıf yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3b6ef-161">System.String class methods</span></span>](xref:System.String#methods)

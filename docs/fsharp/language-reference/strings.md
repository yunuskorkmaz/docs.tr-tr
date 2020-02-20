---
title: Dizeler
description: F# ' Dize ' türünün Unicode karakter dizisi olarak sabit metni nasıl temsil ettiğini öğrenin.
ms.date: 07/05/2019
ms.openlocfilehash: 002de464d09a49b6161608db6e46c619369f5ceb
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452824"
---
# <a name="strings"></a><span data-ttu-id="46352-103">Dizeler</span><span class="sxs-lookup"><span data-stu-id="46352-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="46352-104">Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürür.</span><span class="sxs-lookup"><span data-stu-id="46352-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="46352-105">Docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="46352-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="46352-106">`string` türü, Unicode karakter dizisi olarak sabit metni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46352-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="46352-107">`string`, .NET Framework `System.String` için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="46352-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="46352-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46352-108">Remarks</span></span>

<span data-ttu-id="46352-109">Dize sabit değerleri tırnak işareti (") karakteriyle sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="46352-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="46352-110">Ters eğik çizgi karakteri (\\) belirli özel karakterleri kodlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46352-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="46352-111">Ters eğik çizgi ve sonraki karakter birlikte *kaçış sırası*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="46352-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="46352-112">F# Dize sabit değerlerinde desteklenen kaçış dizileri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46352-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="46352-113">Karakter</span><span class="sxs-lookup"><span data-stu-id="46352-113">Character</span></span>|<span data-ttu-id="46352-114">Kaçış sırası</span><span class="sxs-lookup"><span data-stu-id="46352-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="46352-115">Uyarı</span><span class="sxs-lookup"><span data-stu-id="46352-115">Alert</span></span>|`\a`|
|<span data-ttu-id="46352-116">Geri Al tuşu</span><span class="sxs-lookup"><span data-stu-id="46352-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="46352-117">Form akışı</span><span class="sxs-lookup"><span data-stu-id="46352-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="46352-118">Metninde</span><span class="sxs-lookup"><span data-stu-id="46352-118">Newline</span></span>|`\n`|
|<span data-ttu-id="46352-119">Satır başı</span><span class="sxs-lookup"><span data-stu-id="46352-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="46352-120">Tab</span><span class="sxs-lookup"><span data-stu-id="46352-120">Tab</span></span>|`\t`|
|<span data-ttu-id="46352-121">Dikey sekme</span><span class="sxs-lookup"><span data-stu-id="46352-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="46352-122">Ters eğik çizgi</span><span class="sxs-lookup"><span data-stu-id="46352-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="46352-123">Tırnak işareti</span><span class="sxs-lookup"><span data-stu-id="46352-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="46352-124">Kesme işareti</span><span class="sxs-lookup"><span data-stu-id="46352-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="46352-125">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="46352-125">Unicode character</span></span>|<span data-ttu-id="46352-126">`\DDD` (`D` ondalık basamağı gösterir; 000-255 aralığı; Örneğin, `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="46352-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="46352-127">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="46352-127">Unicode character</span></span>|<span data-ttu-id="46352-128">`\xHH` (`H` on altılı bir basamak, 00-FF aralığı; Örneğin, `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="46352-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="46352-129">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="46352-129">Unicode character</span></span>|<span data-ttu-id="46352-130">`\uHHHH` (UTF-16) (`H` onaltılık bir basamak, 0000-FFFF) aralığı;  Örneğin, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="46352-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="46352-131">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="46352-131">Unicode character</span></span>|<span data-ttu-id="46352-132">`\U00HHHHHH` (UTF-32) (`H` onaltılık bir basamak gösterir; 000000 yazın-10FFFF) aralığı  Örneğin, `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="46352-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="46352-133">`\DDD` kaçış sırası, diğer dillerin çoğunda, sekizli gösterimde değil ondalık gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="46352-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="46352-134">Bu nedenle, `8` ve `9` basamakları geçerlidir ve bir `\032` dizisi bir boşluk (U + 0020) temsil ederken, sekizlik gösterimde aynı kod noktası `\040`olur.</span><span class="sxs-lookup"><span data-stu-id="46352-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="46352-135">0-255 (0xFF) aralığıyla sınırlandırılmakta, `\DDD` ve `\x` kaçış dizileri, ilk 256 Unicode kod noktalarıyla eşleştiğinden, etkin şekilde [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) karakter kümesidir.</span><span class="sxs-lookup"><span data-stu-id="46352-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="46352-136">Tam dizeler</span><span class="sxs-lookup"><span data-stu-id="46352-136">Verbatim Strings</span></span>

<span data-ttu-id="46352-137">Önünde @ sembolü varsa, değişmez değer tam bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="46352-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="46352-138">Bu, iki tırnak işareti karakterinin tek tırnak işareti karakteri olarak yorumlanmasının dışında, tüm kaçış dizileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="46352-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="46352-139">Üçlü alıntılanmış dizeler</span><span class="sxs-lookup"><span data-stu-id="46352-139">Triple Quoted Strings</span></span>

<span data-ttu-id="46352-140">Ayrıca, bir dize, Üçlü tırnak içine alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="46352-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="46352-141">Bu durumda, çift tırnak işareti karakterleri de dahil olmak üzere tüm kaçış dizileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="46352-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="46352-142">Katıştırılmış bir alıntı dize içeren bir dize belirtmek için, tam bir dize veya Üçlü tırnak işareti kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46352-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="46352-143">Tam bir dize kullanırsanız, tek tırnak işareti karakterini göstermek için iki tırnak işareti karakteri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46352-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="46352-144">Üçlü olarak tırnak içine alınmış bir dize kullanırsanız, tek tırnak işareti karakterlerini dizenin sonu olarak ayrıştırılmaksızın kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46352-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="46352-145">Bu teknik, ekli tırnak işaretleri içeren XML veya diğer yapılarla çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="46352-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="46352-146">Kod içinde, satır sonları içeren dizeler kabul edilir ve satır sonları satır sonundan önce son karakter olan bir ters eğik çizgi karakteri olmayan bir şekilde newlines olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="46352-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="46352-147">Ters eğik çizgi karakteri kullanıldığında sonraki satırdaki baştaki boşluk yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="46352-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="46352-148">Aşağıdaki kod, değer `"abc\ndef"` olan bir dize `str1` ve değer `"abcdef"`olan bir dize `str2` üretir.</span><span class="sxs-lookup"><span data-stu-id="46352-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="46352-149">Dize dizinleme ve dilimleme</span><span class="sxs-lookup"><span data-stu-id="46352-149">String Indexing and Slicing</span></span>

<span data-ttu-id="46352-150">Bir dizedeki ayrı karakterlere, aşağıdaki gibi dizi benzeri sözdizimini kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46352-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="46352-151">Çıktı `b`.</span><span class="sxs-lookup"><span data-stu-id="46352-151">The output is `b`.</span></span>

<span data-ttu-id="46352-152">Ya da aşağıdaki kodda gösterildiği gibi, dizi dilimi söz dizimini kullanarak alt dizeleri de ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46352-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="46352-153">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="46352-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="46352-154">ASCII dizelerini işaretsiz bayt dizileri ile temsil edebilirsiniz, `byte[]`yazın.</span><span class="sxs-lookup"><span data-stu-id="46352-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="46352-155">Bir dize sabit değerinin bir ASCII dizesi olduğunu göstermek için sonek `B` eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="46352-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="46352-156">Bayt dizileri ile kullanılan ASCII dize sabit değerleri, Unicode kaçış dizileri hariç, Unicode dizeleriyle aynı kaçış dizilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="46352-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="46352-157">Dize İşleçleri</span><span class="sxs-lookup"><span data-stu-id="46352-157">String Operators</span></span>

<span data-ttu-id="46352-158">Dizeleri birleştirmek için iki yol vardır: `+` işlecini veya `^` işlecini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="46352-158">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="46352-159">`+` işleci, .NET Framework dize işleme özellikleriyle uyumluluğu korur.</span><span class="sxs-lookup"><span data-stu-id="46352-159">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="46352-160">Aşağıdaki örnekte dize birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46352-160">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="46352-161">String sınıfı</span><span class="sxs-lookup"><span data-stu-id="46352-161">String Class</span></span>

<span data-ttu-id="46352-162">İçindeki F# dize türü aslında bir .NET Framework `System.String` türü olduğundan, tüm `System.String` üyeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46352-162">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="46352-163">Bu, dizeleri birleştirmek için kullanılan `+` işlecini, `Length` özelliğini ve dizeyi bir Unicode karakter dizisi olarak döndüren `Chars` özelliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="46352-163">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="46352-164">Dizeler hakkında daha fazla bilgi için bkz. `System.String`.</span><span class="sxs-lookup"><span data-stu-id="46352-164">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="46352-165">`System.String``Chars` özelliğini kullanarak, aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dizedeki ayrı karakterlere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46352-165">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="46352-166">Dize modülü</span><span class="sxs-lookup"><span data-stu-id="46352-166">String Module</span></span>

<span data-ttu-id="46352-167">Dize işleme için ek işlevler, `FSharp.Core` ad alanındaki `String` modülüne dahildir.</span><span class="sxs-lookup"><span data-stu-id="46352-167">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="46352-168">Daha fazla bilgi için bkz. [Core. String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="46352-168">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="46352-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46352-169">See also</span></span>

- [<span data-ttu-id="46352-170">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="46352-170">F# Language Reference</span></span>](index.md)

---
title: Dizeler
description: F# 'string' türünün değişmez metni Unicode karakter dizisi olarak nasıl temsil edeni öğrenin.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739563"
---
# <a name="strings"></a><span data-ttu-id="15239-103">Dizeler</span><span class="sxs-lookup"><span data-stu-id="15239-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="15239-104">Bu makaledeki API başvuru bağlantıları sizi MSDN'ye götürür.</span><span class="sxs-lookup"><span data-stu-id="15239-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="15239-105">docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="15239-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="15239-106">Tür, `string` değişmez metni Unicode karakter dizisi olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="15239-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="15239-107">`string`.NET Framework'de bir `System.String` diğer addır.</span><span class="sxs-lookup"><span data-stu-id="15239-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="15239-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15239-108">Remarks</span></span>

<span data-ttu-id="15239-109">String literals tırnak işareti (") karakteri ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="15239-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="15239-110">Ters eğik \\ çizgi karakteri ( ) belirli özel karakterleri kodlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15239-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="15239-111">Backslash ve sonraki karakter birlikte bir *kaçış dizisi*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="15239-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="15239-112">F# string literals desteklenen kaçış dizileri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="15239-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="15239-113">Karakter</span><span class="sxs-lookup"><span data-stu-id="15239-113">Character</span></span>|<span data-ttu-id="15239-114">Kaçış sırası</span><span class="sxs-lookup"><span data-stu-id="15239-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="15239-115">Uyarı</span><span class="sxs-lookup"><span data-stu-id="15239-115">Alert</span></span>|`\a`|
|<span data-ttu-id="15239-116">Geri Al tuşu</span><span class="sxs-lookup"><span data-stu-id="15239-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="15239-117">Form akışı</span><span class="sxs-lookup"><span data-stu-id="15239-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="15239-118">Newline</span><span class="sxs-lookup"><span data-stu-id="15239-118">Newline</span></span>|`\n`|
|<span data-ttu-id="15239-119">Satır başı</span><span class="sxs-lookup"><span data-stu-id="15239-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="15239-120">Tab</span><span class="sxs-lookup"><span data-stu-id="15239-120">Tab</span></span>|`\t`|
|<span data-ttu-id="15239-121">Dikey sekme</span><span class="sxs-lookup"><span data-stu-id="15239-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="15239-122">Ters eğik çizgi</span><span class="sxs-lookup"><span data-stu-id="15239-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="15239-123">Teklif işareti</span><span class="sxs-lookup"><span data-stu-id="15239-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="15239-124">Kesme işareti</span><span class="sxs-lookup"><span data-stu-id="15239-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="15239-125">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="15239-125">Unicode character</span></span>|<span data-ttu-id="15239-126">`\DDD`(ondalık basamak gösterir; `D` 000 - 255 aralığı; `\231` örneğin, = "ç")</span><span class="sxs-lookup"><span data-stu-id="15239-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="15239-127">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="15239-127">Unicode character</span></span>|<span data-ttu-id="15239-128">`\xHH`(hexadecimal `H` basamak; 00 - FF aralığı; örneğin `\xE7` , = "ç")</span><span class="sxs-lookup"><span data-stu-id="15239-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="15239-129">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="15239-129">Unicode character</span></span>|<span data-ttu-id="15239-130">`\uHHHH`(UTF-16) (burada `H` bir hexadecimal basamak gösterir; 0000 aralığı - FFFF;  örneğin, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="15239-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="15239-131">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="15239-131">Unicode character</span></span>|<span data-ttu-id="15239-132">`\U00HHHHHH`(UTF-32) (hexadecimal `H` basamak gösterir; 000000 - 10FFFF aralığı;  örneğin, `\U0001F47D` =👽" ")</span><span class="sxs-lookup"><span data-stu-id="15239-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="15239-133">Kaçış `\DDD` sırası ondalık gösterimdir, diğer dillerdeki gibi sekizli gösterim değildir.</span><span class="sxs-lookup"><span data-stu-id="15239-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="15239-134">Bu nedenle, `8` `9` basamak ve geçerli ve `\032` bir boşluk (U+0020) temsil eder, octal gösterimaynı `\040`kod noktası ise .</span><span class="sxs-lookup"><span data-stu-id="15239-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="15239-135">0 - 255 (0xFF) aralığıyla sınırlandırılan `\x` ve `\DDD` kaçış sekansları, ilk 256 Unicode kod puanıyla eşleştiğinden etkili bir şekilde [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) karakter kümesidir.</span><span class="sxs-lookup"><span data-stu-id="15239-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="15239-136">Verbatim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="15239-136">Verbatim Strings</span></span>

<span data-ttu-id="15239-137">@ sembolünden önce yse, literal harfi harfi harfine dizedir.</span><span class="sxs-lookup"><span data-stu-id="15239-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="15239-138">Bu, iki tırnak işareti karakterinin bir tırnak işareti karakteri olarak yorumlanması dışında, herhangi bir kaçış dizisinin yoksayılması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="15239-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="15239-139">Üçlü Tırnaklı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="15239-139">Triple Quoted Strings</span></span>

<span data-ttu-id="15239-140">Ayrıca, bir dize üçlü tırnak ile eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="15239-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="15239-141">Bu durumda, çift tırnak işareti karakterleri de dahil olmak üzere tüm kaçış dizileri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="15239-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="15239-142">Katıştılı bir alıntı dizesini içeren bir dize belirtmek için, bir harfi harfini veya üç tırnaklı dizeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15239-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="15239-143">Bir harfi harfini dize kullanıyorsanız, tek bir tırnak işareti karakterini belirtmek için iki tırnak işareti karakteri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="15239-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="15239-144">Üç tırnaklı bir dize kullanıyorsanız, tek tırnak işareti karakterlerini dize sonu olarak ayrıştıolmadan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15239-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="15239-145">Bu teknik, XML veya gömülü tırnak işaretleri içeren diğer yapılarla çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="15239-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="15239-146">Kodda, satır sonları olan dizeleri kabul edilir ve satır sonu, satır sonu kesmeden önceki son karakter olmadığı sürece, tam anlamıyla yeni satırlar olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="15239-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="15239-147">Ters eğik çizgi karakteri kullanıldığında bir sonraki satırda satırda satır satır beyaz boşluk yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="15239-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="15239-148">`str1` Aşağıdaki kod değeri `"abc\ndef"` olan bir dize `str2` ve `"abcdef"`değeri olan bir dize üretir.</span><span class="sxs-lookup"><span data-stu-id="15239-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="15239-149">Dize Dizini Oluşturma ve Dilimleme</span><span class="sxs-lookup"><span data-stu-id="15239-149">String Indexing and Slicing</span></span>

<span data-ttu-id="15239-150">Dizi benzeri sözdizimini kullanarak bir dizedeki tek tek karakterlere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15239-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="15239-151">Çıktı. `b`</span><span class="sxs-lookup"><span data-stu-id="15239-151">The output is `b`.</span></span>

<span data-ttu-id="15239-152">Veya aşağıdaki kodda gösterildiği gibi dizi dilimi sözdizimini kullanarak alt dizeleri ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15239-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="15239-153">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="15239-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="15239-154">ASCII dizelerini imzasız bayt dizilerine göre `byte[]`temsil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15239-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="15239-155">Bir ASCII `B` dize olduğunu belirtmek için bir dize literal soneki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="15239-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="15239-156">Byte dizileriyle kullanılan ASCII dize literalleri, Unicode kaçış dizileri dışında Unicode dizeleriyle aynı kaçış dizilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="15239-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="15239-157">Dize İşleçleri</span><span class="sxs-lookup"><span data-stu-id="15239-157">String Operators</span></span>

<span data-ttu-id="15239-158">İşleç, `+` .NET Framework dize işleme özellikleriyle uyumluluğu koruyarak dizeleri birleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15239-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="15239-159">Aşağıdaki örnek, dize boğma gösterir.</span><span class="sxs-lookup"><span data-stu-id="15239-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="15239-160">Yaylı Çalgılar Sınıfı</span><span class="sxs-lookup"><span data-stu-id="15239-160">String Class</span></span>

<span data-ttu-id="15239-161">F# dize türü aslında bir .NET Framework `System.String` `System.String` türü olduğundan, tüm üyeler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15239-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="15239-162">Bu, `+` dizeleri, `Length` özelliği ve diziyi Unicode karakter `Chars` dizisi olarak döndüren özelliği birleştirmek için kullanılan işleci içerir.</span><span class="sxs-lookup"><span data-stu-id="15239-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="15239-163">Dizeleri hakkında daha fazla `System.String`bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="15239-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="15239-164">`System.String`, özelliğini kullanarak, `Chars` aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dize tek tek karakterlererişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15239-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="15239-165">Yaylı Modül</span><span class="sxs-lookup"><span data-stu-id="15239-165">String Module</span></span>

<span data-ttu-id="15239-166">Dize işleme için ek işlevsellik `String` `FSharp.Core` ad alanında modüle dahildir.</span><span class="sxs-lookup"><span data-stu-id="15239-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="15239-167">Daha fazla bilgi için [Core.String Modülü'ne](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)bakın.</span><span class="sxs-lookup"><span data-stu-id="15239-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="15239-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15239-168">See also</span></span>

- [<span data-ttu-id="15239-169">F# Dil Referansı</span><span class="sxs-lookup"><span data-stu-id="15239-169">F# Language Reference</span></span>](index.md)

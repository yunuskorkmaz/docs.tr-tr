---
title: Dizeler
description: F# ' Dize ' türünün Unicode karakter dizisi olarak sabit metni nasıl temsil ettiğini öğrenin.
ms.date: 07/05/2019
ms.openlocfilehash: 25f5d7ce5059ba5ddb4e938313c511734c2d7320
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216740"
---
# <a name="strings"></a><span data-ttu-id="db305-103">Dizeler</span><span class="sxs-lookup"><span data-stu-id="db305-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="db305-104">Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürür.</span><span class="sxs-lookup"><span data-stu-id="db305-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="db305-105">Docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="db305-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="db305-106">Tür `string` , Unicode karakter dizisi olarak sabit metni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db305-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="db305-107">`string`, .NET Framework için `System.String` bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="db305-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="db305-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db305-108">Remarks</span></span>

<span data-ttu-id="db305-109">Dize sabit değerleri tırnak işareti (") karakteriyle sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="db305-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="db305-110">Ters eğik çizgi karakteri \\ () belirli özel karakterleri kodlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db305-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="db305-111">Ters eğik çizgi ve sonraki karakter birlikte *kaçış sırası*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="db305-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="db305-112">F# Dize sabit değerlerinde desteklenen kaçış dizileri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="db305-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="db305-113">Karakter</span><span class="sxs-lookup"><span data-stu-id="db305-113">Character</span></span>|<span data-ttu-id="db305-114">Kaçış sırası</span><span class="sxs-lookup"><span data-stu-id="db305-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="db305-115">Uyarı</span><span class="sxs-lookup"><span data-stu-id="db305-115">Alert</span></span>|`\a`|
|<span data-ttu-id="db305-116">Geri Al tuşu</span><span class="sxs-lookup"><span data-stu-id="db305-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="db305-117">Form akışı</span><span class="sxs-lookup"><span data-stu-id="db305-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="db305-118">Metninde</span><span class="sxs-lookup"><span data-stu-id="db305-118">Newline</span></span>|`\n`|
|<span data-ttu-id="db305-119">Satır başı</span><span class="sxs-lookup"><span data-stu-id="db305-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="db305-120">Tab</span><span class="sxs-lookup"><span data-stu-id="db305-120">Tab</span></span>|`\t`|
|<span data-ttu-id="db305-121">Dikey sekme</span><span class="sxs-lookup"><span data-stu-id="db305-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="db305-122">Ters eğik çizgi</span><span class="sxs-lookup"><span data-stu-id="db305-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="db305-123">Tırnak işareti</span><span class="sxs-lookup"><span data-stu-id="db305-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="db305-124">Kesme işareti</span><span class="sxs-lookup"><span data-stu-id="db305-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="db305-125">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="db305-125">Unicode character</span></span>|<span data-ttu-id="db305-126">`\DDD`(ondalık basamağı `\231` belirtir;000-255aralığı;Örneğin,=`D` "ç")</span><span class="sxs-lookup"><span data-stu-id="db305-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="db305-127">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="db305-127">Unicode character</span></span>|<span data-ttu-id="db305-128">`\xHH`(onaltılık basamağı `\xE7` belirtir;00-FFaralığı;Örneğin,=`H` "ç")</span><span class="sxs-lookup"><span data-stu-id="db305-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="db305-129">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="db305-129">Unicode character</span></span>|<span data-ttu-id="db305-130">`\uHHHH`(UTF-16) (onaltılık basamağı belirtir; 0000-ffff aralığı; `H`  Örneğin, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="db305-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="db305-131">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="db305-131">Unicode character</span></span>|<span data-ttu-id="db305-132">`\U00HHHHHH`(UTF-32) (onaltılık basamağı belirtir; 000000 yazın-10FFFF) aralığı `H`  Örneğin, `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="db305-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="db305-133">`\DDD` Kaçış sırası, diğer dillerin çoğunda, sekizli gösterimi değil ondalık gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="db305-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="db305-134">Bu nedenle, `8` rakamlar `9` ve geçerli ve bir dizisi `\032` bir boşluk (U + 0020) temsil ederken, sekizlik gösterimde aynı kod noktası olur `\040`.</span><span class="sxs-lookup"><span data-stu-id="db305-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="db305-135">0-255 (0xFF) `\DDD` aralığıyla sınırlandırılmakta, ve `\x` kaçış dizileri, ilk 256 Unicode kod noktalarıyla eşleştiğinden, etkin şekilde [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) karakter kümesidir.</span><span class="sxs-lookup"><span data-stu-id="db305-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="db305-136">Önünde @ sembolü varsa, değişmez değer tam bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="db305-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="db305-137">Bu, iki tırnak işareti karakterinin tek tırnak işareti karakteri olarak yorumlanmasının dışında, tüm kaçış dizileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="db305-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="db305-138">Ayrıca, bir dize, Üçlü tırnak içine alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="db305-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="db305-139">Bu durumda, çift tırnak işareti karakterleri de dahil olmak üzere tüm kaçış dizileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="db305-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="db305-140">Katıştırılmış bir alıntı dize içeren bir dize belirtmek için, tam bir dize veya Üçlü tırnak işareti kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db305-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="db305-141">Tam bir dize kullanırsanız, tek tırnak işareti karakterini göstermek için iki tırnak işareti karakteri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="db305-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="db305-142">Üçlü olarak tırnak içine alınmış bir dize kullanırsanız, tek tırnak işareti karakterlerini dizenin sonu olarak ayrıştırılmaksızın kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db305-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="db305-143">Bu teknik, ekli tırnak işaretleri içeren XML veya diğer yapılarla çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="db305-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="db305-144">Kod içinde, satır sonları içeren dizeler kabul edilir ve satır sonları satır sonundan önce son karakter olan bir ters eğik çizgi karakteri olmayan bir şekilde newlines olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="db305-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="db305-145">Ters eğik çizgi karakteri kullanıldığında sonraki satırdaki baştaki boşluk yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="db305-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="db305-146">Aşağıdaki kod değeri `"abc\ndef"` olan bir dize `str1` ve değeri `"abcdef"`olan bir `str2` dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db305-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="db305-147">Bir dizedeki ayrı karakterlere, aşağıdaki gibi dizi benzeri sözdizimini kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db305-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="db305-148">Çıktı `b`.</span><span class="sxs-lookup"><span data-stu-id="db305-148">The output is `b`.</span></span>

<span data-ttu-id="db305-149">Ya da aşağıdaki kodda gösterildiği gibi, dizi dilimi söz dizimini kullanarak alt dizeleri de ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db305-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="db305-150">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="db305-150">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="db305-151">ASCII dizelerini işaretsiz bayt dizileri ile temsil edebilirsiniz, şunu yazın `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="db305-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="db305-152">Bir ASCII dizesi olduğunu `B` göstermek için son eki bir dize değişmez değerine eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="db305-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="db305-153">Bayt dizileri ile kullanılan ASCII dize sabit değerleri, Unicode kaçış dizileri hariç, Unicode dizeleriyle aynı kaçış dizilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="db305-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="db305-154">Dize İşleçleri</span><span class="sxs-lookup"><span data-stu-id="db305-154">String Operators</span></span>

<span data-ttu-id="db305-155">Dizeleri birleştirmek için iki yol vardır: `+` işlecini kullanarak veya `^` işlecini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="db305-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="db305-156">`+` İşleci .NET Framework dize işleme özellikleriyle uyumluluğu korur.</span><span class="sxs-lookup"><span data-stu-id="db305-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="db305-157">Aşağıdaki örnekte dize birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="db305-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="db305-158">String sınıfı</span><span class="sxs-lookup"><span data-stu-id="db305-158">String Class</span></span>

<span data-ttu-id="db305-159">İçindeki F# dize türü aslında .NET Framework `System.String` bir `System.String` tür olduğundan tüm Üyeler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db305-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="db305-160">Bu, dizeleri `+` `Length` , özelliği ve `Chars` bir Unicode karakter dizisi olarak dizeyi döndüren özelliğini birleştirmek için kullanılan işleci içerir.</span><span class="sxs-lookup"><span data-stu-id="db305-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="db305-161">Dizeler hakkında daha fazla bilgi için bkz `System.String`.</span><span class="sxs-lookup"><span data-stu-id="db305-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="db305-162">`Chars` Özelliğini kullanarak ,aşağıdakikoddagösterildiğigibibirdizinbelirterekbirdizedeki`System.String`ayrı karakterlere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db305-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="db305-163">Dize modülü</span><span class="sxs-lookup"><span data-stu-id="db305-163">String Module</span></span>

<span data-ttu-id="db305-164">Dize işleme için ek işlevler, `String` `FSharp.Core` ad alanındaki modüle dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="db305-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="db305-165">Daha fazla bilgi için bkz. [Core. String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="db305-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="db305-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db305-166">See also</span></span>

- [<span data-ttu-id="db305-167">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="db305-167">F# Language Reference</span></span>](index.md)

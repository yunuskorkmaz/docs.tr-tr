---
title: Dizeler
description: "F # ' String ' türünün Unicode karakter dizisi olarak sabit metni nasıl temsil ettiğini öğrenin."
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812217"
---
# <a name="strings"></a><span data-ttu-id="af1e0-103">Dizeler</span><span class="sxs-lookup"><span data-stu-id="af1e0-103">Strings</span></span>

<span data-ttu-id="af1e0-104">`string`Tür, Unicode karakter dizisi olarak sabit metni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="af1e0-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="af1e0-105">`string` , .NET içindeki için bir diğer addır `System.String` .</span><span class="sxs-lookup"><span data-stu-id="af1e0-105">`string` is an alias for `System.String` in .NET.</span></span>

## <a name="remarks"></a><span data-ttu-id="af1e0-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af1e0-106">Remarks</span></span>

<span data-ttu-id="af1e0-107">Dize sabit değerleri tırnak işareti (") karakteriyle sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="af1e0-107">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="af1e0-108">Ters eğik çizgi karakteri ( \\ ) belirli özel karakterleri kodlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af1e0-108">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="af1e0-109">Ters eğik çizgi ve sonraki karakter birlikte *kaçış sırası*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-109">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="af1e0-110">F # dize değişmez değerlerinde desteklenen kaçış dizileri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-110">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="af1e0-111">Karakter</span><span class="sxs-lookup"><span data-stu-id="af1e0-111">Character</span></span>|<span data-ttu-id="af1e0-112">Kaçış sırası</span><span class="sxs-lookup"><span data-stu-id="af1e0-112">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="af1e0-113">Uyarı</span><span class="sxs-lookup"><span data-stu-id="af1e0-113">Alert</span></span>|`\a`|
|<span data-ttu-id="af1e0-114">Geri Al tuşu</span><span class="sxs-lookup"><span data-stu-id="af1e0-114">Backspace</span></span>|`\b`|
|<span data-ttu-id="af1e0-115">Form akışı</span><span class="sxs-lookup"><span data-stu-id="af1e0-115">Form feed</span></span>|`\f`|
|<span data-ttu-id="af1e0-116">Metninde</span><span class="sxs-lookup"><span data-stu-id="af1e0-116">Newline</span></span>|`\n`|
|<span data-ttu-id="af1e0-117">Satır başı</span><span class="sxs-lookup"><span data-stu-id="af1e0-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="af1e0-118">Tab</span><span class="sxs-lookup"><span data-stu-id="af1e0-118">Tab</span></span>|`\t`|
|<span data-ttu-id="af1e0-119">Dikey sekme</span><span class="sxs-lookup"><span data-stu-id="af1e0-119">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="af1e0-120">Sola</span><span class="sxs-lookup"><span data-stu-id="af1e0-120">Backslash</span></span>|`\\`|
|<span data-ttu-id="af1e0-121">Tırnak işareti</span><span class="sxs-lookup"><span data-stu-id="af1e0-121">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="af1e0-122">Kesme işareti</span><span class="sxs-lookup"><span data-stu-id="af1e0-122">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="af1e0-123">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="af1e0-123">Unicode character</span></span>|<span data-ttu-id="af1e0-124">`\DDD` ( `D` ondalık basamağı belirtir; 000-255 aralığı; Örneğin, `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="af1e0-124">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="af1e0-125">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="af1e0-125">Unicode character</span></span>|<span data-ttu-id="af1e0-126">`\xHH` ( `H` onaltılık basamağı belirtir; 00-FF aralığı; Örneğin, `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="af1e0-126">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="af1e0-127">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="af1e0-127">Unicode character</span></span>|<span data-ttu-id="af1e0-128">`\uHHHH` (UTF-16) ( `H` onaltılık basamağı belirtir; 0000-ffff aralığı;  Örneğin, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="af1e0-128">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="af1e0-129">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="af1e0-129">Unicode character</span></span>|<span data-ttu-id="af1e0-130">`\U00HHHHHH` (UTF-32) ( `H` onaltılık basamağı belirtir; 000000 yazın-10FFFF) aralığı  Örneğin, `\U0001F47D` = " 👽 ")</span><span class="sxs-lookup"><span data-stu-id="af1e0-130">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="af1e0-131">`\DDD`Kaçış sırası, diğer dillerin çoğunda, sekizli gösterimi değil ondalık gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-131">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="af1e0-132">Bu nedenle, rakamlar `8` ve `9` geçerli ve bir dizisi `\032` bir boşluk (U + 0020) temsil ederken, sekizlik gösterimde aynı kod noktası olur `\040` .</span><span class="sxs-lookup"><span data-stu-id="af1e0-132">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="af1e0-133">0-255 (0xFF) aralığıyla sınırlandırılmakta, `\DDD` ve `\x` kaçış dizileri, Ilk 256 Unicode kod noktalarıyla eşleştiğinden, etkin şekilde [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) karakter kümesidir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-133">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="af1e0-134">Tam dizeler</span><span class="sxs-lookup"><span data-stu-id="af1e0-134">Verbatim Strings</span></span>

<span data-ttu-id="af1e0-135">Önünde @ sembolü varsa, değişmez değer tam bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-135">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="af1e0-136">Bu, iki tırnak işareti karakterinin tek tırnak işareti karakteri olarak yorumlanmasının dışında, tüm kaçış dizileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="af1e0-136">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="af1e0-137">Üçlü alıntılanmış dizeler</span><span class="sxs-lookup"><span data-stu-id="af1e0-137">Triple Quoted Strings</span></span>

<span data-ttu-id="af1e0-138">Ayrıca, bir dize, Üçlü tırnak içine alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="af1e0-139">Bu durumda, çift tırnak işareti karakterleri de dahil olmak üzere tüm kaçış dizileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="af1e0-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="af1e0-140">Katıştırılmış bir alıntı dize içeren bir dize belirtmek için, tam bir dize veya Üçlü tırnak işareti kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af1e0-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="af1e0-141">Tam bir dize kullanırsanız, tek tırnak işareti karakterini göstermek için iki tırnak işareti karakteri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="af1e0-142">Üçlü olarak tırnak içine alınmış bir dize kullanırsanız, tek tırnak işareti karakterlerini dizenin sonu olarak ayrıştırılmaksızın kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af1e0-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="af1e0-143">Bu teknik, ekli tırnak işaretleri içeren XML veya diğer yapılarla çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="af1e0-144">Kod içinde, satır sonları içeren dizeler kabul edilir ve satır sonları satır sonundan önce son karakter olan bir ters eğik çizgi karakteri olmayan bir şekilde newlines olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="af1e0-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="af1e0-145">Ters eğik çizgi karakteri kullanıldığında sonraki satırdaki baştaki boşluk yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="af1e0-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="af1e0-146">Aşağıdaki kod değeri olan bir dize `str1` `"abc\ndef"` ve değeri olan bir dize oluşturur `str2` `"abcdef"` .</span><span class="sxs-lookup"><span data-stu-id="af1e0-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="af1e0-147">Dize dizinleme ve dilimleme</span><span class="sxs-lookup"><span data-stu-id="af1e0-147">String Indexing and Slicing</span></span>

<span data-ttu-id="af1e0-148">Bir dizedeki ayrı karakterlere, aşağıdaki gibi dizi benzeri sözdizimini kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af1e0-148">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="af1e0-149">Çıktı `b` olur.</span><span class="sxs-lookup"><span data-stu-id="af1e0-149">The output is `b`.</span></span>

<span data-ttu-id="af1e0-150">Ya da aşağıdaki kodda gösterildiği gibi, dizi dilimi söz dizimini kullanarak alt dizeleri de ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af1e0-150">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="af1e0-151">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="af1e0-151">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="af1e0-152">ASCII dizelerini işaretsiz bayt dizileri ile temsil edebilirsiniz, şunu yazın `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="af1e0-152">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="af1e0-153">Bir `B` ASCII dizesi olduğunu göstermek için son eki bir dize değişmez değerine eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="af1e0-153">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="af1e0-154">Bayt dizileri ile kullanılan ASCII dize sabit değerleri, Unicode kaçış dizileri hariç, Unicode dizeleriyle aynı kaçış dizilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="af1e0-154">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="af1e0-155">Dize İşleçleri</span><span class="sxs-lookup"><span data-stu-id="af1e0-155">String Operators</span></span>

<span data-ttu-id="af1e0-156">`+`İşleci, .NET Framework dize işleme özellikleriyle uyumluluğu korumak için dizeleri birleştirmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-156">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="af1e0-157">Aşağıdaki örnekte dize birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="af1e0-158">String sınıfı</span><span class="sxs-lookup"><span data-stu-id="af1e0-158">String Class</span></span>

<span data-ttu-id="af1e0-159">F # ' deki dize türü aslında .NET Framework bir tür olduğundan `System.String` tüm `System.String` Üyeler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="af1e0-160">Bu, `+` dizeleri, `Length` özelliği ve `Chars` bir Unicode karakter dizisi olarak dizeyi döndüren özelliğini birleştirmek için kullanılan işleci içerir.</span><span class="sxs-lookup"><span data-stu-id="af1e0-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="af1e0-161">Dizeler hakkında daha fazla bilgi için bkz `System.String` ..</span><span class="sxs-lookup"><span data-stu-id="af1e0-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="af1e0-162">`Chars`Özelliğini kullanarak `System.String` , aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dizedeki ayrı karakterlere erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af1e0-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="af1e0-163">Dize modülü</span><span class="sxs-lookup"><span data-stu-id="af1e0-163">String Module</span></span>

<span data-ttu-id="af1e0-164">Dize işleme için ek işlevler, `String` ad alanındaki modüle dahil edilmiştir `FSharp.Core` .</span><span class="sxs-lookup"><span data-stu-id="af1e0-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="af1e0-165">Daha fazla bilgi için bkz. [dize modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span><span class="sxs-lookup"><span data-stu-id="af1e0-165">For more information, see [String Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="af1e0-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af1e0-166">See also</span></span>

- [<span data-ttu-id="af1e0-167">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="af1e0-167">F# Language Reference</span></span>](index.md)

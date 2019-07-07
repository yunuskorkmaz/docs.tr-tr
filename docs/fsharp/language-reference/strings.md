---
title: Dizeler
description: Bilgi nasıl F# 'string' türü sabit metin Unicode karakter dizisi olarak temsil eder.
ms.date: 07/05/2019
ms.openlocfilehash: b252aef7d7e6e299df8282407198714971e80cd5
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610170"
---
# <a name="strings"></a><span data-ttu-id="48183-103">Dizeler</span><span class="sxs-lookup"><span data-stu-id="48183-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="48183-104">Bu makaledeki API başvuru bağlantıları için MSDN sürer.</span><span class="sxs-lookup"><span data-stu-id="48183-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="48183-105">Docs.microsoft.com API başvuru tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="48183-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="48183-106">`string` Türü sabit metin Unicode karakter dizisi olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48183-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="48183-107">`string` için bir diğer addır `System.String` .NET Framework'teki.</span><span class="sxs-lookup"><span data-stu-id="48183-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="48183-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48183-108">Remarks</span></span>

<span data-ttu-id="48183-109">Dize değişmez değerleri tırnak işareti (") karakteriyle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="48183-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="48183-110">Ters eğik çizgi karakteri ( \\ ) özel karakterleri kodlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48183-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="48183-111">Ters eğik çizgi ve birlikte sonraki karakteri olarak bilinen bir *kaçış dizisi*.</span><span class="sxs-lookup"><span data-stu-id="48183-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="48183-112">Kaçış dizileri desteklenen F# dize değişmez değerleri aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="48183-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="48183-113">Karakter</span><span class="sxs-lookup"><span data-stu-id="48183-113">Character</span></span>|<span data-ttu-id="48183-114">Kaçış sırası</span><span class="sxs-lookup"><span data-stu-id="48183-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="48183-115">Uyarı</span><span class="sxs-lookup"><span data-stu-id="48183-115">Alert</span></span>|`\a`|
|<span data-ttu-id="48183-116">Geri Al tuşu</span><span class="sxs-lookup"><span data-stu-id="48183-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="48183-117">form besleme</span><span class="sxs-lookup"><span data-stu-id="48183-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="48183-118">Yeni satır</span><span class="sxs-lookup"><span data-stu-id="48183-118">Newline</span></span>|`\n`|
|<span data-ttu-id="48183-119">satır başı</span><span class="sxs-lookup"><span data-stu-id="48183-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="48183-120">Tab</span><span class="sxs-lookup"><span data-stu-id="48183-120">Tab</span></span>|`\t`|
|<span data-ttu-id="48183-121">dikey sekme</span><span class="sxs-lookup"><span data-stu-id="48183-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="48183-122">Ters eğik çizgi</span><span class="sxs-lookup"><span data-stu-id="48183-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="48183-123">Tırnak işareti</span><span class="sxs-lookup"><span data-stu-id="48183-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="48183-124">Kesme işareti</span><span class="sxs-lookup"><span data-stu-id="48183-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="48183-125">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="48183-125">Unicode character</span></span>|<span data-ttu-id="48183-126">`\DDD` (burada `D` gösteren bir ondalık basamak; 000 - aralığını 255; örn `\231` "ç" =)</span><span class="sxs-lookup"><span data-stu-id="48183-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; e.g. `\231` = "ç")</span></span>|
|<span data-ttu-id="48183-127">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="48183-127">Unicode character</span></span>|<span data-ttu-id="48183-128">`\xHH` (burada `H` onaltılık bir basamaktır; 00 - FF; aralığını gösteren örn `\xE7` "ç" =)</span><span class="sxs-lookup"><span data-stu-id="48183-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; e.g. `\xE7` = "ç")</span></span>|
|<span data-ttu-id="48183-129">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="48183-129">Unicode character</span></span>|<span data-ttu-id="48183-130">`\uHHHH` (UTF-16) (burada `H` onaltılık bir basamaktır; 0000 - FFFF; aralığını gösterir  Örneğin `\u00E7` "ç" =)</span><span class="sxs-lookup"><span data-stu-id="48183-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  e.g. `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="48183-131">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="48183-131">Unicode character</span></span>|<span data-ttu-id="48183-132">`\U00HHHHHH` (UTF-32) (burada `H` onaltılık bir basamaktır; 000000 - 10FFFF; aralığını gösterir  Örneğin `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="48183-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  e.g. `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="48183-133">`\DDD` Kaçış dizisi olan ondalık gösterim, çoğu dil gibi değil sekizlik gösterim.</span><span class="sxs-lookup"><span data-stu-id="48183-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="48183-134">Bu nedenle, basamak `8` ve `9` geçerli olduğundan ve bir dizi `\032` bir alanını temsil eder (U + 0020), o aynı kod noktası sekizlik gösterimde olabilir ancak `\040`.</span><span class="sxs-lookup"><span data-stu-id="48183-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="48183-135">0 aralığına kısıtlanmasını - 255 (0xFF) `\DDD` ve `\x` kaçış dizileri, esas [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , ilk 256 Unicode kod noktaları eşleştiğinden karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="48183-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="48183-136">Öncesinde, @ sembolü, değişmez değer verbatim bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="48183-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="48183-137">İki tırnak karakteri tek tırnak işareti karakteri yorumlanır dışında bu, herhangi bir kaçış dizileri göz ardı, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="48183-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="48183-138">Ayrıca, bir dize Üçlü tırnak işareti içine alınabilir.</span><span class="sxs-lookup"><span data-stu-id="48183-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="48183-139">Bu durumda, çift tırnak işareti karakterleri dahil olmak üzere tüm kaçış dizileri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="48183-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="48183-140">Sınırlandırılmış bir katıştırılmış içeren bir dize belirtmek için ya da bir harfi harfine veya bir Üçlü alıntılanmış dize kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48183-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="48183-141">Verbatim dizesi kullanıyorsanız, iki tırnak karakteri tek tırnak işareti karakteri belirtmek için belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="48183-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="48183-142">Üçlü tırnak içine bir dize kullanmak, bunları dize sonu Ayrıştırılmakta olmadan tek tırnak işareti karakter kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48183-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="48183-143">Bu teknik, XML veya katıştırılmış tırnak işaretleri dahil diğer yapılar çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="48183-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="48183-144">Kodda satır sonları olan dizeleri kabul edilir ve son karakter satır sonundan önce bir ters eğik çizgi karakteri olmadığı sürece satır sonları tam anlamıyla yeni satırlardan yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="48183-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="48183-145">Ters eğik çizgi karakteri kullanıldığında sonraki satıra önde gelen boşluk yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="48183-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="48183-146">Aşağıdaki kod bir dize üretir `str1` değeri olan `"abc\ndef"` ve bir dize `str2` değeri olan `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="48183-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="48183-147">Aşağıdaki gibi bir dizi benzeri sözdizimi kullanarak, bir dizedeki karakterlerin tek tek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48183-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="48183-148">Çıktı `b`.</span><span class="sxs-lookup"><span data-stu-id="48183-148">The output is `b`.</span></span>

<span data-ttu-id="48183-149">Veya, alt dizeler dizisi dilim söz dizimini kullanarak aşağıdaki kodda gösterildiği gibi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48183-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="48183-150">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="48183-150">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="48183-151">ASCII dizelerinde işaretsiz bayt sayısı, türü bir dizi temsil edebilen `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="48183-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="48183-152">Sonek Ekle `B` için bir ASCII dizesi olduğunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="48183-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="48183-153">Bayt dizileri ile kullanılan ASCII dize değişmez değerleri, Unicode kaçış dizileri dışında Unicode dize olarak aynı kaçış dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="48183-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="48183-154">Dize İşleçleri</span><span class="sxs-lookup"><span data-stu-id="48183-154">String Operators</span></span>

<span data-ttu-id="48183-155">Dizeleri birleştirmek için iki yolu vardır: kullanarak `+` işleci kullanarak veya `^` işleci.</span><span class="sxs-lookup"><span data-stu-id="48183-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="48183-156">`+` İşleci özellikleri işleme .NET Framework dize ile uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="48183-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="48183-157">Aşağıdaki örnekte, dize birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="48183-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="48183-158">Dize sınıfı</span><span class="sxs-lookup"><span data-stu-id="48183-158">String Class</span></span>

<span data-ttu-id="48183-159">Çünkü dize türü içinde F# aslında bir .NET Framework `System.String` yazın, tümünü `System.String` üyeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48183-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="48183-160">Bu içerir `+` dizeyi birleştirmek için kullanılır, operatör `Length` özelliği ve `Chars` dize Unicode karakter dizisi olarak döndüren özellik.</span><span class="sxs-lookup"><span data-stu-id="48183-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="48183-161">Dizeleri hakkında daha fazla bilgi için bkz. `System.String`.</span><span class="sxs-lookup"><span data-stu-id="48183-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="48183-162">Kullanarak `Chars` özelliği `System.String`, aşağıdaki kodda gösterildiği gibi bir dizin belirterek, bir dizedeki karakterlerin tek tek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48183-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="48183-163">String modülü</span><span class="sxs-lookup"><span data-stu-id="48183-163">String Module</span></span>

<span data-ttu-id="48183-164">Dize işleme için ek işlevler dahil `String` modülünde `FSharp.Core` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="48183-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="48183-165">Daha fazla bilgi için [Core.String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="48183-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="48183-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48183-166">See also</span></span>

- [<span data-ttu-id="48183-167">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="48183-167">F# Language Reference</span></span>](index.md)

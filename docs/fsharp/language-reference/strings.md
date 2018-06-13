---
title: Dizeler (F#)
description: "F # 'string' türü değişmez metin Unicode karakter dizisi nasıl temsil öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: bdd1d1a542e70bcd95fce51e75d0c1ddffceb008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564865"
---
# <a name="strings"></a><span data-ttu-id="e97e9-103">Dizeler</span><span class="sxs-lookup"><span data-stu-id="e97e9-103">Strings</span></span>

> [!NOTE]
<span data-ttu-id="e97e9-104">Bu makalede API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="e97e9-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="e97e9-105">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="e97e9-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="e97e9-106">`string` Türü değişmez metin Unicode karakter dizisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e97e9-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="e97e9-107">`string` bir diğer adı için `System.String` .NET Framework'teki.</span><span class="sxs-lookup"><span data-stu-id="e97e9-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="e97e9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e97e9-108">Remarks</span></span>
<span data-ttu-id="e97e9-109">Dize değişmez değerleri tırnak işareti (") karakteriyle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e97e9-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="e97e9-110">Ters eğik çizgi karakteri (\) özel karakterleri kodlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e97e9-110">The backslash character (\) is used to encode certain special characters.</span></span> <span data-ttu-id="e97e9-111">Ters eğik çizgi ve birlikte sonraki karakteri olarak bilinen bir *kaçış dizisi*.</span><span class="sxs-lookup"><span data-stu-id="e97e9-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="e97e9-112">Kaçış dizilerine değişmez değerleri aşağıdaki tabloda gösterilen F # dize desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e97e9-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="e97e9-113">Karakter</span><span class="sxs-lookup"><span data-stu-id="e97e9-113">Character</span></span>|<span data-ttu-id="e97e9-114">Kaçış sırası</span><span class="sxs-lookup"><span data-stu-id="e97e9-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="e97e9-115">Geri Al tuşu</span><span class="sxs-lookup"><span data-stu-id="e97e9-115">Backspace</span></span>|<span data-ttu-id="e97e9-116">\b</span><span class="sxs-lookup"><span data-stu-id="e97e9-116">\b</span></span>|
|<span data-ttu-id="e97e9-117">Yeni satır</span><span class="sxs-lookup"><span data-stu-id="e97e9-117">Newline</span></span>|<span data-ttu-id="e97e9-118">\n</span><span class="sxs-lookup"><span data-stu-id="e97e9-118">\n</span></span>|
|<span data-ttu-id="e97e9-119">satır başı</span><span class="sxs-lookup"><span data-stu-id="e97e9-119">Carriage return</span></span>|<span data-ttu-id="e97e9-120">\r</span><span class="sxs-lookup"><span data-stu-id="e97e9-120">\r</span></span>|
|<span data-ttu-id="e97e9-121">Tab</span><span class="sxs-lookup"><span data-stu-id="e97e9-121">Tab</span></span>|<span data-ttu-id="e97e9-122">\t</span><span class="sxs-lookup"><span data-stu-id="e97e9-122">\t</span></span>|
|<span data-ttu-id="e97e9-123">ters eğik çizgi</span><span class="sxs-lookup"><span data-stu-id="e97e9-123">Backslash</span></span>|\\|
|<span data-ttu-id="e97e9-124">Tırnak işareti</span><span class="sxs-lookup"><span data-stu-id="e97e9-124">Quotation mark</span></span>|\"|
|<span data-ttu-id="e97e9-125">Kesme işareti</span><span class="sxs-lookup"><span data-stu-id="e97e9-125">Apostrophe</span></span>|\'|
|<span data-ttu-id="e97e9-126">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="e97e9-126">Unicode character</span></span>|<span data-ttu-id="e97e9-127">\u*XXXX* veya \U*XXXXXXXX* (burada *X* onaltılık basamak gösterir)</span><span class="sxs-lookup"><span data-stu-id="e97e9-127">\u*XXXX* or \U*XXXXXXXX* (where *X* indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="e97e9-128">Öncesinde, @ sembolü, sabit verbatim bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e97e9-128">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="e97e9-129">İki tırnak işareti karakteri tek tırnak işareti karakteri olarak yorumlanır dışında bu, tüm çıkış sıraları göz ardı, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e97e9-129">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="e97e9-130">Ayrıca, bir dize Üçlü tırnak içine.</span><span class="sxs-lookup"><span data-stu-id="e97e9-130">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="e97e9-131">Bu durumda, çift tırnak işareti karakterleri dahil olmak üzere tüm çıkış sıraları yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e97e9-131">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="e97e9-132">Sınırlandırılmış bir katıştırılmış içeren bir dize belirtmek için ya da bir verbatim veya Üçlü tırnak içine alınmış bir dize kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e97e9-132">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="e97e9-133">Harfi harfine bir dize kullanmak, tek tırnak işareti karakteri belirtmek için iki tırnak işareti karakteri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e97e9-133">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="e97e9-134">Üçlü tırnak içine alınmış bir dize kullanmak, bunları dize sonu Ayrıştırılmakta olmadan tek tırnak işareti karakter kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e97e9-134">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="e97e9-135">Bu yöntem, XML veya katıştırılmış tırnak işaretleri dahil diğer yapıları çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e97e9-135">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="e97e9-136">Kodda, satır sonları sahip dizeleri kabul edilir ve satır sonundan önceki son karakter bir ters bölü karakteri olmadığı sürece satır sonları tam anlamıyla satır başı yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="e97e9-136">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="e97e9-137">Ters eğik çizgi karakteri kullanıldığında, sonraki satıra öndeki boşlukları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="e97e9-137">Leading whitespace on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="e97e9-138">Aşağıdaki kod bir dize oluşturur `str1` değeri olan `"abc\n     def"` ve bir dize `str2` değeri olan `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="e97e9-138">The following code produces a string `str1` that has value `"abc\n     def"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="e97e9-139">Bir dizede tek tek karakterleri şekilde dizi benzeri sözdizimi kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e97e9-139">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="e97e9-140">Çıktı `b`.</span><span class="sxs-lookup"><span data-stu-id="e97e9-140">The output is `b`.</span></span>

<span data-ttu-id="e97e9-141">Veya, alt dizeler dizisi dilim sözdizimini kullanarak aşağıdaki kodda gösterildiği gibi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e97e9-141">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="e97e9-142">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e97e9-142">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="e97e9-143">İmzasız bayt sayısı, türü diziler tarafından ASCII dizeleri gösterebilir `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="e97e9-143">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="e97e9-144">Soneki eklemek `B` bir ASCII dizesi olduğunu belirtmek için bir dize için.</span><span class="sxs-lookup"><span data-stu-id="e97e9-144">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="e97e9-145">Bayt dizileri ile kullanılan ASCII dize değişmez değerleri aynı kaçış sıraları Unicode kaçış sıraları dışında Unicode dizeleri olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="e97e9-145">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a><span data-ttu-id="e97e9-146">Dize İşleçleri</span><span class="sxs-lookup"><span data-stu-id="e97e9-146">String Operators</span></span>
<span data-ttu-id="e97e9-147">Dizeyi birleştirmek için iki yolu vardır: kullanarak `+` işleci veya kullanarak `^` işleci.</span><span class="sxs-lookup"><span data-stu-id="e97e9-147">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="e97e9-148">`+` İşleci .NET Framework dize özellikleri işleme ile uyumluluk korur.</span><span class="sxs-lookup"><span data-stu-id="e97e9-148">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="e97e9-149">Aşağıdaki örnek, dize birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e97e9-149">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a><span data-ttu-id="e97e9-150">String sınıfı</span><span class="sxs-lookup"><span data-stu-id="e97e9-150">String Class</span></span>
<span data-ttu-id="e97e9-151">F # dize türü gerçekte bir .NET Framework olduğundan `System.String` türü, tüm `System.String` üyeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e97e9-151">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="e97e9-152">Bu içerir `+` dizeyi birleştirmek için kullanılan işleci `Length` özelliği ve `Chars` özelliği dize Unicode karakter dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e97e9-152">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="e97e9-153">Dizeleri hakkında daha fazla bilgi için bkz: `System.String`.</span><span class="sxs-lookup"><span data-stu-id="e97e9-153">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="e97e9-154">Kullanarak `Chars` özelliği `System.String`, aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dizedeki karakterleri tek tek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e97e9-154">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a><span data-ttu-id="e97e9-155">String modülü</span><span class="sxs-lookup"><span data-stu-id="e97e9-155">String Module</span></span>
<span data-ttu-id="e97e9-156">Dize işleme için ek işlevler dahil `String` modülünde `FSharp.Core` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e97e9-156">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="e97e9-157">Daha fazla bilgi için bkz: [Core.String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="e97e9-157">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="e97e9-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e97e9-158">See Also</span></span>
[<span data-ttu-id="e97e9-159">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e97e9-159">F# Language Reference</span></span>](index.md)

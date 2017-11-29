---
title: Dizeler (F#)
description: "F # 'string' türü değişmez metin Unicode karakter dizisi nasıl temsil öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: df7624e5-ca6c-4e77-9e2b-87ca7e5e6f52
ms.openlocfilehash: 96a398ebcd53681481b10d1a2bee5f1e5442a5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="strings"></a><span data-ttu-id="bac2a-104">Dizeler</span><span class="sxs-lookup"><span data-stu-id="bac2a-104">Strings</span></span>

> [!NOTE]
<span data-ttu-id="bac2a-105">Bu makalede API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="bac2a-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="bac2a-106">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="bac2a-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="bac2a-107">`string` Türü değişmez metin Unicode karakter dizisi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bac2a-107">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="bac2a-108">`string`bir diğer adı için `System.String` .NET Framework'teki.</span><span class="sxs-lookup"><span data-stu-id="bac2a-108">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="bac2a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bac2a-109">Remarks</span></span>
<span data-ttu-id="bac2a-110">Dize değişmez değerleri tırnak işareti (") karakteriyle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="bac2a-110">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="bac2a-111">Ters eğik çizgi karakteri (\) özel karakterleri kodlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bac2a-111">The backslash character (\) is used to encode certain special characters.</span></span> <span data-ttu-id="bac2a-112">Ters eğik çizgi ve birlikte sonraki karakteri olarak bilinen bir *kaçış dizisi*.</span><span class="sxs-lookup"><span data-stu-id="bac2a-112">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="bac2a-113">Kaçış dizilerine değişmez değerleri aşağıdaki tabloda gösterilen F # dize desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bac2a-113">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="bac2a-114">Karakter</span><span class="sxs-lookup"><span data-stu-id="bac2a-114">Character</span></span>|<span data-ttu-id="bac2a-115">Kaçış sırası</span><span class="sxs-lookup"><span data-stu-id="bac2a-115">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="bac2a-116">Geri Al tuşu</span><span class="sxs-lookup"><span data-stu-id="bac2a-116">Backspace</span></span>|<span data-ttu-id="bac2a-117">\b</span><span class="sxs-lookup"><span data-stu-id="bac2a-117">\b</span></span>|
|<span data-ttu-id="bac2a-118">Yeni satır</span><span class="sxs-lookup"><span data-stu-id="bac2a-118">Newline</span></span>|\n|
|<span data-ttu-id="bac2a-119">satır başı</span><span class="sxs-lookup"><span data-stu-id="bac2a-119">Carriage return</span></span>|<span data-ttu-id="bac2a-120">\r</span><span class="sxs-lookup"><span data-stu-id="bac2a-120">\r</span></span>|
|<span data-ttu-id="bac2a-121">Tab</span><span class="sxs-lookup"><span data-stu-id="bac2a-121">Tab</span></span>|<span data-ttu-id="bac2a-122">\t</span><span class="sxs-lookup"><span data-stu-id="bac2a-122">\t</span></span>|
|<span data-ttu-id="bac2a-123">ters eğik çizgi</span><span class="sxs-lookup"><span data-stu-id="bac2a-123">Backslash</span></span>|\\|
|<span data-ttu-id="bac2a-124">Tırnak işareti</span><span class="sxs-lookup"><span data-stu-id="bac2a-124">Quotation mark</span></span>|\"|
|<span data-ttu-id="bac2a-125">Kesme işareti</span><span class="sxs-lookup"><span data-stu-id="bac2a-125">Apostrophe</span></span>|\'|
|<span data-ttu-id="bac2a-126">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="bac2a-126">Unicode character</span></span>|<span data-ttu-id="bac2a-127">\u*XXXX* veya \U*XXXXXXXX* (burada *X* onaltılık basamak gösterir)</span><span class="sxs-lookup"><span data-stu-id="bac2a-127">\u*XXXX* or \U*XXXXXXXX* (where *X* indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="bac2a-128">Öncesinde, @ sembolü, sabit verbatim bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="bac2a-128">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="bac2a-129">İki tırnak işareti karakteri tek tırnak işareti karakteri olarak yorumlanır dışında bu, tüm çıkış sıraları göz ardı, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bac2a-129">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="bac2a-130">Ayrıca, bir dize Üçlü tırnak içine.</span><span class="sxs-lookup"><span data-stu-id="bac2a-130">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="bac2a-131">Bu durumda, çift tırnak işareti karakterleri dahil olmak üzere tüm çıkış sıraları yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="bac2a-131">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="bac2a-132">Sınırlandırılmış bir katıştırılmış içeren bir dize belirtmek için ya da bir verbatim veya Üçlü tırnak içine alınmış bir dize kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bac2a-132">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="bac2a-133">Harfi harfine bir dize kullanmak, tek tırnak işareti karakteri belirtmek için iki tırnak işareti karakteri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bac2a-133">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="bac2a-134">Üçlü tırnak içine alınmış bir dize kullanmak, bunları dize sonu Ayrıştırılmakta olmadan tek tırnak işareti karakter kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bac2a-134">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="bac2a-135">Bu yöntem, XML veya katıştırılmış tırnak işaretleri dahil diğer yapıları çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bac2a-135">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="bac2a-136">Kodda, satır sonları sahip dizeleri kabul edilir ve satır sonundan önceki son karakter bir ters bölü karakteri olmadığı sürece satır sonları tam anlamıyla satır başı yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="bac2a-136">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="bac2a-137">Ters eğik çizgi karakteri kullanıldığında, sonraki satıra öndeki boşlukları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="bac2a-137">Leading whitespace on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="bac2a-138">Aşağıdaki kod bir dize oluşturur `str1` değeri olan `"abc\n     def"` ve bir dize `str2` değeri olan `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="bac2a-138">The following code produces a string `str1` that has value `"abc\n     def"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="bac2a-139">Bir dizede tek tek karakterleri şekilde dizi benzeri sözdizimi kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bac2a-139">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="bac2a-140">Çıktı `b`.</span><span class="sxs-lookup"><span data-stu-id="bac2a-140">The output is `b`.</span></span>

<span data-ttu-id="bac2a-141">Veya, alt dizeler dizisi dilim sözdizimini kullanarak aşağıdaki kodda gösterildiği gibi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bac2a-141">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="bac2a-142">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bac2a-142">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="bac2a-143">İmzasız bayt sayısı, türü diziler tarafından ASCII dizeleri gösterebilir `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="bac2a-143">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="bac2a-144">Soneki eklemek `B` bir ASCII dizesi olduğunu belirtmek için bir dize için.</span><span class="sxs-lookup"><span data-stu-id="bac2a-144">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="bac2a-145">Bayt dizileri ile kullanılan ASCII dize değişmez değerleri aynı kaçış sıraları Unicode kaçış sıraları dışında Unicode dizeleri olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="bac2a-145">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a><span data-ttu-id="bac2a-146">Dize İşleçleri</span><span class="sxs-lookup"><span data-stu-id="bac2a-146">String Operators</span></span>
<span data-ttu-id="bac2a-147">Dizeyi birleştirmek için iki yolu vardır: kullanarak `+` işleci veya kullanarak `^` işleci.</span><span class="sxs-lookup"><span data-stu-id="bac2a-147">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="bac2a-148">`+` İşleci .NET Framework dize özellikleri işleme ile uyumluluk korur.</span><span class="sxs-lookup"><span data-stu-id="bac2a-148">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="bac2a-149">Aşağıdaki örnek, dize birleştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bac2a-149">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a><span data-ttu-id="bac2a-150">String sınıfı</span><span class="sxs-lookup"><span data-stu-id="bac2a-150">String Class</span></span>
<span data-ttu-id="bac2a-151">F # dize türü gerçekte bir .NET Framework olduğundan `System.String` türü, tüm `System.String` üyeleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bac2a-151">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="bac2a-152">Bu içerir `+` dizeyi birleştirmek için kullanılan işleci `Length` özelliği ve `Chars` özelliği dize Unicode karakter dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="bac2a-152">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="bac2a-153">Dizeleri hakkında daha fazla bilgi için bkz: `System.String`.</span><span class="sxs-lookup"><span data-stu-id="bac2a-153">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="bac2a-154">Kullanarak `Chars` özelliği `System.String`, aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dizedeki karakterleri tek tek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bac2a-154">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a><span data-ttu-id="bac2a-155">String modülü</span><span class="sxs-lookup"><span data-stu-id="bac2a-155">String Module</span></span>
<span data-ttu-id="bac2a-156">Dize işleme için ek işlevler dahil `String` modülünde `FSharp.Core` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bac2a-156">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="bac2a-157">Daha fazla bilgi için bkz: [Core.String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="bac2a-157">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="bac2a-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bac2a-158">See Also</span></span>
[<span data-ttu-id="bac2a-159">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="bac2a-159">F# Language Reference</span></span>](index.md)

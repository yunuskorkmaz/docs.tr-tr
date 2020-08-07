---
title: Değişmez Değerler
description: 'F # programlama dilindeki değişmez türler hakkında bilgi edinin.'
ms.date: 06/28/2019
ms.openlocfilehash: 98d609a1cf0beb00c0dd4d45ea343aaa2280b62e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855029"
---
# <a name="literals"></a><span data-ttu-id="04665-103">Değişmez Değerler</span><span class="sxs-lookup"><span data-stu-id="04665-103">Literals</span></span>

<span data-ttu-id="04665-104">Bu makale, F # içinde bir sabit değerin türünü nasıl belirtmeyle ilgili bir tablo sağlar.</span><span class="sxs-lookup"><span data-stu-id="04665-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

> [!NOTE]
> <span data-ttu-id="04665-105">F # için docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="04665-105">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="04665-106">Bozuk bağlantılarla karşılaşırsanız, bunun yerine [F # Çekirdek Kitaplığı belgelerine](https://fsharp.github.io/fsharp-core-docs/) başvurun.</span><span class="sxs-lookup"><span data-stu-id="04665-106">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="literal-types"></a><span data-ttu-id="04665-107">Değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="04665-107">Literal types</span></span>

<span data-ttu-id="04665-108">Aşağıdaki tabloda, F # içinde değişmez türler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="04665-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="04665-109">Onaltılı gösterimdeki basamakları temsil eden karakterler büyük/küçük harfe duyarlı değildir; türü tanımlayan karakterler büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="04665-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="04665-110">Tür</span><span class="sxs-lookup"><span data-stu-id="04665-110">Type</span></span>|<span data-ttu-id="04665-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04665-111">Description</span></span>|<span data-ttu-id="04665-112">Sonek veya ön ek</span><span class="sxs-lookup"><span data-stu-id="04665-112">Suffix or prefix</span></span>|<span data-ttu-id="04665-113">Örnekler</span><span class="sxs-lookup"><span data-stu-id="04665-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="04665-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="04665-114">sbyte</span></span>|<span data-ttu-id="04665-115">imzalanan 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="04665-115">signed 8-bit integer</span></span>|<span data-ttu-id="04665-116">y</span><span class="sxs-lookup"><span data-stu-id="04665-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="04665-117">byte</span><span class="sxs-lookup"><span data-stu-id="04665-117">byte</span></span>|<span data-ttu-id="04665-118">işaretsiz 8 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="04665-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="04665-119">uy</span><span class="sxs-lookup"><span data-stu-id="04665-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="04665-120">Int16</span><span class="sxs-lookup"><span data-stu-id="04665-120">int16</span></span>|<span data-ttu-id="04665-121">imzalanan 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="04665-121">signed 16-bit integer</span></span>|<span data-ttu-id="04665-122">s</span><span class="sxs-lookup"><span data-stu-id="04665-122">s</span></span>|`86s`|
|<span data-ttu-id="04665-123">Int16</span><span class="sxs-lookup"><span data-stu-id="04665-123">uint16</span></span>|<span data-ttu-id="04665-124">işaretsiz 16 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="04665-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="04665-125">ABD</span><span class="sxs-lookup"><span data-stu-id="04665-125">us</span></span>|`86us`|
|<span data-ttu-id="04665-126">int</span><span class="sxs-lookup"><span data-stu-id="04665-126">int</span></span><br /><br /><span data-ttu-id="04665-127">Int32</span><span class="sxs-lookup"><span data-stu-id="04665-127">int32</span></span>|<span data-ttu-id="04665-128">imzalanan 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="04665-128">signed 32-bit integer</span></span>|<span data-ttu-id="04665-129">l veya hiçbiri</span><span class="sxs-lookup"><span data-stu-id="04665-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="04665-130">uint</span><span class="sxs-lookup"><span data-stu-id="04665-130">uint</span></span><br /><br /><span data-ttu-id="04665-131">Int32</span><span class="sxs-lookup"><span data-stu-id="04665-131">uint32</span></span>|<span data-ttu-id="04665-132">işaretsiz 32 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="04665-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="04665-133">u veya UL</span><span class="sxs-lookup"><span data-stu-id="04665-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="04665-134">nativeint</span><span class="sxs-lookup"><span data-stu-id="04665-134">nativeint</span></span>|<span data-ttu-id="04665-135">doğal olarak imzalanan bir sayının yerel işaretçisi</span><span class="sxs-lookup"><span data-stu-id="04665-135">native pointer to a signed natural number</span></span>|<span data-ttu-id="04665-136">n</span><span class="sxs-lookup"><span data-stu-id="04665-136">n</span></span>|`123n`|
|<span data-ttu-id="04665-137">unativeint</span><span class="sxs-lookup"><span data-stu-id="04665-137">unativeint</span></span>|<span data-ttu-id="04665-138">işaretsiz doğal sayı olarak yerel işaretçi</span><span class="sxs-lookup"><span data-stu-id="04665-138">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="04665-139">alma</span><span class="sxs-lookup"><span data-stu-id="04665-139">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="04665-140">tutulamaz</span><span class="sxs-lookup"><span data-stu-id="04665-140">int64</span></span>|<span data-ttu-id="04665-141">imzalanan 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="04665-141">signed 64-bit integer</span></span>|<span data-ttu-id="04665-142">L</span><span class="sxs-lookup"><span data-stu-id="04665-142">L</span></span>|`86L`|
|<span data-ttu-id="04665-143">Int64</span><span class="sxs-lookup"><span data-stu-id="04665-143">uint64</span></span>|<span data-ttu-id="04665-144">işaretsiz 64 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="04665-144">unsigned 64-bit natural number</span></span>|<span data-ttu-id="04665-145">UL</span><span class="sxs-lookup"><span data-stu-id="04665-145">UL</span></span>|`86UL`|
|<span data-ttu-id="04665-146">Single, float32</span><span class="sxs-lookup"><span data-stu-id="04665-146">single, float32</span></span>|<span data-ttu-id="04665-147">32-bit kayan noktalı sayı</span><span class="sxs-lookup"><span data-stu-id="04665-147">32-bit floating point number</span></span>|<span data-ttu-id="04665-148">F veya f</span><span class="sxs-lookup"><span data-stu-id="04665-148">F or f</span></span>|<span data-ttu-id="04665-149">`4.14F` veya `4.14f`</span><span class="sxs-lookup"><span data-stu-id="04665-149">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="04665-150">LF</span><span class="sxs-lookup"><span data-stu-id="04665-150">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="04665-151">float Çift</span><span class="sxs-lookup"><span data-stu-id="04665-151">float; double</span></span>|<span data-ttu-id="04665-152">64-bit kayan noktalı sayı</span><span class="sxs-lookup"><span data-stu-id="04665-152">64-bit floating point number</span></span>|<span data-ttu-id="04665-153">yok</span><span class="sxs-lookup"><span data-stu-id="04665-153">none</span></span>|<span data-ttu-id="04665-154">`4.14`or `2.3E+32` veya`2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="04665-154">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="04665-155">LF</span><span class="sxs-lookup"><span data-stu-id="04665-155">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="04665-156">bigint</span><span class="sxs-lookup"><span data-stu-id="04665-156">bigint</span></span>|<span data-ttu-id="04665-157">tamsayı, 64 bitlik gösterimiyle sınırlı değildir</span><span class="sxs-lookup"><span data-stu-id="04665-157">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="04665-158">I</span><span class="sxs-lookup"><span data-stu-id="04665-158">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="04665-159">decimal</span><span class="sxs-lookup"><span data-stu-id="04665-159">decimal</span></span>|<span data-ttu-id="04665-160">sabit bir nokta veya Rational numarası olarak temsil edilen kesirli sayı</span><span class="sxs-lookup"><span data-stu-id="04665-160">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="04665-161">A veya d</span><span class="sxs-lookup"><span data-stu-id="04665-161">M or m</span></span>|<span data-ttu-id="04665-162">`0.7833M` veya `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="04665-162">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="04665-163">Char</span><span class="sxs-lookup"><span data-stu-id="04665-163">Char</span></span>|<span data-ttu-id="04665-164">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="04665-164">Unicode character</span></span>|<span data-ttu-id="04665-165">yok</span><span class="sxs-lookup"><span data-stu-id="04665-165">none</span></span>|<span data-ttu-id="04665-166">`'a'` veya `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="04665-166">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="04665-167">Dize</span><span class="sxs-lookup"><span data-stu-id="04665-167">String</span></span>|<span data-ttu-id="04665-168">Unicode dizesi</span><span class="sxs-lookup"><span data-stu-id="04665-168">Unicode string</span></span>|<span data-ttu-id="04665-169">yok</span><span class="sxs-lookup"><span data-stu-id="04665-169">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="04665-170">veya</span><span class="sxs-lookup"><span data-stu-id="04665-170">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="04665-171">veya</span><span class="sxs-lookup"><span data-stu-id="04665-171">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="04665-172">veya</span><span class="sxs-lookup"><span data-stu-id="04665-172">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="04665-173">Ayrıca bkz. [dizeler](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="04665-173">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="04665-174">byte</span><span class="sxs-lookup"><span data-stu-id="04665-174">byte</span></span>|<span data-ttu-id="04665-175">ASCII karakteri</span><span class="sxs-lookup"><span data-stu-id="04665-175">ASCII character</span></span>|<span data-ttu-id="04665-176">B</span><span class="sxs-lookup"><span data-stu-id="04665-176">B</span></span>|`'a'B`|
|<span data-ttu-id="04665-177">Byte []</span><span class="sxs-lookup"><span data-stu-id="04665-177">byte[]</span></span>|<span data-ttu-id="04665-178">ASCII dizesi</span><span class="sxs-lookup"><span data-stu-id="04665-178">ASCII string</span></span>|<span data-ttu-id="04665-179">B</span><span class="sxs-lookup"><span data-stu-id="04665-179">B</span></span>|`"text"B`|
|<span data-ttu-id="04665-180">Dize veya Byte []</span><span class="sxs-lookup"><span data-stu-id="04665-180">String or byte[]</span></span>|<span data-ttu-id="04665-181">Tam dize</span><span class="sxs-lookup"><span data-stu-id="04665-181">verbatim string</span></span>|<span data-ttu-id="04665-182">@ ön eki</span><span class="sxs-lookup"><span data-stu-id="04665-182">@ prefix</span></span>|<span data-ttu-id="04665-183">`@"\\server\share"`Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="04665-183">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="04665-184">`@"\\server\share"B`ASCII</span><span class="sxs-lookup"><span data-stu-id="04665-184">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="04665-185">Adlandırılmış sabit değerler</span><span class="sxs-lookup"><span data-stu-id="04665-185">Named literals</span></span>

<span data-ttu-id="04665-186">Sabitler olması amaçlanan değerler [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliğiyle işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="04665-186">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="04665-187">Bu öznitelik, bir değerin bir sabit olarak derlenmesine neden olan etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="04665-187">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="04665-188">Desenler eşleşen ifadelerde, küçük harfli karakterlerle başlayan tanımlayıcılar her zaman değişmez değer yerine, her zaman bağlanacak değişkenler olarak değerlendirilir. bu nedenle, sabit değerleri tanımlarken genellikle ilk büyük harfleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="04665-188">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a><span data-ttu-id="04665-189">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04665-189">Remarks</span></span>

<span data-ttu-id="04665-190">Unicode dizeleri, ardından, `\u` `\U` herhangi bir Unicode kod noktasını temsil eden 32 bitlik bir onaltılık kod ile bunu kullanarak belirtebileceğiniz bir 16 bit onaltılı kod (0000-ffff) veya UTF-32 kodlamalarının ardından kullanarak belirtebileceğiniz açık kodlamalar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="04665-190">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="04665-191">Dışındaki diğer bit düzeyinde işleçlerin kullanımına `|||` izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="04665-191">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="04665-192">Diğer tabandaki tamsayılar</span><span class="sxs-lookup"><span data-stu-id="04665-192">Integers in other bases</span></span>

<span data-ttu-id="04665-193">İmzalanan 32 bit tamsayılar Ayrıca `0x` , `0o` sırasıyla bir veya öneki kullanılarak onaltılık, sekizlik veya ikili olarak belirtilebilir `0b` .</span><span class="sxs-lookup"><span data-stu-id="04665-193">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="04665-194">Sayısal sabit değerlerde alt çizgiler</span><span class="sxs-lookup"><span data-stu-id="04665-194">Underscores in numeric literals</span></span>

<span data-ttu-id="04665-195">Rakamları alt çizgi karakteri () ile ayırabilirsiniz `_` .</span><span class="sxs-lookup"><span data-stu-id="04665-195">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="04665-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04665-196">See also</span></span>

- [<span data-ttu-id="04665-197">Core. LiteralAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="04665-197">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

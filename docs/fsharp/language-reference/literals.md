---
title: Sabit değerler
description: F# Programlama dilindeki değişmez türler hakkında bilgi edinin.
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041039"
---
# <a name="literals"></a><span data-ttu-id="a1629-103">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="a1629-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="a1629-104">Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürecektir (şimdilik).</span><span class="sxs-lookup"><span data-stu-id="a1629-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="a1629-105">Bu konu, içinde F#bir sabit değerin türünü nasıl belirtmeyle ilgili bir tablo sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1629-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="a1629-106">Değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="a1629-106">Literal Types</span></span>

<span data-ttu-id="a1629-107">Aşağıdaki tabloda, içindeki F#değişmez türler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a1629-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="a1629-108">Onaltılı gösterimdeki basamakları temsil eden karakterler büyük/küçük harfe duyarlı değildir; türü tanımlayan karakterler büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a1629-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="a1629-109">Tür</span><span class="sxs-lookup"><span data-stu-id="a1629-109">Type</span></span>|<span data-ttu-id="a1629-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1629-110">Description</span></span>|<span data-ttu-id="a1629-111">Sonek veya ön ek</span><span class="sxs-lookup"><span data-stu-id="a1629-111">Suffix or prefix</span></span>|<span data-ttu-id="a1629-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a1629-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="a1629-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="a1629-113">sbyte</span></span>|<span data-ttu-id="a1629-114">İmzalanan 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="a1629-114">signed 8-bit integer</span></span>|<span data-ttu-id="a1629-115">y</span><span class="sxs-lookup"><span data-stu-id="a1629-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="a1629-116">byte</span><span class="sxs-lookup"><span data-stu-id="a1629-116">byte</span></span>|<span data-ttu-id="a1629-117">işaretsiz 8 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="a1629-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="a1629-118">uy</span><span class="sxs-lookup"><span data-stu-id="a1629-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="a1629-119">Int16</span><span class="sxs-lookup"><span data-stu-id="a1629-119">int16</span></span>|<span data-ttu-id="a1629-120">İmzalanan 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="a1629-120">signed 16-bit integer</span></span>|<span data-ttu-id="a1629-121">s</span><span class="sxs-lookup"><span data-stu-id="a1629-121">s</span></span>|`86s`|
|<span data-ttu-id="a1629-122">Int16</span><span class="sxs-lookup"><span data-stu-id="a1629-122">uint16</span></span>|<span data-ttu-id="a1629-123">işaretsiz 16 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="a1629-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="a1629-124">ABD</span><span class="sxs-lookup"><span data-stu-id="a1629-124">us</span></span>|`86us`|
|<span data-ttu-id="a1629-125">int</span><span class="sxs-lookup"><span data-stu-id="a1629-125">int</span></span><br /><br /><span data-ttu-id="a1629-126">Int32</span><span class="sxs-lookup"><span data-stu-id="a1629-126">int32</span></span>|<span data-ttu-id="a1629-127">İmzalanan 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="a1629-127">signed 32-bit integer</span></span>|<span data-ttu-id="a1629-128">l veya hiçbiri</span><span class="sxs-lookup"><span data-stu-id="a1629-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="a1629-129">uint</span><span class="sxs-lookup"><span data-stu-id="a1629-129">uint</span></span><br /><br /><span data-ttu-id="a1629-130">Int32</span><span class="sxs-lookup"><span data-stu-id="a1629-130">uint32</span></span>|<span data-ttu-id="a1629-131">işaretsiz 32 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="a1629-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="a1629-132">u veya UL</span><span class="sxs-lookup"><span data-stu-id="a1629-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="a1629-133">nativeint</span><span class="sxs-lookup"><span data-stu-id="a1629-133">nativeint</span></span>|<span data-ttu-id="a1629-134">doğal olarak imzalanan bir sayının yerel işaretçisi</span><span class="sxs-lookup"><span data-stu-id="a1629-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="a1629-135">n</span><span class="sxs-lookup"><span data-stu-id="a1629-135">n</span></span>|`123n`|
|<span data-ttu-id="a1629-136">unativeint</span><span class="sxs-lookup"><span data-stu-id="a1629-136">unativeint</span></span>|<span data-ttu-id="a1629-137">işaretsiz doğal sayı olarak yerel işaretçi</span><span class="sxs-lookup"><span data-stu-id="a1629-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="a1629-138">alma</span><span class="sxs-lookup"><span data-stu-id="a1629-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="a1629-139">Tutulamaz</span><span class="sxs-lookup"><span data-stu-id="a1629-139">int64</span></span>|<span data-ttu-id="a1629-140">İmzalanan 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="a1629-140">signed 64-bit integer</span></span>|<span data-ttu-id="a1629-141">L</span><span class="sxs-lookup"><span data-stu-id="a1629-141">L</span></span>|`86L`|
|<span data-ttu-id="a1629-142">Int64</span><span class="sxs-lookup"><span data-stu-id="a1629-142">uint64</span></span>|<span data-ttu-id="a1629-143">işaretsiz 64 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="a1629-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="a1629-144">UL</span><span class="sxs-lookup"><span data-stu-id="a1629-144">UL</span></span>|`86UL`|
|<span data-ttu-id="a1629-145">Single, float32</span><span class="sxs-lookup"><span data-stu-id="a1629-145">single, float32</span></span>|<span data-ttu-id="a1629-146">32-bit kayan noktalı sayı</span><span class="sxs-lookup"><span data-stu-id="a1629-146">32-bit floating point number</span></span>|<span data-ttu-id="a1629-147">F veya f</span><span class="sxs-lookup"><span data-stu-id="a1629-147">F or f</span></span>|<span data-ttu-id="a1629-148">`4.14F` veya `4.14f`</span><span class="sxs-lookup"><span data-stu-id="a1629-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="a1629-149">LF</span><span class="sxs-lookup"><span data-stu-id="a1629-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="a1629-150">float Çift</span><span class="sxs-lookup"><span data-stu-id="a1629-150">float; double</span></span>|<span data-ttu-id="a1629-151">64-bit kayan noktalı sayı</span><span class="sxs-lookup"><span data-stu-id="a1629-151">64-bit floating point number</span></span>|<span data-ttu-id="a1629-152">yok</span><span class="sxs-lookup"><span data-stu-id="a1629-152">none</span></span>|<span data-ttu-id="a1629-153">`4.14` veya `2.3E+32` veya `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="a1629-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="a1629-154">LF</span><span class="sxs-lookup"><span data-stu-id="a1629-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="a1629-155">bigint</span><span class="sxs-lookup"><span data-stu-id="a1629-155">bigint</span></span>|<span data-ttu-id="a1629-156">tamsayı, 64 bitlik gösterimiyle sınırlı değildir</span><span class="sxs-lookup"><span data-stu-id="a1629-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="a1629-157">I</span><span class="sxs-lookup"><span data-stu-id="a1629-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="a1629-158">decimal</span><span class="sxs-lookup"><span data-stu-id="a1629-158">decimal</span></span>|<span data-ttu-id="a1629-159">sabit bir nokta veya Rational numarası olarak temsil edilen kesirli sayı</span><span class="sxs-lookup"><span data-stu-id="a1629-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="a1629-160">A veya d</span><span class="sxs-lookup"><span data-stu-id="a1629-160">M or m</span></span>|<span data-ttu-id="a1629-161">`0.7833M` veya `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="a1629-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="a1629-162">Char</span><span class="sxs-lookup"><span data-stu-id="a1629-162">Char</span></span>|<span data-ttu-id="a1629-163">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="a1629-163">Unicode character</span></span>|<span data-ttu-id="a1629-164">yok</span><span class="sxs-lookup"><span data-stu-id="a1629-164">none</span></span>|<span data-ttu-id="a1629-165">`'a'` veya `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="a1629-165">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="a1629-166">Dize</span><span class="sxs-lookup"><span data-stu-id="a1629-166">String</span></span>|<span data-ttu-id="a1629-167">Unicode dizesi</span><span class="sxs-lookup"><span data-stu-id="a1629-167">Unicode string</span></span>|<span data-ttu-id="a1629-168">yok</span><span class="sxs-lookup"><span data-stu-id="a1629-168">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="a1629-169">veya</span><span class="sxs-lookup"><span data-stu-id="a1629-169">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="a1629-170">veya</span><span class="sxs-lookup"><span data-stu-id="a1629-170">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="a1629-171">veya</span><span class="sxs-lookup"><span data-stu-id="a1629-171">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="a1629-172">Ayrıca bkz. [dizeler](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="a1629-172">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="a1629-173">byte</span><span class="sxs-lookup"><span data-stu-id="a1629-173">byte</span></span>|<span data-ttu-id="a1629-174">ASCII karakteri</span><span class="sxs-lookup"><span data-stu-id="a1629-174">ASCII character</span></span>|<span data-ttu-id="a1629-175">B</span><span class="sxs-lookup"><span data-stu-id="a1629-175">B</span></span>|`'a'B`|
|<span data-ttu-id="a1629-176">Byte []</span><span class="sxs-lookup"><span data-stu-id="a1629-176">byte[]</span></span>|<span data-ttu-id="a1629-177">ASCII dizesi</span><span class="sxs-lookup"><span data-stu-id="a1629-177">ASCII string</span></span>|<span data-ttu-id="a1629-178">B</span><span class="sxs-lookup"><span data-stu-id="a1629-178">B</span></span>|`"text"B`|
|<span data-ttu-id="a1629-179">Dize veya Byte []</span><span class="sxs-lookup"><span data-stu-id="a1629-179">String or byte[]</span></span>|<span data-ttu-id="a1629-180">Tam dize</span><span class="sxs-lookup"><span data-stu-id="a1629-180">verbatim string</span></span>|<span data-ttu-id="a1629-181">@ ön eki</span><span class="sxs-lookup"><span data-stu-id="a1629-181">@ prefix</span></span>|<span data-ttu-id="a1629-182">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="a1629-182">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="a1629-183">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="a1629-183">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="a1629-184">Adlandırılmış sabit değerler</span><span class="sxs-lookup"><span data-stu-id="a1629-184">Named literals</span></span>

<span data-ttu-id="a1629-185">Sabitler olması amaçlanan değerler [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliğiyle işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a1629-185">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="a1629-186">Bu öznitelik, bir değerin bir sabit olarak derlenmesine neden olan etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a1629-186">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="a1629-187">Desenler eşleşen ifadelerde, küçük harfli karakterlerle başlayan tanımlayıcılar her zaman değişmez değer yerine, her zaman bağlanacak değişkenler olarak değerlendirilir. bu nedenle, sabit değerleri tanımlarken genellikle ilk büyük harfleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1629-187">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="a1629-188">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1629-188">Remarks</span></span>

<span data-ttu-id="a1629-189">Unicode dizeleri, `\u` ve ardından bir 16 bit onaltılı kod (0000-FFFF) veya UTF-32 kodlamalarının ardından, herhangi bir Unicode 'U temsil eden 32 bitlik bir onaltılık kod tarafından ve `\U` kullanarak belirtebileceğiniz açık kodlamalar içerebilir kod noktası (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="a1629-189">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="a1629-190">`|||` dışındaki diğer bit düzeyinde işleçlerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="a1629-190">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="a1629-191">Diğer tabandaki tamsayılar</span><span class="sxs-lookup"><span data-stu-id="a1629-191">Integers in other bases</span></span>

<span data-ttu-id="a1629-192">İmzalı 32 bitlik tamsayılar, sırasıyla `0x``0o` veya `0b` ön eki kullanılarak onaltılık, sekizlik veya ikili düzende de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1629-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="a1629-193">Sayısal sabit değerlerde alt çizgiler</span><span class="sxs-lookup"><span data-stu-id="a1629-193">Underscores in numeric literals</span></span>

<span data-ttu-id="a1629-194">Rakamları alt çizgi karakteri (`_`) ile ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1629-194">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="a1629-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1629-195">See also</span></span>

- [<span data-ttu-id="a1629-196">Core. LiteralAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="a1629-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

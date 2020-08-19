---
title: Değişmez Değerler
description: 'F # programlama dilindeki değişmez türler hakkında bilgi edinin.'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559160"
---
# <a name="literals"></a><span data-ttu-id="fc76f-103">Değişmez Değerler</span><span class="sxs-lookup"><span data-stu-id="fc76f-103">Literals</span></span>

<span data-ttu-id="fc76f-104">Bu makale, F # içinde bir sabit değerin türünü nasıl belirtmeyle ilgili bir tablo sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc76f-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="fc76f-105">Değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="fc76f-105">Literal types</span></span>

<span data-ttu-id="fc76f-106">Aşağıdaki tabloda, F # içinde değişmez türler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc76f-106">The following table shows the literal types in F#.</span></span> <span data-ttu-id="fc76f-107">Onaltılı gösterimdeki basamakları temsil eden karakterler büyük/küçük harfe duyarlı değildir; türü tanımlayan karakterler büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="fc76f-107">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="fc76f-108">Tür</span><span class="sxs-lookup"><span data-stu-id="fc76f-108">Type</span></span>|<span data-ttu-id="fc76f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc76f-109">Description</span></span>|<span data-ttu-id="fc76f-110">Sonek veya ön ek</span><span class="sxs-lookup"><span data-stu-id="fc76f-110">Suffix or prefix</span></span>|<span data-ttu-id="fc76f-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fc76f-111">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="fc76f-112">sbyte</span><span class="sxs-lookup"><span data-stu-id="fc76f-112">sbyte</span></span>|<span data-ttu-id="fc76f-113">imzalanan 8 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="fc76f-113">signed 8-bit integer</span></span>|<span data-ttu-id="fc76f-114">y</span><span class="sxs-lookup"><span data-stu-id="fc76f-114">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="fc76f-115">byte</span><span class="sxs-lookup"><span data-stu-id="fc76f-115">byte</span></span>|<span data-ttu-id="fc76f-116">işaretsiz 8 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="fc76f-116">unsigned 8-bit natural number</span></span>|<span data-ttu-id="fc76f-117">uy</span><span class="sxs-lookup"><span data-stu-id="fc76f-117">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="fc76f-118">Int16</span><span class="sxs-lookup"><span data-stu-id="fc76f-118">int16</span></span>|<span data-ttu-id="fc76f-119">imzalanan 16 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="fc76f-119">signed 16-bit integer</span></span>|<span data-ttu-id="fc76f-120">s</span><span class="sxs-lookup"><span data-stu-id="fc76f-120">s</span></span>|`86s`|
|<span data-ttu-id="fc76f-121">Int16</span><span class="sxs-lookup"><span data-stu-id="fc76f-121">uint16</span></span>|<span data-ttu-id="fc76f-122">işaretsiz 16 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="fc76f-122">unsigned 16-bit natural number</span></span>|<span data-ttu-id="fc76f-123">ABD</span><span class="sxs-lookup"><span data-stu-id="fc76f-123">us</span></span>|`86us`|
|<span data-ttu-id="fc76f-124">int</span><span class="sxs-lookup"><span data-stu-id="fc76f-124">int</span></span><br /><br /><span data-ttu-id="fc76f-125">Int32</span><span class="sxs-lookup"><span data-stu-id="fc76f-125">int32</span></span>|<span data-ttu-id="fc76f-126">imzalanan 32 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="fc76f-126">signed 32-bit integer</span></span>|<span data-ttu-id="fc76f-127">l veya hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fc76f-127">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="fc76f-128">uint</span><span class="sxs-lookup"><span data-stu-id="fc76f-128">uint</span></span><br /><br /><span data-ttu-id="fc76f-129">Int32</span><span class="sxs-lookup"><span data-stu-id="fc76f-129">uint32</span></span>|<span data-ttu-id="fc76f-130">işaretsiz 32 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="fc76f-130">unsigned 32-bit natural number</span></span>|<span data-ttu-id="fc76f-131">u veya UL</span><span class="sxs-lookup"><span data-stu-id="fc76f-131">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="fc76f-132">nativeint</span><span class="sxs-lookup"><span data-stu-id="fc76f-132">nativeint</span></span>|<span data-ttu-id="fc76f-133">doğal olarak imzalanan bir sayının yerel işaretçisi</span><span class="sxs-lookup"><span data-stu-id="fc76f-133">native pointer to a signed natural number</span></span>|<span data-ttu-id="fc76f-134">n</span><span class="sxs-lookup"><span data-stu-id="fc76f-134">n</span></span>|`123n`|
|<span data-ttu-id="fc76f-135">unativeint</span><span class="sxs-lookup"><span data-stu-id="fc76f-135">unativeint</span></span>|<span data-ttu-id="fc76f-136">işaretsiz doğal sayı olarak yerel işaretçi</span><span class="sxs-lookup"><span data-stu-id="fc76f-136">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="fc76f-137">alma</span><span class="sxs-lookup"><span data-stu-id="fc76f-137">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="fc76f-138">tutulamaz</span><span class="sxs-lookup"><span data-stu-id="fc76f-138">int64</span></span>|<span data-ttu-id="fc76f-139">imzalanan 64 bit tamsayı</span><span class="sxs-lookup"><span data-stu-id="fc76f-139">signed 64-bit integer</span></span>|<span data-ttu-id="fc76f-140">L</span><span class="sxs-lookup"><span data-stu-id="fc76f-140">L</span></span>|`86L`|
|<span data-ttu-id="fc76f-141">Int64</span><span class="sxs-lookup"><span data-stu-id="fc76f-141">uint64</span></span>|<span data-ttu-id="fc76f-142">işaretsiz 64 bit doğal numara</span><span class="sxs-lookup"><span data-stu-id="fc76f-142">unsigned 64-bit natural number</span></span>|<span data-ttu-id="fc76f-143">UL</span><span class="sxs-lookup"><span data-stu-id="fc76f-143">UL</span></span>|`86UL`|
|<span data-ttu-id="fc76f-144">Single, float32</span><span class="sxs-lookup"><span data-stu-id="fc76f-144">single, float32</span></span>|<span data-ttu-id="fc76f-145">32-bit kayan noktalı sayı</span><span class="sxs-lookup"><span data-stu-id="fc76f-145">32-bit floating point number</span></span>|<span data-ttu-id="fc76f-146">F veya f</span><span class="sxs-lookup"><span data-stu-id="fc76f-146">F or f</span></span>|<span data-ttu-id="fc76f-147">`4.14F` veya `4.14f`</span><span class="sxs-lookup"><span data-stu-id="fc76f-147">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="fc76f-148">LF</span><span class="sxs-lookup"><span data-stu-id="fc76f-148">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="fc76f-149">float Çift</span><span class="sxs-lookup"><span data-stu-id="fc76f-149">float; double</span></span>|<span data-ttu-id="fc76f-150">64-bit kayan noktalı sayı</span><span class="sxs-lookup"><span data-stu-id="fc76f-150">64-bit floating point number</span></span>|<span data-ttu-id="fc76f-151">yok</span><span class="sxs-lookup"><span data-stu-id="fc76f-151">none</span></span>|<span data-ttu-id="fc76f-152">`4.14` or `2.3E+32` veya `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="fc76f-152">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="fc76f-153">LF</span><span class="sxs-lookup"><span data-stu-id="fc76f-153">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="fc76f-154">bigint</span><span class="sxs-lookup"><span data-stu-id="fc76f-154">bigint</span></span>|<span data-ttu-id="fc76f-155">tamsayı, 64 bitlik gösterimiyle sınırlı değildir</span><span class="sxs-lookup"><span data-stu-id="fc76f-155">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="fc76f-156">I</span><span class="sxs-lookup"><span data-stu-id="fc76f-156">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="fc76f-157">decimal</span><span class="sxs-lookup"><span data-stu-id="fc76f-157">decimal</span></span>|<span data-ttu-id="fc76f-158">sabit bir nokta veya Rational numarası olarak temsil edilen kesirli sayı</span><span class="sxs-lookup"><span data-stu-id="fc76f-158">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="fc76f-159">A veya d</span><span class="sxs-lookup"><span data-stu-id="fc76f-159">M or m</span></span>|<span data-ttu-id="fc76f-160">`0.7833M` veya `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="fc76f-160">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="fc76f-161">Char</span><span class="sxs-lookup"><span data-stu-id="fc76f-161">Char</span></span>|<span data-ttu-id="fc76f-162">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="fc76f-162">Unicode character</span></span>|<span data-ttu-id="fc76f-163">yok</span><span class="sxs-lookup"><span data-stu-id="fc76f-163">none</span></span>|<span data-ttu-id="fc76f-164">`'a'` veya `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="fc76f-164">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="fc76f-165">Dize</span><span class="sxs-lookup"><span data-stu-id="fc76f-165">String</span></span>|<span data-ttu-id="fc76f-166">Unicode dizesi</span><span class="sxs-lookup"><span data-stu-id="fc76f-166">Unicode string</span></span>|<span data-ttu-id="fc76f-167">yok</span><span class="sxs-lookup"><span data-stu-id="fc76f-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="fc76f-168">veya</span><span class="sxs-lookup"><span data-stu-id="fc76f-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="fc76f-169">veya</span><span class="sxs-lookup"><span data-stu-id="fc76f-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="fc76f-170">veya</span><span class="sxs-lookup"><span data-stu-id="fc76f-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="fc76f-171">Ayrıca bkz. [dizeler](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="fc76f-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="fc76f-172">byte</span><span class="sxs-lookup"><span data-stu-id="fc76f-172">byte</span></span>|<span data-ttu-id="fc76f-173">ASCII karakteri</span><span class="sxs-lookup"><span data-stu-id="fc76f-173">ASCII character</span></span>|<span data-ttu-id="fc76f-174">B</span><span class="sxs-lookup"><span data-stu-id="fc76f-174">B</span></span>|`'a'B`|
|<span data-ttu-id="fc76f-175">Byte []</span><span class="sxs-lookup"><span data-stu-id="fc76f-175">byte[]</span></span>|<span data-ttu-id="fc76f-176">ASCII dizesi</span><span class="sxs-lookup"><span data-stu-id="fc76f-176">ASCII string</span></span>|<span data-ttu-id="fc76f-177">B</span><span class="sxs-lookup"><span data-stu-id="fc76f-177">B</span></span>|`"text"B`|
|<span data-ttu-id="fc76f-178">Dize veya Byte []</span><span class="sxs-lookup"><span data-stu-id="fc76f-178">String or byte[]</span></span>|<span data-ttu-id="fc76f-179">Tam dize</span><span class="sxs-lookup"><span data-stu-id="fc76f-179">verbatim string</span></span>|<span data-ttu-id="fc76f-180">@ ön eki</span><span class="sxs-lookup"><span data-stu-id="fc76f-180">@ prefix</span></span>|<span data-ttu-id="fc76f-181">`@"\\server\share"` Kodlamaları</span><span class="sxs-lookup"><span data-stu-id="fc76f-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="fc76f-182">`@"\\server\share"B` ASCII</span><span class="sxs-lookup"><span data-stu-id="fc76f-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="fc76f-183">Adlandırılmış sabit değerler</span><span class="sxs-lookup"><span data-stu-id="fc76f-183">Named literals</span></span>

<span data-ttu-id="fc76f-184">Sabitler olması amaçlanan değerler [değişmez değer](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) özniteliğiyle işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="fc76f-184">Values that are intended to be constants can be marked with the [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) attribute.</span></span> <span data-ttu-id="fc76f-185">Bu öznitelik, bir değerin bir sabit olarak derlenmesine neden olan etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fc76f-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="fc76f-186">Desenler eşleşen ifadelerde, küçük harfli karakterlerle başlayan tanımlayıcılar her zaman değişmez değer yerine, her zaman bağlanacak değişkenler olarak değerlendirilir. bu nedenle, sabit değerleri tanımlarken genellikle ilk büyük harfleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc76f-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="fc76f-187">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc76f-187">Remarks</span></span>

<span data-ttu-id="fc76f-188">Unicode dizeleri, ardından, `\u` `\U` herhangi bir Unicode kod noktasını temsil eden 32 bitlik bir onaltılık kod ile bunu kullanarak belirtebileceğiniz bir 16 bit onaltılı kod (0000-ffff) veya UTF-32 kodlamalarının ardından kullanarak belirtebileceğiniz açık kodlamalar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fc76f-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="fc76f-189">Dışındaki diğer bit düzeyinde işleçlerin kullanımına `|||` izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="fc76f-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="fc76f-190">Diğer tabandaki tamsayılar</span><span class="sxs-lookup"><span data-stu-id="fc76f-190">Integers in other bases</span></span>

<span data-ttu-id="fc76f-191">İmzalanan 32 bit tamsayılar Ayrıca `0x` , `0o` sırasıyla bir veya öneki kullanılarak onaltılık, sekizlik veya ikili olarak belirtilebilir `0b` .</span><span class="sxs-lookup"><span data-stu-id="fc76f-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="fc76f-192">Sayısal sabit değerlerde alt çizgiler</span><span class="sxs-lookup"><span data-stu-id="fc76f-192">Underscores in numeric literals</span></span>

<span data-ttu-id="fc76f-193">Rakamları alt çizgi karakteri () ile ayırabilirsiniz `_` .</span><span class="sxs-lookup"><span data-stu-id="fc76f-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

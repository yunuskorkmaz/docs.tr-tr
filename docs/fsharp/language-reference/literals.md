---
title: Değişmez Değerler (F#)
description: 'F # programlama dili değişmez değer türleri hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 961d6a10122c5d5c691d394efa8d2b7b31a80453
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="literals"></a><span data-ttu-id="03d96-103">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="03d96-103">Literals</span></span>

> [!NOTE]
<span data-ttu-id="03d96-104">Bu makalede API başvuru bağlantılar (şimdilik) için MSDN sürer.</span><span class="sxs-lookup"><span data-stu-id="03d96-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="03d96-105">Bu konu, bir hazır değer türü F #'ta belirtme gösteren bir tablo sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d96-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="03d96-106">Değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="03d96-106">Literal Types</span></span>
<span data-ttu-id="03d96-107">Değişmez değer türleri aşağıdaki tabloda F #'de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="03d96-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="03d96-108">Onaltılık gösterimde basamağı temsil karakterleri büyük küçük harfe duyarlı değildir; tür belirleme karakterleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="03d96-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="03d96-109">Tür</span><span class="sxs-lookup"><span data-stu-id="03d96-109">Type</span></span>|<span data-ttu-id="03d96-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03d96-110">Description</span></span>|<span data-ttu-id="03d96-111">Sonek veya öneki</span><span class="sxs-lookup"><span data-stu-id="03d96-111">Suffix or prefix</span></span>|<span data-ttu-id="03d96-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="03d96-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="03d96-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="03d96-113">sbyte</span></span>|<span data-ttu-id="03d96-114">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="03d96-114">signed 8-bit integer</span></span>|<span data-ttu-id="03d96-115">y</span><span class="sxs-lookup"><span data-stu-id="03d96-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="03d96-116">byte</span><span class="sxs-lookup"><span data-stu-id="03d96-116">byte</span></span>|<span data-ttu-id="03d96-117">İmzasız 8 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="03d96-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="03d96-118">Uy</span><span class="sxs-lookup"><span data-stu-id="03d96-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="03d96-119">Int16</span><span class="sxs-lookup"><span data-stu-id="03d96-119">int16</span></span>|<span data-ttu-id="03d96-120">İşaretli 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="03d96-120">signed 16-bit integer</span></span>|<span data-ttu-id="03d96-121">s</span><span class="sxs-lookup"><span data-stu-id="03d96-121">s</span></span>|`86s`|
|<span data-ttu-id="03d96-122">uint16</span><span class="sxs-lookup"><span data-stu-id="03d96-122">uint16</span></span>|<span data-ttu-id="03d96-123">İmzasız 16 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="03d96-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="03d96-124">Bize</span><span class="sxs-lookup"><span data-stu-id="03d96-124">us</span></span>|`86us`|
|<span data-ttu-id="03d96-125">int</span><span class="sxs-lookup"><span data-stu-id="03d96-125">int</span></span><br /><br /><span data-ttu-id="03d96-126">Int32</span><span class="sxs-lookup"><span data-stu-id="03d96-126">int32</span></span>|<span data-ttu-id="03d96-127">işaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="03d96-127">signed 32-bit integer</span></span>|<span data-ttu-id="03d96-128">m veya hiçbiri</span><span class="sxs-lookup"><span data-stu-id="03d96-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="03d96-129">uint</span><span class="sxs-lookup"><span data-stu-id="03d96-129">uint</span></span><br /><br /><span data-ttu-id="03d96-130">uint32</span><span class="sxs-lookup"><span data-stu-id="03d96-130">uint32</span></span>|<span data-ttu-id="03d96-131">İmzasız 32-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="03d96-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="03d96-132">u veya ul</span><span class="sxs-lookup"><span data-stu-id="03d96-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="03d96-133">unativeint</span><span class="sxs-lookup"><span data-stu-id="03d96-133">unativeint</span></span>|<span data-ttu-id="03d96-134">işaretsiz doğal sayı olarak yerel işaretçiden</span><span class="sxs-lookup"><span data-stu-id="03d96-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="03d96-135">kaldırma</span><span class="sxs-lookup"><span data-stu-id="03d96-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="03d96-136">Int64</span><span class="sxs-lookup"><span data-stu-id="03d96-136">int64</span></span>|<span data-ttu-id="03d96-137">işaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="03d96-137">signed 64-bit integer</span></span>|<span data-ttu-id="03d96-138">L</span><span class="sxs-lookup"><span data-stu-id="03d96-138">L</span></span>|`86L`|
|<span data-ttu-id="03d96-139">uint64</span><span class="sxs-lookup"><span data-stu-id="03d96-139">uint64</span></span>|<span data-ttu-id="03d96-140">İmzasız 64-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="03d96-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="03d96-141">UL</span><span class="sxs-lookup"><span data-stu-id="03d96-141">UL</span></span>|`86UL`|
|<span data-ttu-id="03d96-142">tek float32</span><span class="sxs-lookup"><span data-stu-id="03d96-142">single, float32</span></span>|<span data-ttu-id="03d96-143">32 bit kayan nokta sayısı</span><span class="sxs-lookup"><span data-stu-id="03d96-143">32-bit floating point number</span></span>|<span data-ttu-id="03d96-144">F veya f</span><span class="sxs-lookup"><span data-stu-id="03d96-144">F or f</span></span>|<span data-ttu-id="03d96-145">`4.14F` Veya `4.14f`</span><span class="sxs-lookup"><span data-stu-id="03d96-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="03d96-146">LF</span><span class="sxs-lookup"><span data-stu-id="03d96-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="03d96-147">float; çift</span><span class="sxs-lookup"><span data-stu-id="03d96-147">float; double</span></span>|<span data-ttu-id="03d96-148">64-bit kayan nokta sayısı</span><span class="sxs-lookup"><span data-stu-id="03d96-148">64-bit floating point number</span></span>|<span data-ttu-id="03d96-149">yok</span><span class="sxs-lookup"><span data-stu-id="03d96-149">none</span></span>|<span data-ttu-id="03d96-150">`4.14` veya `2.3E+32` veya `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="03d96-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="03d96-151">LF</span><span class="sxs-lookup"><span data-stu-id="03d96-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="03d96-152">bigint</span><span class="sxs-lookup"><span data-stu-id="03d96-152">bigint</span></span>|<span data-ttu-id="03d96-153">64-bit gösterimine bunlarla sınırlı olmamak tamsayı</span><span class="sxs-lookup"><span data-stu-id="03d96-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="03d96-154">I</span><span class="sxs-lookup"><span data-stu-id="03d96-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="03d96-155">decimal</span><span class="sxs-lookup"><span data-stu-id="03d96-155">decimal</span></span>|<span data-ttu-id="03d96-156">bir sabit bir nokta ya da rasyonel sayı olarak temsil kesirli numarası</span><span class="sxs-lookup"><span data-stu-id="03d96-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="03d96-157">M veya m</span><span class="sxs-lookup"><span data-stu-id="03d96-157">M or m</span></span>|<span data-ttu-id="03d96-158">`0.7833M` Veya `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="03d96-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="03d96-159">Char</span><span class="sxs-lookup"><span data-stu-id="03d96-159">Char</span></span>|<span data-ttu-id="03d96-160">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="03d96-160">Unicode character</span></span>|<span data-ttu-id="03d96-161">yok</span><span class="sxs-lookup"><span data-stu-id="03d96-161">none</span></span>|`'a'`|
|<span data-ttu-id="03d96-162">Dize</span><span class="sxs-lookup"><span data-stu-id="03d96-162">String</span></span>|<span data-ttu-id="03d96-163">UNICODE dizesi</span><span class="sxs-lookup"><span data-stu-id="03d96-163">Unicode string</span></span>|<span data-ttu-id="03d96-164">yok</span><span class="sxs-lookup"><span data-stu-id="03d96-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="03d96-165">veya</span><span class="sxs-lookup"><span data-stu-id="03d96-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="03d96-166">veya</span><span class="sxs-lookup"><span data-stu-id="03d96-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="03d96-167">veya</span><span class="sxs-lookup"><span data-stu-id="03d96-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="03d96-168">Ayrıca bkz. [dizeleri](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="03d96-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="03d96-169">byte</span><span class="sxs-lookup"><span data-stu-id="03d96-169">byte</span></span>|<span data-ttu-id="03d96-170">ASCII karakter</span><span class="sxs-lookup"><span data-stu-id="03d96-170">ASCII character</span></span>|<span data-ttu-id="03d96-171">B</span><span class="sxs-lookup"><span data-stu-id="03d96-171">B</span></span>|`'a'B`|
|<span data-ttu-id="03d96-172">Byte]</span><span class="sxs-lookup"><span data-stu-id="03d96-172">byte[]</span></span>|<span data-ttu-id="03d96-173">ASCII dizesi</span><span class="sxs-lookup"><span data-stu-id="03d96-173">ASCII string</span></span>|<span data-ttu-id="03d96-174">B</span><span class="sxs-lookup"><span data-stu-id="03d96-174">B</span></span>|`"text"B`|
|<span data-ttu-id="03d96-175">String veya byte]</span><span class="sxs-lookup"><span data-stu-id="03d96-175">String or byte[]</span></span>|<span data-ttu-id="03d96-176">harfi harfine dize</span><span class="sxs-lookup"><span data-stu-id="03d96-176">verbatim string</span></span>|<span data-ttu-id="03d96-177">@ öneki</span><span class="sxs-lookup"><span data-stu-id="03d96-177">@ prefix</span></span>|<span data-ttu-id="03d96-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="03d96-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="03d96-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="03d96-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="03d96-180">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03d96-180">Remarks</span></span>
<span data-ttu-id="03d96-181">Unicode dizelerini kullanarak belirtebilirsiniz açık Kodlamalar içerebilir `\u` bir 16 bit onaltılık kodu veya kullanarak belirtebilirsiniz UTF-32 kodlamaları arkasından `\U` bir Unicode temsil eden bir 32 bit onaltılık kodla ve ardından yedek çifti.</span><span class="sxs-lookup"><span data-stu-id="03d96-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="03d96-182">F # 3.1 itibariyle, kullandığınız `+` dize değişmez değerleri birleştirmek oturum açın.</span><span class="sxs-lookup"><span data-stu-id="03d96-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="03d96-183">Bit düzeyinde kullanabilirsiniz veya (`|||`) enum bayrakları birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="03d96-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="03d96-184">Örneğin, aşağıdaki kodu F # 3.1 uygundur:</span><span class="sxs-lookup"><span data-stu-id="03d96-184">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="03d96-185">Diğer bit düzeyinde işleçler kullanılmasına izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="03d96-185">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="03d96-186">Adlandırılmış değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="03d96-186">Named Literals</span></span>
<span data-ttu-id="03d96-187">Sabitler yönelik değerleri işaretlenir ile [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="03d96-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="03d96-188">Bu öznitelik, bir sabit değer olarak derlenmesi için bir değer neden etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="03d96-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="03d96-189">Eşleşen düzeninde küçük harf karakterler ile başlayan tanımlayıcıları her zaman bağlı olmasını değişkenleri olarak davranılır yerine değişmez değerler tanımlarken değişmez değerler, bu nedenle genellikle ilk harfler büyük harf kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03d96-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="03d96-190">Diğer tabanları tamsayılar</span><span class="sxs-lookup"><span data-stu-id="03d96-190">Integers In Other Bases</span></span>

<span data-ttu-id="03d96-191">İmzalı 32-bit tamsayı de belirtilebilir onaltılı, sekizli veya ikili kullanarak bir `0x`, `0o` veya `0b` sırasıyla önek.</span><span class="sxs-lookup"><span data-stu-id="03d96-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="03d96-192">Sayısal değişmez değerlerinde alt çizgiler</span><span class="sxs-lookup"><span data-stu-id="03d96-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="03d96-193">F # 4.1 ile başlayarak, basamak alt çizgi karakteriyle ayırabilirsiniz (`_`).</span><span class="sxs-lookup"><span data-stu-id="03d96-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="03d96-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03d96-194">See Also</span></span>

[<span data-ttu-id="03d96-195">Core.LiteralAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="03d96-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

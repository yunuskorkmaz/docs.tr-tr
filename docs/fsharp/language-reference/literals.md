---
title: "Değişmez Değerler (F#)"
description: "F # programlama dili değişmez değer türleri hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a><span data-ttu-id="6f729-104">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="6f729-104">Literals</span></span>

> [!NOTE]
<span data-ttu-id="6f729-105">Bu makalede API başvuru bağlantılar (şimdilik) için MSDN sürer.</span><span class="sxs-lookup"><span data-stu-id="6f729-105">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="6f729-106">Bu konu, bir hazır değer türü F #'ta belirtme gösteren bir tablo sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f729-106">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="6f729-107">Değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="6f729-107">Literal Types</span></span>
<span data-ttu-id="6f729-108">Değişmez değer türleri aşağıdaki tabloda F #'de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f729-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="6f729-109">Onaltılık gösterimde basamağı temsil karakterleri büyük küçük harfe duyarlı değildir; tür belirleme karakterleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="6f729-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="6f729-110">Tür</span><span class="sxs-lookup"><span data-stu-id="6f729-110">Type</span></span>|<span data-ttu-id="6f729-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f729-111">Description</span></span>|<span data-ttu-id="6f729-112">Sonek veya öneki</span><span class="sxs-lookup"><span data-stu-id="6f729-112">Suffix or prefix</span></span>|<span data-ttu-id="6f729-113">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6f729-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="6f729-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="6f729-114">sbyte</span></span>|<span data-ttu-id="6f729-115">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="6f729-115">signed 8-bit integer</span></span>|<span data-ttu-id="6f729-116">y</span><span class="sxs-lookup"><span data-stu-id="6f729-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="6f729-117">byte</span><span class="sxs-lookup"><span data-stu-id="6f729-117">byte</span></span>|<span data-ttu-id="6f729-118">İmzasız 8 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="6f729-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="6f729-119">Uy</span><span class="sxs-lookup"><span data-stu-id="6f729-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="6f729-120">Int16</span><span class="sxs-lookup"><span data-stu-id="6f729-120">int16</span></span>|<span data-ttu-id="6f729-121">İşaretli 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="6f729-121">signed 16-bit integer</span></span>|<span data-ttu-id="6f729-122">s</span><span class="sxs-lookup"><span data-stu-id="6f729-122">s</span></span>|`86s`|
|<span data-ttu-id="6f729-123">uint16</span><span class="sxs-lookup"><span data-stu-id="6f729-123">uint16</span></span>|<span data-ttu-id="6f729-124">İmzasız 16 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="6f729-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="6f729-125">Bize</span><span class="sxs-lookup"><span data-stu-id="6f729-125">us</span></span>|`86us`|
|<span data-ttu-id="6f729-126">int</span><span class="sxs-lookup"><span data-stu-id="6f729-126">int</span></span><br /><br /><span data-ttu-id="6f729-127">Int32</span><span class="sxs-lookup"><span data-stu-id="6f729-127">int32</span></span>|<span data-ttu-id="6f729-128">işaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="6f729-128">signed 32-bit integer</span></span>|<span data-ttu-id="6f729-129">m veya hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6f729-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="6f729-130">uint</span><span class="sxs-lookup"><span data-stu-id="6f729-130">uint</span></span><br /><br /><span data-ttu-id="6f729-131">uint32</span><span class="sxs-lookup"><span data-stu-id="6f729-131">uint32</span></span>|<span data-ttu-id="6f729-132">İmzasız 32-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="6f729-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="6f729-133">u veya ul</span><span class="sxs-lookup"><span data-stu-id="6f729-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="6f729-134">unativeint</span><span class="sxs-lookup"><span data-stu-id="6f729-134">unativeint</span></span>|<span data-ttu-id="6f729-135">işaretsiz doğal sayı olarak yerel işaretçiden</span><span class="sxs-lookup"><span data-stu-id="6f729-135">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="6f729-136">kaldırma</span><span class="sxs-lookup"><span data-stu-id="6f729-136">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="6f729-137">Int64</span><span class="sxs-lookup"><span data-stu-id="6f729-137">int64</span></span>|<span data-ttu-id="6f729-138">işaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="6f729-138">signed 64-bit integer</span></span>|<span data-ttu-id="6f729-139">L</span><span class="sxs-lookup"><span data-stu-id="6f729-139">L</span></span>|`86L`|
|<span data-ttu-id="6f729-140">uint64</span><span class="sxs-lookup"><span data-stu-id="6f729-140">uint64</span></span>|<span data-ttu-id="6f729-141">İmzasız 64-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="6f729-141">unsigned 64-bit natural number</span></span>|<span data-ttu-id="6f729-142">UL</span><span class="sxs-lookup"><span data-stu-id="6f729-142">UL</span></span>|`86UL`|
|<span data-ttu-id="6f729-143">tek float32</span><span class="sxs-lookup"><span data-stu-id="6f729-143">single, float32</span></span>|<span data-ttu-id="6f729-144">32 bit kayan nokta sayısı</span><span class="sxs-lookup"><span data-stu-id="6f729-144">32-bit floating point number</span></span>|<span data-ttu-id="6f729-145">F veya f</span><span class="sxs-lookup"><span data-stu-id="6f729-145">F or f</span></span>|<span data-ttu-id="6f729-146">`4.14F`veya`4.14f`</span><span class="sxs-lookup"><span data-stu-id="6f729-146">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="6f729-147">LF</span><span class="sxs-lookup"><span data-stu-id="6f729-147">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="6f729-148">float; çift</span><span class="sxs-lookup"><span data-stu-id="6f729-148">float; double</span></span>|<span data-ttu-id="6f729-149">64-bit kayan nokta sayısı</span><span class="sxs-lookup"><span data-stu-id="6f729-149">64-bit floating point number</span></span>|<span data-ttu-id="6f729-150">yok</span><span class="sxs-lookup"><span data-stu-id="6f729-150">none</span></span>|<span data-ttu-id="6f729-151">`4.14`veya `2.3E+32` veya`2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="6f729-151">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="6f729-152">LF</span><span class="sxs-lookup"><span data-stu-id="6f729-152">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="6f729-153">bigint</span><span class="sxs-lookup"><span data-stu-id="6f729-153">bigint</span></span>|<span data-ttu-id="6f729-154">64-bit gösterimine bunlarla sınırlı olmamak tamsayı</span><span class="sxs-lookup"><span data-stu-id="6f729-154">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="6f729-155">I</span><span class="sxs-lookup"><span data-stu-id="6f729-155">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="6f729-156">decimal</span><span class="sxs-lookup"><span data-stu-id="6f729-156">decimal</span></span>|<span data-ttu-id="6f729-157">bir sabit bir nokta ya da rasyonel sayı olarak temsil kesirli numarası</span><span class="sxs-lookup"><span data-stu-id="6f729-157">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="6f729-158">M veya m</span><span class="sxs-lookup"><span data-stu-id="6f729-158">M or m</span></span>|<span data-ttu-id="6f729-159">`0.7833M`veya`0.7833m`</span><span class="sxs-lookup"><span data-stu-id="6f729-159">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="6f729-160">Char</span><span class="sxs-lookup"><span data-stu-id="6f729-160">Char</span></span>|<span data-ttu-id="6f729-161">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="6f729-161">Unicode character</span></span>|<span data-ttu-id="6f729-162">yok</span><span class="sxs-lookup"><span data-stu-id="6f729-162">none</span></span>|`'a'`|
|<span data-ttu-id="6f729-163">Dize</span><span class="sxs-lookup"><span data-stu-id="6f729-163">String</span></span>|<span data-ttu-id="6f729-164">UNICODE dizesi</span><span class="sxs-lookup"><span data-stu-id="6f729-164">Unicode string</span></span>|<span data-ttu-id="6f729-165">yok</span><span class="sxs-lookup"><span data-stu-id="6f729-165">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="6f729-166">veya</span><span class="sxs-lookup"><span data-stu-id="6f729-166">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="6f729-167">veya</span><span class="sxs-lookup"><span data-stu-id="6f729-167">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="6f729-168">veya</span><span class="sxs-lookup"><span data-stu-id="6f729-168">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="6f729-169">Ayrıca bkz. [dizeleri](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="6f729-169">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="6f729-170">byte</span><span class="sxs-lookup"><span data-stu-id="6f729-170">byte</span></span>|<span data-ttu-id="6f729-171">ASCII karakter</span><span class="sxs-lookup"><span data-stu-id="6f729-171">ASCII character</span></span>|<span data-ttu-id="6f729-172">B</span><span class="sxs-lookup"><span data-stu-id="6f729-172">B</span></span>|`'a'B`|
|<span data-ttu-id="6f729-173">Byte]</span><span class="sxs-lookup"><span data-stu-id="6f729-173">byte[]</span></span>|<span data-ttu-id="6f729-174">ASCII dizesi</span><span class="sxs-lookup"><span data-stu-id="6f729-174">ASCII string</span></span>|<span data-ttu-id="6f729-175">B</span><span class="sxs-lookup"><span data-stu-id="6f729-175">B</span></span>|`"text"B`|
|<span data-ttu-id="6f729-176">String veya byte]</span><span class="sxs-lookup"><span data-stu-id="6f729-176">String or byte[]</span></span>|<span data-ttu-id="6f729-177">harfi harfine dize</span><span class="sxs-lookup"><span data-stu-id="6f729-177">verbatim string</span></span>|<span data-ttu-id="6f729-178">@ öneki</span><span class="sxs-lookup"><span data-stu-id="6f729-178">@ prefix</span></span>|<span data-ttu-id="6f729-179">`@"\\server\share"`(Unicode)</span><span class="sxs-lookup"><span data-stu-id="6f729-179">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="6f729-180">`@"\\server\share"B`(ASCII)</span><span class="sxs-lookup"><span data-stu-id="6f729-180">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="6f729-181">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f729-181">Remarks</span></span>
<span data-ttu-id="6f729-182">Unicode dizelerini kullanarak belirtebilirsiniz açık Kodlamalar içerebilir `\u` bir 16 bit onaltılık kodu veya kullanarak belirtebilirsiniz UTF-32 kodlamaları arkasından `\U` bir Unicode temsil eden bir 32 bit onaltılık kodla ve ardından yedek çifti.</span><span class="sxs-lookup"><span data-stu-id="6f729-182">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="6f729-183">F # 3.1 itibariyle, kullandığınız `+` dize değişmez değerleri birleştirmek oturum açın.</span><span class="sxs-lookup"><span data-stu-id="6f729-183">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="6f729-184">Bit düzeyinde kullanabilirsiniz veya (`|||`) enum bayrakları birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="6f729-184">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="6f729-185">Örneğin, aşağıdaki kodu F # 3.1 uygundur:</span><span class="sxs-lookup"><span data-stu-id="6f729-185">For example, the following code is legal in F# 3.1:</span></span>

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

<span data-ttu-id="6f729-186">Diğer bit düzeyinde işleçler kullanılmasına izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="6f729-186">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="6f729-187">Adlandırılmış değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="6f729-187">Named Literals</span></span>
<span data-ttu-id="6f729-188">Sabitler yönelik değerleri işaretlenir ile [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6f729-188">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="6f729-189">Bu öznitelik, bir sabit değer olarak derlenmesi için bir değer neden etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="6f729-189">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="6f729-190">Eşleşen düzeninde küçük harf karakterler ile başlayan tanımlayıcıları her zaman bağlı olmasını değişkenleri olarak davranılır yerine değişmez değerler tanımlarken değişmez değerler, bu nedenle genellikle ilk harfler büyük harf kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f729-190">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="6f729-191">Diğer tabanları tamsayılar</span><span class="sxs-lookup"><span data-stu-id="6f729-191">Integers In Other Bases</span></span>

<span data-ttu-id="6f729-192">İmzalı 32-bit tamsayı de belirtilebilir onaltılı, sekizli veya ikili kullanarak bir `0x`, `0o` veya `0b` sırasıyla önek.</span><span class="sxs-lookup"><span data-stu-id="6f729-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="6f729-193">Sayısal değişmez değerlerinde alt çizgiler</span><span class="sxs-lookup"><span data-stu-id="6f729-193">Underscores in Numeric Literals</span></span>

<span data-ttu-id="6f729-194">F # 4.1 ile başlayarak, basamak alt çizgi karakteriyle ayırabilirsiniz (`_`).</span><span class="sxs-lookup"><span data-stu-id="6f729-194">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="6f729-195">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f729-195">See Also</span></span>

[<span data-ttu-id="6f729-196">Core.LiteralAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="6f729-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

---
title: Değişmez Değerler (F#)
description: 'F # programlama dili değişmez değer türleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: f28ca0ae7a0b092bbc039d23625b883faffd241c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564345"
---
# <a name="literals"></a><span data-ttu-id="e4971-103">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="e4971-103">Literals</span></span>

> [!NOTE]
<span data-ttu-id="e4971-104">Bu makalede API başvuru bağlantılar (şimdilik) için MSDN sürer.</span><span class="sxs-lookup"><span data-stu-id="e4971-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="e4971-105">Bu konu, bir hazır değer türü F #'ta belirtme gösteren bir tablo sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4971-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="e4971-106">Değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="e4971-106">Literal Types</span></span>
<span data-ttu-id="e4971-107">Değişmez değer türleri aşağıdaki tabloda F #'de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e4971-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="e4971-108">Onaltılık gösterimde basamağı temsil karakterleri büyük küçük harfe duyarlı değildir; tür belirleme karakterleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4971-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="e4971-109">Tür</span><span class="sxs-lookup"><span data-stu-id="e4971-109">Type</span></span>|<span data-ttu-id="e4971-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4971-110">Description</span></span>|<span data-ttu-id="e4971-111">Sonek veya öneki</span><span class="sxs-lookup"><span data-stu-id="e4971-111">Suffix or prefix</span></span>|<span data-ttu-id="e4971-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e4971-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="e4971-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="e4971-113">sbyte</span></span>|<span data-ttu-id="e4971-114">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e4971-114">signed 8-bit integer</span></span>|<span data-ttu-id="e4971-115">y</span><span class="sxs-lookup"><span data-stu-id="e4971-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="e4971-116">byte</span><span class="sxs-lookup"><span data-stu-id="e4971-116">byte</span></span>|<span data-ttu-id="e4971-117">İmzasız 8 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="e4971-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="e4971-118">Uy</span><span class="sxs-lookup"><span data-stu-id="e4971-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="e4971-119">Int16</span><span class="sxs-lookup"><span data-stu-id="e4971-119">int16</span></span>|<span data-ttu-id="e4971-120">İşaretli 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e4971-120">signed 16-bit integer</span></span>|<span data-ttu-id="e4971-121">s</span><span class="sxs-lookup"><span data-stu-id="e4971-121">s</span></span>|`86s`|
|<span data-ttu-id="e4971-122">uint16</span><span class="sxs-lookup"><span data-stu-id="e4971-122">uint16</span></span>|<span data-ttu-id="e4971-123">İmzasız 16 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="e4971-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="e4971-124">Bize</span><span class="sxs-lookup"><span data-stu-id="e4971-124">us</span></span>|`86us`|
|<span data-ttu-id="e4971-125">int</span><span class="sxs-lookup"><span data-stu-id="e4971-125">int</span></span><br /><br /><span data-ttu-id="e4971-126">Int32</span><span class="sxs-lookup"><span data-stu-id="e4971-126">int32</span></span>|<span data-ttu-id="e4971-127">işaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e4971-127">signed 32-bit integer</span></span>|<span data-ttu-id="e4971-128">m veya hiçbiri</span><span class="sxs-lookup"><span data-stu-id="e4971-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="e4971-129">uint</span><span class="sxs-lookup"><span data-stu-id="e4971-129">uint</span></span><br /><br /><span data-ttu-id="e4971-130">uint32</span><span class="sxs-lookup"><span data-stu-id="e4971-130">uint32</span></span>|<span data-ttu-id="e4971-131">İmzasız 32-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="e4971-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="e4971-132">u veya ul</span><span class="sxs-lookup"><span data-stu-id="e4971-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="e4971-133">unativeint</span><span class="sxs-lookup"><span data-stu-id="e4971-133">unativeint</span></span>|<span data-ttu-id="e4971-134">işaretsiz doğal sayı olarak yerel işaretçiden</span><span class="sxs-lookup"><span data-stu-id="e4971-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="e4971-135">kaldırma</span><span class="sxs-lookup"><span data-stu-id="e4971-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="e4971-136">Int64</span><span class="sxs-lookup"><span data-stu-id="e4971-136">int64</span></span>|<span data-ttu-id="e4971-137">işaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="e4971-137">signed 64-bit integer</span></span>|<span data-ttu-id="e4971-138">L</span><span class="sxs-lookup"><span data-stu-id="e4971-138">L</span></span>|`86L`|
|<span data-ttu-id="e4971-139">uint64</span><span class="sxs-lookup"><span data-stu-id="e4971-139">uint64</span></span>|<span data-ttu-id="e4971-140">İmzasız 64-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="e4971-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="e4971-141">UL</span><span class="sxs-lookup"><span data-stu-id="e4971-141">UL</span></span>|`86UL`|
|<span data-ttu-id="e4971-142">tek float32</span><span class="sxs-lookup"><span data-stu-id="e4971-142">single, float32</span></span>|<span data-ttu-id="e4971-143">32 bit kayan nokta sayısı</span><span class="sxs-lookup"><span data-stu-id="e4971-143">32-bit floating point number</span></span>|<span data-ttu-id="e4971-144">F veya f</span><span class="sxs-lookup"><span data-stu-id="e4971-144">F or f</span></span>|<span data-ttu-id="e4971-145">`4.14F` Veya `4.14f`</span><span class="sxs-lookup"><span data-stu-id="e4971-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="e4971-146">LF</span><span class="sxs-lookup"><span data-stu-id="e4971-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="e4971-147">float; çift</span><span class="sxs-lookup"><span data-stu-id="e4971-147">float; double</span></span>|<span data-ttu-id="e4971-148">64-bit kayan nokta sayısı</span><span class="sxs-lookup"><span data-stu-id="e4971-148">64-bit floating point number</span></span>|<span data-ttu-id="e4971-149">yok</span><span class="sxs-lookup"><span data-stu-id="e4971-149">none</span></span>|<span data-ttu-id="e4971-150">`4.14` veya `2.3E+32` veya `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="e4971-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="e4971-151">LF</span><span class="sxs-lookup"><span data-stu-id="e4971-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="e4971-152">bigint</span><span class="sxs-lookup"><span data-stu-id="e4971-152">bigint</span></span>|<span data-ttu-id="e4971-153">64-bit gösterimine bunlarla sınırlı olmamak tamsayı</span><span class="sxs-lookup"><span data-stu-id="e4971-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="e4971-154">I</span><span class="sxs-lookup"><span data-stu-id="e4971-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="e4971-155">decimal</span><span class="sxs-lookup"><span data-stu-id="e4971-155">decimal</span></span>|<span data-ttu-id="e4971-156">bir sabit bir nokta ya da rasyonel sayı olarak temsil kesirli numarası</span><span class="sxs-lookup"><span data-stu-id="e4971-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="e4971-157">M veya m</span><span class="sxs-lookup"><span data-stu-id="e4971-157">M or m</span></span>|<span data-ttu-id="e4971-158">`0.7833M` Veya `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="e4971-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="e4971-159">Char</span><span class="sxs-lookup"><span data-stu-id="e4971-159">Char</span></span>|<span data-ttu-id="e4971-160">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="e4971-160">Unicode character</span></span>|<span data-ttu-id="e4971-161">yok</span><span class="sxs-lookup"><span data-stu-id="e4971-161">none</span></span>|`'a'`|
|<span data-ttu-id="e4971-162">Dize</span><span class="sxs-lookup"><span data-stu-id="e4971-162">String</span></span>|<span data-ttu-id="e4971-163">UNICODE dizesi</span><span class="sxs-lookup"><span data-stu-id="e4971-163">Unicode string</span></span>|<span data-ttu-id="e4971-164">yok</span><span class="sxs-lookup"><span data-stu-id="e4971-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="e4971-165">veya</span><span class="sxs-lookup"><span data-stu-id="e4971-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="e4971-166">veya</span><span class="sxs-lookup"><span data-stu-id="e4971-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="e4971-167">veya</span><span class="sxs-lookup"><span data-stu-id="e4971-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="e4971-168">Ayrıca bkz. [dizeleri](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="e4971-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="e4971-169">byte</span><span class="sxs-lookup"><span data-stu-id="e4971-169">byte</span></span>|<span data-ttu-id="e4971-170">ASCII karakter</span><span class="sxs-lookup"><span data-stu-id="e4971-170">ASCII character</span></span>|<span data-ttu-id="e4971-171">B</span><span class="sxs-lookup"><span data-stu-id="e4971-171">B</span></span>|`'a'B`|
|<span data-ttu-id="e4971-172">Byte]</span><span class="sxs-lookup"><span data-stu-id="e4971-172">byte[]</span></span>|<span data-ttu-id="e4971-173">ASCII dizesi</span><span class="sxs-lookup"><span data-stu-id="e4971-173">ASCII string</span></span>|<span data-ttu-id="e4971-174">B</span><span class="sxs-lookup"><span data-stu-id="e4971-174">B</span></span>|`"text"B`|
|<span data-ttu-id="e4971-175">String veya byte]</span><span class="sxs-lookup"><span data-stu-id="e4971-175">String or byte[]</span></span>|<span data-ttu-id="e4971-176">harfi harfine dize</span><span class="sxs-lookup"><span data-stu-id="e4971-176">verbatim string</span></span>|<span data-ttu-id="e4971-177">@ öneki</span><span class="sxs-lookup"><span data-stu-id="e4971-177">@ prefix</span></span>|<span data-ttu-id="e4971-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="e4971-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="e4971-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="e4971-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4971-180">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4971-180">Remarks</span></span>
<span data-ttu-id="e4971-181">Unicode dizelerini kullanarak belirtebilirsiniz açık Kodlamalar içerebilir `\u` bir 16 bit onaltılık kodu veya kullanarak belirtebilirsiniz UTF-32 kodlamaları arkasından `\U` bir Unicode temsil eden bir 32 bit onaltılık kodla ve ardından yedek çifti.</span><span class="sxs-lookup"><span data-stu-id="e4971-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="e4971-182">F # 3.1 itibariyle, kullandığınız `+` dize değişmez değerleri birleştirmek oturum açın.</span><span class="sxs-lookup"><span data-stu-id="e4971-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="e4971-183">Bit düzeyinde kullanabilirsiniz veya (`|||`) enum bayrakları birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="e4971-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="e4971-184">Örneğin, aşağıdaki kodu F # 3.1 uygundur:</span><span class="sxs-lookup"><span data-stu-id="e4971-184">For example, the following code is legal in F# 3.1:</span></span>

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

<span data-ttu-id="e4971-185">Diğer bit düzeyinde işleçler kullanılmasına izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="e4971-185">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="e4971-186">Adlandırılmış değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="e4971-186">Named Literals</span></span>
<span data-ttu-id="e4971-187">Sabitler yönelik değerleri işaretlenir ile [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e4971-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="e4971-188">Bu öznitelik, bir sabit değer olarak derlenmesi için bir değer neden etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="e4971-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="e4971-189">Eşleşen düzeninde küçük harf karakterler ile başlayan tanımlayıcıları her zaman bağlı olmasını değişkenleri olarak davranılır yerine değişmez değerler tanımlarken değişmez değerler, bu nedenle genellikle ilk harfler büyük harf kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4971-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="e4971-190">Diğer tabanları tamsayılar</span><span class="sxs-lookup"><span data-stu-id="e4971-190">Integers In Other Bases</span></span>

<span data-ttu-id="e4971-191">İmzalı 32-bit tamsayı de belirtilebilir onaltılı, sekizli veya ikili kullanarak bir `0x`, `0o` veya `0b` sırasıyla önek.</span><span class="sxs-lookup"><span data-stu-id="e4971-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="e4971-192">Sayısal değişmez değerlerinde alt çizgiler</span><span class="sxs-lookup"><span data-stu-id="e4971-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="e4971-193">F # 4.1 ile başlayarak, basamak alt çizgi karakteriyle ayırabilirsiniz (`_`).</span><span class="sxs-lookup"><span data-stu-id="e4971-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="e4971-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4971-194">See Also</span></span>

[<span data-ttu-id="e4971-195">Core.LiteralAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="e4971-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

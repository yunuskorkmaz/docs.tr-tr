---
title: Değişmez Değerler (F#)
description: Değişmez değer türleri hakkında bilgi edinin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: 7a531cd63c5a4dc1123834d481fc998216b0d82d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131345"
---
# <a name="literals"></a><span data-ttu-id="62d72-103">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="62d72-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="62d72-104">Bu makaledeki API başvuru bağlantıları için MSDN (şimdilik) sürer.</span><span class="sxs-lookup"><span data-stu-id="62d72-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="62d72-105">Bu konu, bir sabit listesinde değişmez değerin türünü gösteren bir tablo sağlar F#.</span><span class="sxs-lookup"><span data-stu-id="62d72-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="62d72-106">Değişmez değer türleri</span><span class="sxs-lookup"><span data-stu-id="62d72-106">Literal Types</span></span>

<span data-ttu-id="62d72-107">Aşağıdaki tabloda, değişmez değer türleri gösterilmektedir F#.</span><span class="sxs-lookup"><span data-stu-id="62d72-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="62d72-108">Onaltılık gösterimdeki basamakları temsil eden karakterler büyük küçük harfe duyarlı değildir; türü tanımlayan karakterler büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="62d72-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="62d72-109">Tür</span><span class="sxs-lookup"><span data-stu-id="62d72-109">Type</span></span>|<span data-ttu-id="62d72-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62d72-110">Description</span></span>|<span data-ttu-id="62d72-111">Sonek veya önek</span><span class="sxs-lookup"><span data-stu-id="62d72-111">Suffix or prefix</span></span>|<span data-ttu-id="62d72-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="62d72-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="62d72-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="62d72-113">sbyte</span></span>|<span data-ttu-id="62d72-114">İşaretli 8 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-114">signed 8-bit integer</span></span>|<span data-ttu-id="62d72-115">y</span><span class="sxs-lookup"><span data-stu-id="62d72-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="62d72-116">byte</span><span class="sxs-lookup"><span data-stu-id="62d72-116">byte</span></span>|<span data-ttu-id="62d72-117">imzalanmamış 8 bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="62d72-118">Uy</span><span class="sxs-lookup"><span data-stu-id="62d72-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="62d72-119">Int16</span><span class="sxs-lookup"><span data-stu-id="62d72-119">int16</span></span>|<span data-ttu-id="62d72-120">İşaretli 16 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-120">signed 16-bit integer</span></span>|<span data-ttu-id="62d72-121">s</span><span class="sxs-lookup"><span data-stu-id="62d72-121">s</span></span>|`86s`|
|<span data-ttu-id="62d72-122">uint16</span><span class="sxs-lookup"><span data-stu-id="62d72-122">uint16</span></span>|<span data-ttu-id="62d72-123">İmzasız 16-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="62d72-124">ABD</span><span class="sxs-lookup"><span data-stu-id="62d72-124">us</span></span>|`86us`|
|<span data-ttu-id="62d72-125">int</span><span class="sxs-lookup"><span data-stu-id="62d72-125">int</span></span><br /><br /><span data-ttu-id="62d72-126">Int32</span><span class="sxs-lookup"><span data-stu-id="62d72-126">int32</span></span>|<span data-ttu-id="62d72-127">İşaretli 32 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-127">signed 32-bit integer</span></span>|<span data-ttu-id="62d72-128">l ya da yok</span><span class="sxs-lookup"><span data-stu-id="62d72-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="62d72-129">uint</span><span class="sxs-lookup"><span data-stu-id="62d72-129">uint</span></span><br /><br /><span data-ttu-id="62d72-130">uint32</span><span class="sxs-lookup"><span data-stu-id="62d72-130">uint32</span></span>|<span data-ttu-id="62d72-131">işaretsiz 32-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="62d72-132">u veya ul</span><span class="sxs-lookup"><span data-stu-id="62d72-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="62d72-133">unativeint</span><span class="sxs-lookup"><span data-stu-id="62d72-133">unativeint</span></span>|<span data-ttu-id="62d72-134">işeritsiz doğal sayı olarak yerel işaretçi</span><span class="sxs-lookup"><span data-stu-id="62d72-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="62d72-135">Geri Al</span><span class="sxs-lookup"><span data-stu-id="62d72-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="62d72-136">Int64</span><span class="sxs-lookup"><span data-stu-id="62d72-136">int64</span></span>|<span data-ttu-id="62d72-137">İşaretli 64 bit tam sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-137">signed 64-bit integer</span></span>|<span data-ttu-id="62d72-138">L</span><span class="sxs-lookup"><span data-stu-id="62d72-138">L</span></span>|`86L`|
|<span data-ttu-id="62d72-139">uint64</span><span class="sxs-lookup"><span data-stu-id="62d72-139">uint64</span></span>|<span data-ttu-id="62d72-140">işaretsiz 64-bit doğal sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="62d72-141">UL</span><span class="sxs-lookup"><span data-stu-id="62d72-141">UL</span></span>|`86UL`|
|<span data-ttu-id="62d72-142">tek, float32</span><span class="sxs-lookup"><span data-stu-id="62d72-142">single, float32</span></span>|<span data-ttu-id="62d72-143">32 bit kayan nokta sayısı</span><span class="sxs-lookup"><span data-stu-id="62d72-143">32-bit floating point number</span></span>|<span data-ttu-id="62d72-144">F veya f</span><span class="sxs-lookup"><span data-stu-id="62d72-144">F or f</span></span>|<span data-ttu-id="62d72-145">`4.14F` veya `4.14f`</span><span class="sxs-lookup"><span data-stu-id="62d72-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="62d72-146">LF</span><span class="sxs-lookup"><span data-stu-id="62d72-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="62d72-147">kayan nokta; çift</span><span class="sxs-lookup"><span data-stu-id="62d72-147">float; double</span></span>|<span data-ttu-id="62d72-148">64-bit kayan nokta sayısı</span><span class="sxs-lookup"><span data-stu-id="62d72-148">64-bit floating point number</span></span>|<span data-ttu-id="62d72-149">yok</span><span class="sxs-lookup"><span data-stu-id="62d72-149">none</span></span>|<span data-ttu-id="62d72-150">`4.14` veya `2.3E+32` veya `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="62d72-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="62d72-151">LF</span><span class="sxs-lookup"><span data-stu-id="62d72-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="62d72-152">bigint</span><span class="sxs-lookup"><span data-stu-id="62d72-152">bigint</span></span>|<span data-ttu-id="62d72-153">64 bit gösterimle sınırlı olmayan tamsayı</span><span class="sxs-lookup"><span data-stu-id="62d72-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="62d72-154">I</span><span class="sxs-lookup"><span data-stu-id="62d72-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="62d72-155">decimal</span><span class="sxs-lookup"><span data-stu-id="62d72-155">decimal</span></span>|<span data-ttu-id="62d72-156">Sabit nokta veya rasyonel sayı olarak temsil edilen kesirli sayı</span><span class="sxs-lookup"><span data-stu-id="62d72-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="62d72-157">M veya m</span><span class="sxs-lookup"><span data-stu-id="62d72-157">M or m</span></span>|<span data-ttu-id="62d72-158">`0.7833M` veya `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="62d72-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="62d72-159">Char</span><span class="sxs-lookup"><span data-stu-id="62d72-159">Char</span></span>|<span data-ttu-id="62d72-160">Unicode karakter</span><span class="sxs-lookup"><span data-stu-id="62d72-160">Unicode character</span></span>|<span data-ttu-id="62d72-161">yok</span><span class="sxs-lookup"><span data-stu-id="62d72-161">none</span></span>|`'a'`|
|<span data-ttu-id="62d72-162">Dize</span><span class="sxs-lookup"><span data-stu-id="62d72-162">String</span></span>|<span data-ttu-id="62d72-163">Unicode dizesi</span><span class="sxs-lookup"><span data-stu-id="62d72-163">Unicode string</span></span>|<span data-ttu-id="62d72-164">yok</span><span class="sxs-lookup"><span data-stu-id="62d72-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="62d72-165">veya</span><span class="sxs-lookup"><span data-stu-id="62d72-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="62d72-166">veya</span><span class="sxs-lookup"><span data-stu-id="62d72-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="62d72-167">veya</span><span class="sxs-lookup"><span data-stu-id="62d72-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="62d72-168">Ayrıca bkz: [dizeleri](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="62d72-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="62d72-169">byte</span><span class="sxs-lookup"><span data-stu-id="62d72-169">byte</span></span>|<span data-ttu-id="62d72-170">ASCII karakteri</span><span class="sxs-lookup"><span data-stu-id="62d72-170">ASCII character</span></span>|<span data-ttu-id="62d72-171">B</span><span class="sxs-lookup"><span data-stu-id="62d72-171">B</span></span>|`'a'B`|
|<span data-ttu-id="62d72-172">bayt]</span><span class="sxs-lookup"><span data-stu-id="62d72-172">byte[]</span></span>|<span data-ttu-id="62d72-173">ASCII dizesi</span><span class="sxs-lookup"><span data-stu-id="62d72-173">ASCII string</span></span>|<span data-ttu-id="62d72-174">B</span><span class="sxs-lookup"><span data-stu-id="62d72-174">B</span></span>|`"text"B`|
|<span data-ttu-id="62d72-175">Dize veya bayt]</span><span class="sxs-lookup"><span data-stu-id="62d72-175">String or byte[]</span></span>|<span data-ttu-id="62d72-176">Verbatim dizesi</span><span class="sxs-lookup"><span data-stu-id="62d72-176">verbatim string</span></span>|<span data-ttu-id="62d72-177">@ ön ek</span><span class="sxs-lookup"><span data-stu-id="62d72-177">@ prefix</span></span>|<span data-ttu-id="62d72-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="62d72-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="62d72-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="62d72-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="62d72-180">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62d72-180">Remarks</span></span>

<span data-ttu-id="62d72-181">Unicode dizelerini kullanarak belirttiğiniz açık Kodlamalar içerebilir `\u` bir 16 bitlik onaltılık kod ya da kullanarak belirtebilirsiniz UTF-32 kodlamalarına ardından `\U` bir Unicode temsil eden bir 32 bit onaltılık kodla ve ardından vekil çifti.</span><span class="sxs-lookup"><span data-stu-id="62d72-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="62d72-182">Sürümünden itibaren F# kullanabileceğiniz 3.1, `+` dize değişmez değerlerini birleştirmek için oturum açın.</span><span class="sxs-lookup"><span data-stu-id="62d72-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="62d72-183">Bit düzeyinde kullanabilirsiniz veya (`|||`) numaralandırma bayraklarını birleştirmek istiyorsanız işleci.</span><span class="sxs-lookup"><span data-stu-id="62d72-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="62d72-184">Örneğin, aşağıdaki yasal kodudur F# 3.1:</span><span class="sxs-lookup"><span data-stu-id="62d72-184">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let literal1 = "a" + "b"

[<Literal>]
let fileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let literal2 = 1 ||| 64

[<Literal>]
let literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="62d72-185">Bit düzeyindeki diğer işleçlerin kullanımına izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="62d72-185">The use of other bitwise operators isn't allowed.</span></span>

## <a name="named-literals"></a><span data-ttu-id="62d72-186">Adlandırılmış değişmez değerler</span><span class="sxs-lookup"><span data-stu-id="62d72-186">Named Literals</span></span>

<span data-ttu-id="62d72-187">Sabit olması amaçlanır değerler ile işaretlenebilir [değişmez değer](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="62d72-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="62d72-188">Bu öznitelik değeri bir sabit olarak derlenmesine neden etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="62d72-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="62d72-189">Eşleştirme ifadesi deseninde, küçük harfle başlayan tanımlayıcılar her zaman bağlı değişkenleri olarak kabul edilir yerine sabit değerleri tanımlarken değişmez değer olarak, bu nedenle genellikle ilk harfleri büyük kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62d72-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="62d72-190">Diğer Tabanlara tamsayılar</span><span class="sxs-lookup"><span data-stu-id="62d72-190">Integers In Other Bases</span></span>

<span data-ttu-id="62d72-191">İşaretli 32 bit tam sayılar da belirtilebilir onaltılık, sekizlik veya ikili kullanarak bir `0x`, `0o` veya `0b` sırasıyla önek.</span><span class="sxs-lookup"><span data-stu-id="62d72-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="62d72-192">Sayısal sabit değerlerde alt çizgiler</span><span class="sxs-lookup"><span data-stu-id="62d72-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="62d72-193">İle başlayarak F# 4.1, basamak alt çizgi karakteriyle ayırın (`_`).</span><span class="sxs-lookup"><span data-stu-id="62d72-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="62d72-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62d72-194">See also</span></span>

- [<span data-ttu-id="62d72-195">Core.LiteralAttribute sınıfı</span><span class="sxs-lookup"><span data-stu-id="62d72-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

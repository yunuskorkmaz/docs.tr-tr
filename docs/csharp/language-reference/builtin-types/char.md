---
title: char türü - C# referans
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 8727e47e13082e8550fb174c92139dfd5c17ec36
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134334"
---
# <a name="char-c-reference"></a><span data-ttu-id="d784f-102">char (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="d784f-102">char (C# reference)</span></span>

<span data-ttu-id="d784f-103">Tür `char` anahtar kelimesi, UNicode UTF-16 karakterini temsil eden .NET <xref:System.Char?displayProperty=nameWithType> yapı türüiçin bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="d784f-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="d784f-104">Tür</span><span class="sxs-lookup"><span data-stu-id="d784f-104">Type</span></span>|<span data-ttu-id="d784f-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="d784f-105">Range</span></span>|<span data-ttu-id="d784f-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="d784f-106">Size</span></span>|<span data-ttu-id="d784f-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="d784f-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="d784f-108">U+0000 için U+FFFF</span><span class="sxs-lookup"><span data-stu-id="d784f-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="d784f-109">16 bit</span><span class="sxs-lookup"><span data-stu-id="d784f-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="d784f-110">`char` Türünün varsayılan değeri `\0`, yani U+0000'dir.</span><span class="sxs-lookup"><span data-stu-id="d784f-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="d784f-111">[Dize](reference-types.md#the-string-type) türü, metni bir `char` değerler dizisi olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d784f-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="d784f-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="d784f-112">Literals</span></span>

<span data-ttu-id="d784f-113">Aşağıdakilerle bir `char` değer belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d784f-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="d784f-114">gerçek bir karakter.</span><span class="sxs-lookup"><span data-stu-id="d784f-114">a character literal.</span></span>
- <span data-ttu-id="d784f-115">bir karakter kodunun dört `\u` sembollü hexadecimal gösterimi tarafından izlenen bir Unicode kaçış sırası.</span><span class="sxs-lookup"><span data-stu-id="d784f-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="d784f-116">bir karakter kodunun hexadecimal gösterimi takip eden `\x` bir hexadecimal kaçış dizisi.</span><span class="sxs-lookup"><span data-stu-id="d784f-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

<span data-ttu-id="d784f-117">Önceki örnekte de görüldüğü gibi, karakter kodunun değerini karşılık `char` gelen değere de atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d784f-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="d784f-118">Unicode kaçış sırası durumunda, dört hexadecimal basamak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d784f-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="d784f-119">Diğer bir `\u006A` süre geçerli bir `\u06A` kaçış `\u6A` dizisidir ve geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d784f-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="d784f-120">Bir hexadecimal kaçış sırası durumunda, önde gelen sıfırları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d784f-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="d784f-121">Diğer bir `\x006A`şey, , , `\x06A`ve `\x6A` kaçış dizileri geçerlidir ve aynı karaktere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d784f-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="d784f-122">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="d784f-122">Conversions</span></span>

<span data-ttu-id="d784f-123">Türü `char` örtülü olarak aşağıdaki [integral](integral-numeric-types.md) türlerine `ushort`dönüştürülebilir: `long`, `ulong`, `int` `uint`, ve .</span><span class="sxs-lookup"><span data-stu-id="d784f-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="d784f-124">Ayrıca dahili [kayan nokta](floating-point-numeric-types.md) sayısal türlerine dolaylı olarak dönüştürülebilir: `float` `double`, `decimal`, ve .</span><span class="sxs-lookup"><span data-stu-id="d784f-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="d784f-125">Açıkça dönüştürülebilir `sbyte`, `byte`, ve `short` integral türleri.</span><span class="sxs-lookup"><span data-stu-id="d784f-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="d784f-126">Diğer türlerden `char` türe örtülü dönüşüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="d784f-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="d784f-127">Ancak, herhangi bir [integral](integral-numeric-types.md) veya [kayan nokta](floating-point-numeric-types.md) sayısal türü `char`açıkça dönüştürülebilir .</span><span class="sxs-lookup"><span data-stu-id="d784f-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d784f-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d784f-128">C# language specification</span></span>

<span data-ttu-id="d784f-129">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İntegral türleri](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d784f-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d784f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d784f-130">See also</span></span>

- [<span data-ttu-id="d784f-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d784f-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d784f-132">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="d784f-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="d784f-133">Dizeler</span><span class="sxs-lookup"><span data-stu-id="d784f-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="d784f-134">.NET'te karakter kodlaması</span><span class="sxs-lookup"><span data-stu-id="d784f-134">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)

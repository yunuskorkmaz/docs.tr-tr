---
title: karakter türü- C# başvuru
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: a5aca12e4037d517c3bcfb403c990605a052d48f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239852"
---
# <a name="char-c-reference"></a><span data-ttu-id="e4073-102">Char (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="e4073-102">char (C# reference)</span></span>

<span data-ttu-id="e4073-103">`char` Type anahtar sözcüğü, bir Unicode UTF-16 karakteri temsil eden .NET <xref:System.Char?displayProperty=nameWithType> yapı türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="e4073-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="e4073-104">Tür</span><span class="sxs-lookup"><span data-stu-id="e4073-104">Type</span></span>|<span data-ttu-id="e4073-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="e4073-105">Range</span></span>|<span data-ttu-id="e4073-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="e4073-106">Size</span></span>|<span data-ttu-id="e4073-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="e4073-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="e4073-108">U + 0000-U + FFFF</span><span class="sxs-lookup"><span data-stu-id="e4073-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="e4073-109">16 bit</span><span class="sxs-lookup"><span data-stu-id="e4073-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="e4073-110">`char` türünün varsayılan değeri `\0`, yani U + 0000.</span><span class="sxs-lookup"><span data-stu-id="e4073-110">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="e4073-111">[Dize](reference-types.md#the-string-type) türü, metni `char` değerleri dizisi olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e4073-111">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="e4073-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="e4073-112">Literals</span></span>

<span data-ttu-id="e4073-113">İle bir `char` değeri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e4073-113">You can specify a `char` value with:</span></span>

- <span data-ttu-id="e4073-114">bir karakter sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="e4073-114">a character literal.</span></span>
- <span data-ttu-id="e4073-115">bir karakter kodunun dört basamaklı onaltılı temsili `\u` bir Unicode kaçış sırası.</span><span class="sxs-lookup"><span data-stu-id="e4073-115">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="e4073-116">`\x` bir karakter kodunun onaltılı gösterimi tarafından izlenen bir onaltılık kaçış sırası.</span><span class="sxs-lookup"><span data-stu-id="e4073-116">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/snippets/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="e4073-117">Yukarıdaki örnekte gösterildiği gibi, bir karakter kodunun değerini de karşılık gelen `char` değerine çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4073-117">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="e4073-118">Unicode kaçış sırası söz konusu olduğunda, dört onaltılık basamağı de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4073-118">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="e4073-119">Yani, `\u006A` geçerli bir kaçış sırası, `\u06A` ve `\u6A` geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e4073-119">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="e4073-120">Onaltılı kaçış sırası söz konusu olduğunda, öndeki sıfırları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4073-120">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="e4073-121">Diğer bir deyişle, `\x006A`, `\x06A`ve `\x6A` kaçış dizileri geçerlidir ve aynı karaktere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e4073-121">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="e4073-122">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="e4073-122">Conversions</span></span>

<span data-ttu-id="e4073-123">`char` türü örtük olarak şu [integral](integral-numeric-types.md) türlerine dönüştürülebilir: `ushort`, `int`, `uint`, `long`ve `ulong`.</span><span class="sxs-lookup"><span data-stu-id="e4073-123">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="e4073-124">Ayrıca yerleşik [kayan nokta](floating-point-numeric-types.md) sayısal türlerine örtülü olarak dönüştürülebilir: `float`, `double`ve `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e4073-124">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="e4073-125">`sbyte`, `byte`ve `short` integral türlerine açıkça dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e4073-125">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="e4073-126">Diğer türlerden `char` türüne örtük dönüştürme yok.</span><span class="sxs-lookup"><span data-stu-id="e4073-126">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="e4073-127">Ancak, herhangi bir [integral](integral-numeric-types.md) veya [kayan nokta](floating-point-numeric-types.md) sayısal türü `char`açıkça dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e4073-127">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e4073-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e4073-128">C# language specification</span></span>

<span data-ttu-id="e4073-129">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Integral türler](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e4073-129">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4073-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4073-130">See also</span></span>

- [<span data-ttu-id="e4073-131">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="e4073-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e4073-132">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="e4073-132">Value types</span></span>](value-types.md)
- [<span data-ttu-id="e4073-133">Dizeler</span><span class="sxs-lookup"><span data-stu-id="e4073-133">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>

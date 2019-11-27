---
title: karakter türü- C# başvuru
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451166"
---
# <a name="char-c-reference"></a><span data-ttu-id="712fa-102">Char (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="712fa-102">char (C# reference)</span></span>

<span data-ttu-id="712fa-103">`char` Type anahtar sözcüğü, bir Unicode UTF-16 karakteri temsil eden .NET <xref:System.Char?displayProperty=nameWithType> yapı türü için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="712fa-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="712fa-104">Type</span><span class="sxs-lookup"><span data-stu-id="712fa-104">Type</span></span>|<span data-ttu-id="712fa-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="712fa-105">Range</span></span>|<span data-ttu-id="712fa-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="712fa-106">Size</span></span>|<span data-ttu-id="712fa-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="712fa-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="712fa-108">U + 0000-U + FFFF</span><span class="sxs-lookup"><span data-stu-id="712fa-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="712fa-109">16 bit</span><span class="sxs-lookup"><span data-stu-id="712fa-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="712fa-110">[Dize](reference-types.md#the-string-type) türü, metni `char` değerleri dizisi olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="712fa-110">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="712fa-111">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="712fa-111">Literals</span></span>

<span data-ttu-id="712fa-112">İle bir `char` değeri belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="712fa-112">You can specify a `char` value with:</span></span>

- <span data-ttu-id="712fa-113">bir karakter sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="712fa-113">a character literal.</span></span>
- <span data-ttu-id="712fa-114">bir karakter kodunun dört basamaklı onaltılı temsili `\u` bir Unicode kaçış sırası.</span><span class="sxs-lookup"><span data-stu-id="712fa-114">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="712fa-115">`\x` bir karakter kodunun onaltılı gösterimi tarafından izlenen bir onaltılık kaçış sırası.</span><span class="sxs-lookup"><span data-stu-id="712fa-115">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

<span data-ttu-id="712fa-116">Yukarıdaki örnekte gösterildiği gibi, bir karakter kodunun değerini de karşılık gelen `char` değerine çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="712fa-116">As the preceding example shows, you also can cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="712fa-117">Unicode kaçış sırası söz konusu olduğunda, dört onaltılık basamağı de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="712fa-117">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="712fa-118">Yani, `\u006A` geçerli bir kaçış sırası, `\u06A` ve `\u6A` geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="712fa-118">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="712fa-119">Onaltılı kaçış sırası söz konusu olduğunda, öndeki sıfırları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="712fa-119">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="712fa-120">Diğer bir deyişle, `\x006A`, `\x06A`ve `\x6A` kaçış dizileri geçerlidir ve aynı karaktere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="712fa-120">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="712fa-121">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="712fa-121">Conversions</span></span>

<span data-ttu-id="712fa-122">`char` türü örtük olarak şu [integral](integral-numeric-types.md) türlerine dönüştürülebilir: `ushort`, `int`, `uint`, `long`ve `ulong`.</span><span class="sxs-lookup"><span data-stu-id="712fa-122">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="712fa-123">Ayrıca yerleşik [kayan nokta](floating-point-numeric-types.md) sayısal türlerine örtülü olarak dönüştürülebilir: `float`, `double`ve `decimal`.</span><span class="sxs-lookup"><span data-stu-id="712fa-123">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="712fa-124">`sbyte`, `byte`ve `short` integral türlerine açıkça dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="712fa-124">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="712fa-125">Diğer türlerden `char` türüne örtük dönüştürme yok.</span><span class="sxs-lookup"><span data-stu-id="712fa-125">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="712fa-126">Ancak, herhangi bir [integral](integral-numeric-types.md) veya [kayan nokta](floating-point-numeric-types.md) sayısal türü `char`açıkça dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="712fa-126">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="712fa-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="712fa-127">C# language specification</span></span>

<span data-ttu-id="712fa-128">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Integral türler](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="712fa-128">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="712fa-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="712fa-129">See also</span></span>

- [<span data-ttu-id="712fa-130">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="712fa-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="712fa-131">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="712fa-131">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="712fa-132">Dizeler</span><span class="sxs-lookup"><span data-stu-id="712fa-132">Strings</span></span>](../../programming-guide/strings/index.md)

---
title: Char anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771796"
---
# <a name="char-c-reference"></a><span data-ttu-id="e2282-102">Char (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="e2282-102">char (C# reference)</span></span>

<span data-ttu-id="e2282-103">@No__t_0 Type anahtar sözcüğü, bir Unicode UTF-16 karakteri temsil eden .NET <xref:System.Char?displayProperty=nameWithType> yapı türü için bir diğer addır:</span><span class="sxs-lookup"><span data-stu-id="e2282-103">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character:</span></span>

|<span data-ttu-id="e2282-104">Tür</span><span class="sxs-lookup"><span data-stu-id="e2282-104">Type</span></span>|<span data-ttu-id="e2282-105">Aralık</span><span class="sxs-lookup"><span data-stu-id="e2282-105">Range</span></span>|<span data-ttu-id="e2282-106">Boyut</span><span class="sxs-lookup"><span data-stu-id="e2282-106">Size</span></span>|<span data-ttu-id="e2282-107">.NET türü</span><span class="sxs-lookup"><span data-stu-id="e2282-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="e2282-108">U + 0000-U + FFFF</span><span class="sxs-lookup"><span data-stu-id="e2282-108">U+0000 to U+FFFF</span></span>|<span data-ttu-id="e2282-109">16 bit</span><span class="sxs-lookup"><span data-stu-id="e2282-109">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="e2282-110">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="e2282-110">Literals</span></span>

<span data-ttu-id="e2282-111">@No__t_0 türünün sabitleri, karakter sabit değerleri, onaltılık kaçış dizisi veya Unicode temsili olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2282-111">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="e2282-112">Ayrıca, bir integral karakter kodunu karşılık gelen `char` değerine de çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2282-112">You can also cast an integral character code into the corresponding `char` value.</span></span> <span data-ttu-id="e2282-113">Aşağıdaki örnekte, `char` dizisinin dört öğesi aynı karakterle `X` başlatılır:</span><span class="sxs-lookup"><span data-stu-id="e2282-113">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="e2282-114">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="e2282-114">Conversions</span></span>

<span data-ttu-id="e2282-115">@No__t_0 türü örtük olarak şu [integral](../builtin-types/integral-numeric-types.md) türlerine dönüştürülebilir: `ushort`, `int`, `uint`, `long` ve `ulong`.</span><span class="sxs-lookup"><span data-stu-id="e2282-115">The `char` type is implicitly convertible to the following [integral](../builtin-types/integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="e2282-116">Ayrıca yerleşik [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türlerine örtülü olarak dönüştürülebilir: `float`, `double` ve `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e2282-116">It's also implicitly convertible to the built-in [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="e2282-117">@No__t_0, `byte` ve `short` integral türlerine açıkça dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e2282-117">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="e2282-118">Diğer türlerden `char` türüne örtük dönüştürme yok.</span><span class="sxs-lookup"><span data-stu-id="e2282-118">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="e2282-119">Ancak, herhangi bir [integral](../builtin-types/integral-numeric-types.md) veya [kayan nokta](../builtin-types/floating-point-numeric-types.md) sayısal türü `char` açıkça dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e2282-119">However, any [integral](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e2282-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e2282-120">C# language specification</span></span>

<span data-ttu-id="e2282-121">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Integral türler](~/_csharplang/spec/types.md#integral-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2282-121">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2282-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2282-122">See also</span></span>

- [<span data-ttu-id="e2282-123">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="e2282-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e2282-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e2282-124">C# keywords</span></span>](./index.md)
- [<span data-ttu-id="e2282-125">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="e2282-125">Built-in types table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="e2282-126">Dizeler</span><span class="sxs-lookup"><span data-stu-id="e2282-126">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>

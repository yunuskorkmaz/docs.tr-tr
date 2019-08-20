---
title: Char anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 754c04bfc3b4090906420d55d55e51606b72f187
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605954"
---
# <a name="char-c-reference"></a><span data-ttu-id="cdc29-102">char (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cdc29-102">char (C# Reference)</span></span>

<span data-ttu-id="cdc29-103">Anahtar sözcüğü, .NET Framework bir Unicode karakteri temsil etmek için <xref:System.Char?displayProperty=nameWithType> kullandığı yapının bir örneğini bildirmek için kullanılır. `char`</span><span class="sxs-lookup"><span data-stu-id="cdc29-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="cdc29-104">Bir `Char` nesnenin değeri 16 bit sayısal (sıra sayısı) değeridir.</span><span class="sxs-lookup"><span data-stu-id="cdc29-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="cdc29-105">Unicode karakterler, dünyanın her yerindeki yazılı dillerin çoğunu temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdc29-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="cdc29-106">Tür</span><span class="sxs-lookup"><span data-stu-id="cdc29-106">Type</span></span>|<span data-ttu-id="cdc29-107">Aralık</span><span class="sxs-lookup"><span data-stu-id="cdc29-107">Range</span></span>|<span data-ttu-id="cdc29-108">Boyut</span><span class="sxs-lookup"><span data-stu-id="cdc29-108">Size</span></span>|<span data-ttu-id="cdc29-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="cdc29-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="cdc29-110">U + 0000-U + FFFF</span><span class="sxs-lookup"><span data-stu-id="cdc29-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="cdc29-111">Unicode 16 bit karakter</span><span class="sxs-lookup"><span data-stu-id="cdc29-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="cdc29-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="cdc29-112">Literals</span></span>

<span data-ttu-id="cdc29-113">`char` Türün sabitleri, karakter sabit değerleri, onaltılık kaçış dizisi veya Unicode temsili olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc29-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="cdc29-114">İntegral karakter kodlarını da çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc29-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="cdc29-115">Aşağıdaki örnekte, dört `char` değişken aynı karakterle `X`başlatılır:</span><span class="sxs-lookup"><span data-stu-id="cdc29-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="cdc29-116">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="cdc29-116">Conversions</span></span>

<span data-ttu-id="cdc29-117">Bir `char` , örtük olarak [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)veya [Decimal](../builtin-types/floating-point-numeric-types.md)'a dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="cdc29-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="cdc29-118">Ancak, diğer türlerden `char` türüne örtülü dönüşüm yoktur.</span><span class="sxs-lookup"><span data-stu-id="cdc29-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="cdc29-119">Türü <xref:System.Char?displayProperty=nameWithType> , `char` değerleriyle çalışmak için çeşitli statik yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc29-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cdc29-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="cdc29-120">C# language specification</span></span>  

<span data-ttu-id="cdc29-121">Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Integral türleri](~/_csharplang/spec/types.md#integral-types) .</span><span class="sxs-lookup"><span data-stu-id="cdc29-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="cdc29-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="cdc29-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdc29-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdc29-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="cdc29-124">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="cdc29-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cdc29-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cdc29-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cdc29-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="cdc29-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="cdc29-127">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="cdc29-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="cdc29-128">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="cdc29-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="cdc29-129">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="cdc29-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="cdc29-130">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="cdc29-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="cdc29-131">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="cdc29-131">Nullable Types</span></span>](../../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="cdc29-132">Dizeler</span><span class="sxs-lookup"><span data-stu-id="cdc29-132">Strings</span></span>](../../programming-guide/strings/index.md)

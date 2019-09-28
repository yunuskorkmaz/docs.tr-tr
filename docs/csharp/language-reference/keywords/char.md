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
ms.openlocfilehash: 255e69d3715a22e7933b4036e968e610657748cf
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353772"
---
# <a name="char-c-reference"></a><span data-ttu-id="8070c-102">char (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8070c-102">char (C# Reference)</span></span>

<span data-ttu-id="8070c-103">@No__t-0 anahtar sözcüğü, .NET Framework bir Unicode karakteri temsil etmek için kullandığı <xref:System.Char?displayProperty=nameWithType> yapısının bir örneğini bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8070c-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="8070c-104">@No__t-0 nesnesinin değeri 16 bit sayısal (sıra sayısı) değeridir.</span><span class="sxs-lookup"><span data-stu-id="8070c-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="8070c-105">Unicode karakterler, dünyanın her yerindeki yazılı dillerin çoğunu temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8070c-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="8070c-106">Type</span><span class="sxs-lookup"><span data-stu-id="8070c-106">Type</span></span>|<span data-ttu-id="8070c-107">Aralık</span><span class="sxs-lookup"><span data-stu-id="8070c-107">Range</span></span>|<span data-ttu-id="8070c-108">Size</span><span class="sxs-lookup"><span data-stu-id="8070c-108">Size</span></span>|<span data-ttu-id="8070c-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="8070c-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="8070c-110">U + 0000-U + FFFF</span><span class="sxs-lookup"><span data-stu-id="8070c-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="8070c-111">Unicode 16 bit karakter</span><span class="sxs-lookup"><span data-stu-id="8070c-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="8070c-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="8070c-112">Literals</span></span>

<span data-ttu-id="8070c-113">@No__t-0 türündeki sabitler, karakter sabit değerleri, onaltılık kaçış dizisi veya Unicode temsili olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="8070c-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="8070c-114">İntegral karakter kodlarını da çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8070c-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="8070c-115">Aşağıdaki örnekte, dört `char` değişkenleri aynı karakterle `X` ile başlatılır:</span><span class="sxs-lookup"><span data-stu-id="8070c-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="8070c-116">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="8070c-116">Conversions</span></span>

<span data-ttu-id="8070c-117">@No__t-0 örtük olarak [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)veya [Decimal](../builtin-types/floating-point-numeric-types.md)'a dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="8070c-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="8070c-118">Ancak, diğer türlerden `char` türüne örtük dönüştürmeler yoktur.</span><span class="sxs-lookup"><span data-stu-id="8070c-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="8070c-119">@No__t-0 türü `char` değerleriyle çalışmak için birkaç statik yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8070c-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8070c-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8070c-120">C# language specification</span></span>  

<span data-ttu-id="8070c-121">Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Integral türleri](~/_csharplang/spec/types.md#integral-types) .</span><span class="sxs-lookup"><span data-stu-id="8070c-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="8070c-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="8070c-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8070c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8070c-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="8070c-124">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="8070c-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8070c-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8070c-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8070c-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8070c-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="8070c-127">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="8070c-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="8070c-128">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="8070c-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="8070c-129">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="8070c-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="8070c-130">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="8070c-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="8070c-131">Dizeler</span><span class="sxs-lookup"><span data-stu-id="8070c-131">Strings</span></span>](../../programming-guide/strings/index.md)

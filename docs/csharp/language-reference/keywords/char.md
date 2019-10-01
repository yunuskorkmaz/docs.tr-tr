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
ms.openlocfilehash: 63f8871926e8c279678c59a2256bef46b2ff514e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698781"
---
# <a name="char-c-reference"></a><span data-ttu-id="17ebd-102">char (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="17ebd-102">char (C# Reference)</span></span>

<span data-ttu-id="17ebd-103">@No__t-0 anahtar sözcüğü, .NET Framework bir Unicode karakteri temsil etmek için kullandığı <xref:System.Char?displayProperty=nameWithType> yapısının bir örneğini bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17ebd-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="17ebd-104">@No__t-0 nesnesinin değeri 16 bit sayısal (sıra sayısı) değeridir.</span><span class="sxs-lookup"><span data-stu-id="17ebd-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="17ebd-105">Unicode karakterler, dünyanın her yerindeki yazılı dillerin çoğunu temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17ebd-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="17ebd-106">Tür</span><span class="sxs-lookup"><span data-stu-id="17ebd-106">Type</span></span>|<span data-ttu-id="17ebd-107">Aralık</span><span class="sxs-lookup"><span data-stu-id="17ebd-107">Range</span></span>|<span data-ttu-id="17ebd-108">Boyut</span><span class="sxs-lookup"><span data-stu-id="17ebd-108">Size</span></span>|<span data-ttu-id="17ebd-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="17ebd-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="17ebd-110">U + 0000-U + FFFF</span><span class="sxs-lookup"><span data-stu-id="17ebd-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="17ebd-111">Unicode 16 bit karakter</span><span class="sxs-lookup"><span data-stu-id="17ebd-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="17ebd-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="17ebd-112">Literals</span></span>

<span data-ttu-id="17ebd-113">@No__t-0 türündeki sabitler, karakter sabit değerleri, onaltılık kaçış dizisi veya Unicode temsili olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="17ebd-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="17ebd-114">İntegral karakter kodlarını da çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17ebd-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="17ebd-115">Aşağıdaki örnekte, `char` dizisinin dört öğesi, `X` karakteriyle birlikte başlatılır:</span><span class="sxs-lookup"><span data-stu-id="17ebd-115">In the following example, the four elements of an array of `char` are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="17ebd-116">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="17ebd-116">Conversions</span></span>

<span data-ttu-id="17ebd-117">@No__t-0 örtük olarak [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [Double](../builtin-types/floating-point-numeric-types.md)veya [Decimal](../builtin-types/floating-point-numeric-types.md)'a dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="17ebd-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md), or [decimal](../builtin-types/floating-point-numeric-types.md).</span></span> <span data-ttu-id="17ebd-118">Ancak, diğer türlerden `char` türüne örtük dönüştürmeler yoktur.</span><span class="sxs-lookup"><span data-stu-id="17ebd-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="17ebd-119">@No__t-0 türü `char` değerleriyle çalışmak için birkaç statik yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="17ebd-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="17ebd-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="17ebd-120">C# language specification</span></span>  

<span data-ttu-id="17ebd-121">Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Integral türleri](~/_csharplang/spec/types.md#integral-types) .</span><span class="sxs-lookup"><span data-stu-id="17ebd-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="17ebd-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="17ebd-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="17ebd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17ebd-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="17ebd-124">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="17ebd-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="17ebd-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="17ebd-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="17ebd-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="17ebd-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="17ebd-127">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="17ebd-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="17ebd-128">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="17ebd-128">Built-In Types Table</span></span>](./built-in-types-table.md)
- [<span data-ttu-id="17ebd-129">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="17ebd-129">Implicit Numeric Conversions Table</span></span>](./implicit-numeric-conversions-table.md)
- [<span data-ttu-id="17ebd-130">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="17ebd-130">Explicit Numeric Conversions Table</span></span>](./explicit-numeric-conversions-table.md)
- [<span data-ttu-id="17ebd-131">Dizeler</span><span class="sxs-lookup"><span data-stu-id="17ebd-131">Strings</span></span>](../../programming-guide/strings/index.md)

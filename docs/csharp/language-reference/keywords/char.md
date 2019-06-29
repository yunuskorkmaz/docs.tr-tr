---
title: char anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 0b4f04a1ba6244373e36cc6a6188edabe33ec453
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424338"
---
# <a name="char-c-reference"></a><span data-ttu-id="0dd02-102">char (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0dd02-102">char (C# Reference)</span></span>

<span data-ttu-id="0dd02-103">`char` Örneği bildirmek için anahtar sözcüğü kullanılır <xref:System.Char?displayProperty=nameWithType> yapısı, .NET Framework, Unicode karakterini temsil etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0dd02-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="0dd02-104">Değerini bir `Char` nesnedir (sıra) 16 bit sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="0dd02-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="0dd02-105">Unicode karakterler yazma dillerinin ve dünyanın en iyi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0dd02-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="0dd02-106">Tür</span><span class="sxs-lookup"><span data-stu-id="0dd02-106">Type</span></span>|<span data-ttu-id="0dd02-107">Aralık</span><span class="sxs-lookup"><span data-stu-id="0dd02-107">Range</span></span>|<span data-ttu-id="0dd02-108">Boyut</span><span class="sxs-lookup"><span data-stu-id="0dd02-108">Size</span></span>|<span data-ttu-id="0dd02-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="0dd02-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="0dd02-110">U + 0000'u + FFFF için</span><span class="sxs-lookup"><span data-stu-id="0dd02-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="0dd02-111">Unicode 16-bit karakteri</span><span class="sxs-lookup"><span data-stu-id="0dd02-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="0dd02-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="0dd02-112">Literals</span></span>

<span data-ttu-id="0dd02-113">Sabitleri `char` tür karakter değişmez değerleri, onaltılık çıkış dizisi veya Unicode gösterimi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="0dd02-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="0dd02-114">Ayrıca, integral karakter kodlarını çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dd02-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="0dd02-115">Aşağıdaki örnekte dört `char` değişkenleri, aynı karakterle başlatılır `X`:</span><span class="sxs-lookup"><span data-stu-id="0dd02-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="0dd02-116">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="0dd02-116">Conversions</span></span>

<span data-ttu-id="0dd02-117">A `char` örtük olarak dönüştürülebilir [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="0dd02-117">A `char` can be implicitly converted to [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="0dd02-118">Ancak, diğer türlerinden herhangi bir örtük dönüştürme vardır `char` türü.</span><span class="sxs-lookup"><span data-stu-id="0dd02-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="0dd02-119"><xref:System.Char?displayProperty=nameWithType> Türü ile çalışmak için birkaç statik yöntemler sağlar `char` değerleri.</span><span class="sxs-lookup"><span data-stu-id="0dd02-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0dd02-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0dd02-120">C# language specification</span></span>  

<span data-ttu-id="0dd02-121">Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0dd02-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="0dd02-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="0dd02-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="0dd02-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd02-123">See also</span></span>

- <xref:System.Char>
- [<span data-ttu-id="0dd02-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0dd02-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="0dd02-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0dd02-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0dd02-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0dd02-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="0dd02-127">Tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="0dd02-127">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="0dd02-128">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0dd02-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="0dd02-129">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0dd02-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="0dd02-130">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0dd02-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [<span data-ttu-id="0dd02-131">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="0dd02-131">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
- [<span data-ttu-id="0dd02-132">Dizeler</span><span class="sxs-lookup"><span data-stu-id="0dd02-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

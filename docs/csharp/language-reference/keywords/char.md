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
ms.openlocfilehash: 6acb40117c4f59deb084965cb3db9e4a96f7f61a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242353"
---
# <a name="char-c-reference"></a><span data-ttu-id="601f4-102">char (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="601f4-102">char (C# Reference)</span></span>

<span data-ttu-id="601f4-103">`char` Örneği bildirmek için anahtar sözcüğü kullanılır <xref:System.Char?displayProperty=nameWithType> yapısı, .NET Framework, Unicode karakterini temsil etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="601f4-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="601f4-104">Değerini bir `Char` nesnedir (sıra) 16 bit sayısal değer.</span><span class="sxs-lookup"><span data-stu-id="601f4-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="601f4-105">Unicode karakterler yazma dillerinin ve dünyanın en iyi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="601f4-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="601f4-106">Tür</span><span class="sxs-lookup"><span data-stu-id="601f4-106">Type</span></span>|<span data-ttu-id="601f4-107">Aralık</span><span class="sxs-lookup"><span data-stu-id="601f4-107">Range</span></span>|<span data-ttu-id="601f4-108">Boyut</span><span class="sxs-lookup"><span data-stu-id="601f4-108">Size</span></span>|<span data-ttu-id="601f4-109">.NET türü</span><span class="sxs-lookup"><span data-stu-id="601f4-109">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="601f4-110">U + 0000'u + FFFF için</span><span class="sxs-lookup"><span data-stu-id="601f4-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="601f4-111">Unicode 16-bit karakteri</span><span class="sxs-lookup"><span data-stu-id="601f4-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="601f4-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="601f4-112">Literals</span></span>

<span data-ttu-id="601f4-113">Sabitleri `char` tür karakter değişmez değerleri, onaltılık çıkış dizisi veya Unicode gösterimi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="601f4-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="601f4-114">Ayrıca, integral karakter kodlarını çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="601f4-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="601f4-115">Aşağıdaki örnekte dört `char` değişkenleri, aynı karakterle başlatılır `X`:</span><span class="sxs-lookup"><span data-stu-id="601f4-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="601f4-116">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="601f4-116">Conversions</span></span>

<span data-ttu-id="601f4-117">A `char` örtük olarak dönüştürülebilir [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="601f4-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="601f4-118">Ancak, diğer türlerinden herhangi bir örtük dönüştürme vardır `char` türü.</span><span class="sxs-lookup"><span data-stu-id="601f4-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="601f4-119"><xref:System.Char?displayProperty=nameWithType> Türü ile çalışmak için birkaç statik yöntemler sağlar `char` değerleri.</span><span class="sxs-lookup"><span data-stu-id="601f4-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="601f4-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="601f4-120">C# language specification</span></span>  

<span data-ttu-id="601f4-121">Daha fazla bilgi için [Integral türleri](~/_csharplang/spec/types.md#integral-types) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="601f4-121">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="601f4-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="601f4-122">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="601f4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="601f4-123">See also</span></span>

- <xref:System.Char>  
- [<span data-ttu-id="601f4-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="601f4-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="601f4-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="601f4-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="601f4-126">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="601f4-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="601f4-127">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="601f4-127">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="601f4-128">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="601f4-128">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="601f4-129">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="601f4-129">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="601f4-130">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="601f4-130">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [<span data-ttu-id="601f4-131">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="601f4-131">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
- [<span data-ttu-id="601f4-132">Dizeler</span><span class="sxs-lookup"><span data-stu-id="601f4-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
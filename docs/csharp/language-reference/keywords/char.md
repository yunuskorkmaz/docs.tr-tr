---
title: char anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 4839cacfdc78abc45afc1c59652b944be4863877
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948374"
---
# <a name="char-c-reference"></a><span data-ttu-id="79d13-102">char (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="79d13-102">char (C# Reference)</span></span>

<span data-ttu-id="79d13-103">`char` Örneği bildirmek için kullanılan anahtar sözcüğü <xref:System.Char?displayProperty=nameWithType> Unicode karakteri temsil etmesi için .NET Framework kullanan yapısı.</span><span class="sxs-lookup"><span data-stu-id="79d13-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="79d13-104">Değeri bir `Char` nesnesi bir 16 bit sayısal (sıra) değerdir.</span><span class="sxs-lookup"><span data-stu-id="79d13-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>

 <span data-ttu-id="79d13-105">Unicode karakterler, dünyanın her yazılı dilleri çoğunu göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79d13-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>

|<span data-ttu-id="79d13-106">Tür</span><span class="sxs-lookup"><span data-stu-id="79d13-106">Type</span></span>|<span data-ttu-id="79d13-107">Aralık</span><span class="sxs-lookup"><span data-stu-id="79d13-107">Range</span></span>|<span data-ttu-id="79d13-108">Boyut</span><span class="sxs-lookup"><span data-stu-id="79d13-108">Size</span></span>|<span data-ttu-id="79d13-109">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="79d13-109">.NET Framework type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="79d13-110">U + U + FFFF 0000</span><span class="sxs-lookup"><span data-stu-id="79d13-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="79d13-111">Unicode 16 bit karakter</span><span class="sxs-lookup"><span data-stu-id="79d13-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="79d13-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="79d13-112">Literals</span></span>

<span data-ttu-id="79d13-113">Sabitleri `char` türü karakter değişmez değerleri, onaltılık çıkış dizisi veya Unicode gösterimi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="79d13-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="79d13-114">Ayrıca, tam sayı karakter kodları çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79d13-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="79d13-115">Aşağıdaki örnekte dört `char` değişkenleri aynı karakterle başlatılmış `X`:</span><span class="sxs-lookup"><span data-stu-id="79d13-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a><span data-ttu-id="79d13-116">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="79d13-116">Conversions</span></span>

<span data-ttu-id="79d13-117">A `char` örtük olarak dönüştürülebilir [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="79d13-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="79d13-118">Ancak, diğer türlerinden hiçbir örtük dönüşümler vardır `char` türü.</span><span class="sxs-lookup"><span data-stu-id="79d13-118">However, there are no implicit conversions from other types to the `char` type.</span></span>

<span data-ttu-id="79d13-119"><xref:System.Char?displayProperty=nameWithType> Türü ile çalışmak için birkaç statik yöntemler sağlar `char` değerleri.</span><span class="sxs-lookup"><span data-stu-id="79d13-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="79d13-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="79d13-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="79d13-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79d13-121">See also</span></span>

<xref:System.Char>  
[<span data-ttu-id="79d13-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="79d13-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="79d13-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="79d13-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="79d13-124">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="79d13-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="79d13-125">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="79d13-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
[<span data-ttu-id="79d13-126">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="79d13-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[<span data-ttu-id="79d13-127">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="79d13-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[<span data-ttu-id="79d13-128">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="79d13-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
[<span data-ttu-id="79d13-129">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="79d13-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
[<span data-ttu-id="79d13-130">Dizeler</span><span class="sxs-lookup"><span data-stu-id="79d13-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
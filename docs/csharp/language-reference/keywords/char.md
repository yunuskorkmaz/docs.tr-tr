---
title: "char (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords: char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 41f672e9b12481fa5cce78015e95d2c5245a26db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="char-c-reference"></a><span data-ttu-id="ffe18-102">char (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ffe18-102">char (C# Reference)</span></span>
<span data-ttu-id="ffe18-103">`char` Örneği bildirmek için kullanılan anahtar sözcüğü <xref:System.Char?displayProperty=nameWithType> Unicode karakteri temsil etmesi için .NET Framework kullanan yapısı.</span><span class="sxs-lookup"><span data-stu-id="ffe18-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="ffe18-104">Değeri bir `Char` nesnesi bir 16 bit sayısal (sıra) değerdir.</span><span class="sxs-lookup"><span data-stu-id="ffe18-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="ffe18-105">Unicode karakterler, dünyanın her yazılı dilleri çoğunu göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ffe18-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="ffe18-106">Tür</span><span class="sxs-lookup"><span data-stu-id="ffe18-106">Type</span></span>|<span data-ttu-id="ffe18-107">Aralık</span><span class="sxs-lookup"><span data-stu-id="ffe18-107">Range</span></span>|<span data-ttu-id="ffe18-108">Boyut</span><span class="sxs-lookup"><span data-stu-id="ffe18-108">Size</span></span>|<span data-ttu-id="ffe18-109">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="ffe18-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="ffe18-110">U + U + FFFF 0000</span><span class="sxs-lookup"><span data-stu-id="ffe18-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="ffe18-111">Unicode 16 bit karakter</span><span class="sxs-lookup"><span data-stu-id="ffe18-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="ffe18-112">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="ffe18-112">Literals</span></span>  
 <span data-ttu-id="ffe18-113">Sabitleri `char` türü karakter değişmez değerleri, onaltılık çıkış dizisi veya Unicode gösterimi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="ffe18-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="ffe18-114">Ayrıca, tam sayı karakter kodları çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffe18-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="ffe18-115">Aşağıdaki örnekte dört `char` değişkenleri aynı karakterle başlatılmış `X`:</span><span class="sxs-lookup"><span data-stu-id="ffe18-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a><span data-ttu-id="ffe18-116">Dönüşümler</span><span class="sxs-lookup"><span data-stu-id="ffe18-116">Conversions</span></span>  
 <span data-ttu-id="ffe18-117">A `char` örtük olarak dönüştürülebilir [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), veya [ondalık](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="ffe18-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="ffe18-118">Ancak, diğer türlerinden hiçbir örtük dönüşümler vardır `char` türü.</span><span class="sxs-lookup"><span data-stu-id="ffe18-118">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="ffe18-119"><xref:System.Char?displayProperty=nameWithType> Türü ile çalışmak için birkaç statik yöntemler sağlar `char` değerleri.</span><span class="sxs-lookup"><span data-stu-id="ffe18-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ffe18-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="ffe18-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ffe18-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffe18-121">See Also</span></span>  
 <xref:System.Char>  
 [<span data-ttu-id="ffe18-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ffe18-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ffe18-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ffe18-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ffe18-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ffe18-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ffe18-125">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="ffe18-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="ffe18-126">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="ffe18-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="ffe18-127">Örtük sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="ffe18-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="ffe18-128">Açık sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="ffe18-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="ffe18-129">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="ffe18-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="ffe18-130">Dizeleri</span><span class="sxs-lookup"><span data-stu-id="ffe18-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

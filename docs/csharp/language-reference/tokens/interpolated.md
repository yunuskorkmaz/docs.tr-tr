---
title: $ - dize ilişkilendirme (C# Başvurusu)
description: Dize ilişkilendirme daha geleneksel dize bileşik biçimlendirme dizesi çıkış biçimlendirmek için daha okunabilir ve kullanışlı bir sözdizimi sağlar.
ms.date: 03/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cabb40c9c449780c8c2a504aad3e53938e2ed957
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="0a021-103">$ - dize ilişkilendirme (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0a021-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="0a021-104">`$` Özel karakter tanımlayan bir dize sabit değeri olarak bir *Ara değerli dize*.</span><span class="sxs-lookup"><span data-stu-id="0a021-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="0a021-105">Ara değerli bir dize içeren bir şablon dize gibi görünüyor *Ara değerli ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="0a021-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span> <span data-ttu-id="0a021-106">Ara değerli dize Sonuç dizesini çözümlendiğinde Ara değerli ifadelerle öğeleri ifade sonuçları dize gösterimlerini tarafından değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a021-106">When the interpolated string is resolved to the result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="0a021-107">Bu özellik, C# 6 ve sonraki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a021-107">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="0a021-108">Dize ilişkilendirme daha biçimlendirilmiş dizeler oluşturmak için daha okunabilir ve kullanışlı bir sözdizimi sağlar bir [bileşik biçimlendirme dize](../../../standard/base-types/composite-formatting.md) özelliği.</span><span class="sxs-lookup"><span data-stu-id="0a021-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="0a021-109">Aşağıdaki örnek, aynı çıktı oluşturmak için her iki özellik kullanır:</span><span class="sxs-lookup"><span data-stu-id="0a021-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> <span data-ttu-id="0a021-110">Arasında herhangi bir boşluk olamaz `$` ve `"` dize başlar.</span><span class="sxs-lookup"><span data-stu-id="0a021-110">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="0a021-111">Bunun yapılması, derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0a021-111">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="0a021-112">Ara değerli bir ifadenin bir öğesiyle yapısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0a021-112">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="0a021-113">Köşeli parantezler içindeki öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0a021-113">Elements in square brackets are optional.</span></span> <span data-ttu-id="0a021-114">Aşağıdaki tablo her öğeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a021-114">The following table describes each element.</span></span>

|<span data-ttu-id="0a021-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="0a021-115">Element</span></span>|<span data-ttu-id="0a021-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a021-116">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="0a021-117">Biçimlendirilecek bir sonuç almak için değerlendirilecek olan ifade.</span><span class="sxs-lookup"><span data-stu-id="0a021-117">The expression to evaluate to get a result to be formatted.</span></span> <span data-ttu-id="0a021-118">Dize gösterimini `null` sonuç <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a021-118">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="0a021-119">Sabit ifade değeri Ara değerli ifadenin sonucu dize gösterimini en az karakter sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a021-119">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="0a021-120">Pozitif, sağa hizalı dize gösterimi; negatifse, sola hizalı.</span><span class="sxs-lookup"><span data-stu-id="0a021-120">If positive, the string representation is right-aligned; if negative, it is left-aligned.</span></span> <span data-ttu-id="0a021-121">Daha fazla bilgi için bkz: [hizalama bileşen](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="0a021-121">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="0a021-122">İfade sonucunun türü tarafından desteklenen standart veya özel biçim dizesi.</span><span class="sxs-lookup"><span data-stu-id="0a021-122">A standard or custom format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="0a021-123">Daha fazla bilgi için bkz: [biçim dizesi bileşen](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="0a021-123">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="0a021-124">Aşağıdaki örnek, yukarıda açıklanan biçimlendirme isteğe bağlı bileşenler kullanır:</span><span class="sxs-lookup"><span data-stu-id="0a021-124">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

<span data-ttu-id="0a021-125">Bir küme parantezi içerecek şekilde ("{" veya "}") iki küme ayraçları Ara değerli bir dize üretilen metinde kullanmak "{{" veya "}}".</span><span class="sxs-lookup"><span data-stu-id="0a021-125">To include a brace ("{" or "}") in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="0a021-126">Daha fazla bilgi için bkz: [kaçış ayraçlar](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="0a021-126">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="0a021-127">Noktalı virgül (;) özel bir anlamı kullanmak için bir ara değerli ifade öğesi var. gibi bir [koşullu işleç](../operators/conditional-operator.md) Ara değerli bir ifadede bu ifadesi parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="0a021-127">As the colon (:) has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="0a021-128">Aşağıdaki örnekte, ayraç sonuç dizeye dahil etme ve Ara değerli bir ifadede koşullu bir işleç kullanma gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0a021-128">The following example shows how to include a brace into the result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="0a021-129">Harfi harfine dizeler Kullan'ı değiştirilmiş `$` karakter arkasından `@` karakter.</span><span class="sxs-lookup"><span data-stu-id="0a021-129">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="0a021-130">Harfi harfine dizeler hakkında daha fazla bilgi için bkz: [dize](../keywords/string.md) konu.</span><span class="sxs-lookup"><span data-stu-id="0a021-130">For more information about verbatim strings, see the [string](../keywords/string.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="0a021-131">`$` Belirteci önce görünmelidir `@` verbatim Ara değerli dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="0a021-131">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

<span data-ttu-id="0a021-132">Ara değerli bir dizeden üç örtük dönüşümler vardır:</span><span class="sxs-lookup"><span data-stu-id="0a021-132">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="0a021-133">Ara değerli bir dizeye dönüştürme bir <xref:System.String> Ara değerli ifade ile Ara değerli dize çözümlemesi sonucu örneği öğelerini sonuçları düzgün biçimlendirilmiş dize gösterimlerini ile değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="0a021-133">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="0a021-134">Bu dönüştürme geçerli kültürü kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a021-134">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="0a021-135">Ara değerli bir dizeye dönüştürme bir <xref:System.FormattableString> boyunca bileşik biçim dizesi Biçimlendirilecek ifade sonuçlarla temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="0a021-135">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="0a021-136">Kültüre özgü ile birden çok sonuç dizesi oluşturmak için tek bir içerik sağlayan <xref:System.FormattableString> örneği.</span><span class="sxs-lookup"><span data-stu-id="0a021-136">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="0a021-137">Yapmak için aşağıdaki yöntemlerden birini arayın:</span><span class="sxs-lookup"><span data-stu-id="0a021-137">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="0a021-138">A <xref:System.FormattableString.ToString> için bir sonuç dize üreten aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="0a021-138">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="0a021-139">A <xref:System.FormattableString.Invariant%2A> için bir sonuç dize üreten yöntem <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="0a021-139">A <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="0a021-140">A <xref:System.FormattableString.ToString(System.IFormatProvider)> belirtilen kültür için bir sonuç dize üreten yöntem.</span><span class="sxs-lookup"><span data-stu-id="0a021-140">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

1. <span data-ttu-id="0a021-141">Ara değerli bir dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanızı sağlayan örnek dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği.</span><span class="sxs-lookup"><span data-stu-id="0a021-141">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="0a021-142">Aşağıdaki örnek, örtük dönüştürmeye kullanır <xref:System.FormattableString> kültüre özgü sonuç dizesi oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="0a021-142">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

<span data-ttu-id="0a021-143">Dize ilişkilendirme yeniyseniz, denetleme [dize ilişkilendirme C#](../../quick-starts/interpolated-strings.yml) hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="0a021-143">If you are new to the string interpolation, check the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="0a021-144">Daha fazla örnek için bkz: [dize ilişkilendirme Öğreticisi](../../tutorials/string-interpolation.md).</span><span class="sxs-lookup"><span data-stu-id="0a021-144">For more examples, see the [string interpolation tutorial](../../tutorials/string-interpolation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a021-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a021-145">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="0a021-146">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="0a021-146">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="0a021-147">Dizeler</span><span class="sxs-lookup"><span data-stu-id="0a021-147">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="0a021-148">C# Özel Karakterleri</span><span class="sxs-lookup"><span data-stu-id="0a021-148">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)  
 [<span data-ttu-id="0a021-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0a021-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0a021-150">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0a021-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
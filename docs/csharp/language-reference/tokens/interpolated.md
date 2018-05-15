---
title: $ - dize ilişkilendirme (C# Başvurusu)
description: Dize ilişkilendirme daha geleneksel dize bileşik biçimlendirme dizesi çıkış biçimlendirmek için daha okunabilir ve kullanışlı bir sözdizimi sağlar.
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 407ca9e4744ea9be45867a08e87c502821226472
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="618ae-103">$ - dize ilişkilendirme (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="618ae-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="618ae-104">`$` Özel karakter tanımlayan bir dize sabit değeri olarak bir *Ara değerli dize*.</span><span class="sxs-lookup"><span data-stu-id="618ae-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="618ae-105">Ara değerli bir dize içerebilecek bir değişmez dize değeri olan *Ara değerli ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="618ae-105">An interpolated string is a string literal that might contain *interpolated expressions*.</span></span> <span data-ttu-id="618ae-106">Ara değerli bir dize sonucu dizeye çözümlendiğinde Ara değerli ifadelerle öğeleri ifade sonuçları dize gösterimlerini tarafından değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="618ae-106">When an interpolated string is resolved to a result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="618ae-107">Bu özellik, C# 6 ve sonraki sürümlerinde dil kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="618ae-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="618ae-108">Dize ilişkilendirme daha biçimlendirilmiş dizeler oluşturmak için daha okunabilir ve kullanışlı bir sözdizimi sağlar bir [bileşik biçimlendirme dize](../../../standard/base-types/composite-formatting.md) özelliği.</span><span class="sxs-lookup"><span data-stu-id="618ae-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="618ae-109">Aşağıdaki örnek, aynı çıktı oluşturmak için her iki özellik kullanır:</span><span class="sxs-lookup"><span data-stu-id="618ae-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="618ae-110">Ara değerli bir dize yapısı</span><span class="sxs-lookup"><span data-stu-id="618ae-110">Structure of an interpolated string</span></span>

<span data-ttu-id="618ae-111">Bir dize olarak ara değerli bir dize sabit değeri tanımlamak için kendisiyle başına `$` simgesi.</span><span class="sxs-lookup"><span data-stu-id="618ae-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="618ae-112">Arasında herhangi bir boşluk olamaz `$` ve `"` bir değişmez dize değeri başlatır.</span><span class="sxs-lookup"><span data-stu-id="618ae-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="618ae-113">Bunun yapılması, derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="618ae-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="618ae-114">Ara değerli bir ifadenin bir öğesiyle yapısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="618ae-114">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="618ae-115">Köşeli parantezler içindeki öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="618ae-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="618ae-116">Aşağıdaki tabloda her öğesi açıklar:</span><span class="sxs-lookup"><span data-stu-id="618ae-116">The following table describes each element:</span></span>

|<span data-ttu-id="618ae-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="618ae-117">Element</span></span>|<span data-ttu-id="618ae-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="618ae-118">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="618ae-119">Biçimlendirilmiş olması için bir sonuç üreten ifade.</span><span class="sxs-lookup"><span data-stu-id="618ae-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="618ae-120">Dize gösterimini `null` sonuç <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="618ae-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="618ae-121">Sabit ifade değeri Ara değerli ifadenin sonucu dize gösterimini en az karakter sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="618ae-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="618ae-122">Pozitif, sağa hizalı dize gösterimi; negatifse, sola hizalı.</span><span class="sxs-lookup"><span data-stu-id="618ae-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="618ae-123">Daha fazla bilgi için bkz: [hizalama bileşen](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="618ae-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="618ae-124">İfade sonucunun türü tarafından desteklenen bir biçim dizesi.</span><span class="sxs-lookup"><span data-stu-id="618ae-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="618ae-125">Daha fazla bilgi için bkz: [biçim dizesi bileşen](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="618ae-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="618ae-126">Aşağıdaki örnek, yukarıda açıklanan biçimlendirme isteğe bağlı bileşenler kullanır:</span><span class="sxs-lookup"><span data-stu-id="618ae-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="618ae-127">Özel karakterler</span><span class="sxs-lookup"><span data-stu-id="618ae-127">Special characters</span></span>

<span data-ttu-id="618ae-128">Bir küme parantezi dahil etmek için "{" veya "}", iki küme ayraçları Ara değerli bir dize tarafından üretilen metin kullanma "{{" veya "}}".</span><span class="sxs-lookup"><span data-stu-id="618ae-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="618ae-129">Daha fazla bilgi için bkz: [kaçış ayraçlar](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="618ae-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="618ae-130">İki nokta üst üste olarak (":") kullanmak için bir ara değerli ifade öğesinde özel bir anlamı yoktur bir [koşullu işleç](../operators/conditional-operator.md) Ara değerli bir ifadede bu ifadesi parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="618ae-130">As the colon (":") has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="618ae-131">Aşağıdaki örnek, sonuç dizesinde ayraç ekleme ve Ara değerli bir ifadede koşullu bir işleç kullanmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="618ae-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="618ae-132">Harfi harfine Ara değerli bir dize ile başlayan `$` karakter arkasından `@` karakter.</span><span class="sxs-lookup"><span data-stu-id="618ae-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="618ae-133">Harfi harfine dizeler hakkında daha fazla bilgi için bkz: [dize](../keywords/string.md) ve [verbatim tanımlayıcı](verbatim.md) Konular.</span><span class="sxs-lookup"><span data-stu-id="618ae-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="618ae-134">`$` Belirteci önce görünmelidir `@` verbatim Ara değerli dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="618ae-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="618ae-135">Örtük dönüşümler ve belirterek `IFormatProvider` uygulama</span><span class="sxs-lookup"><span data-stu-id="618ae-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="618ae-136">Ara değerli bir dizeden üç örtük dönüşümler vardır:</span><span class="sxs-lookup"><span data-stu-id="618ae-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="618ae-137">Ara değerli bir dizeye dönüştürme bir <xref:System.String> Ara değerli ifade ile Ara değerli dize çözümlemesi sonucu örneği öğelerini sonuçları düzgün biçimlendirilmiş dize gösterimlerini ile değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="618ae-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="618ae-138">Bu dönüştürme geçerli kültürü kullanır.</span><span class="sxs-lookup"><span data-stu-id="618ae-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="618ae-139">Ara değerli bir dizeye dönüştürme bir <xref:System.FormattableString> boyunca bileşik biçim dizesi Biçimlendirilecek ifade sonuçlarla temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="618ae-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="618ae-140">Kültüre özgü ile birden çok sonuç dizesi oluşturmak için tek bir içerik sağlayan <xref:System.FormattableString> örneği.</span><span class="sxs-lookup"><span data-stu-id="618ae-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="618ae-141">Yapmak için aşağıdaki yöntemlerden birini arayın:</span><span class="sxs-lookup"><span data-stu-id="618ae-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="618ae-142">A <xref:System.FormattableString.ToString> için bir sonuç dize üreten aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="618ae-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="618ae-143">Bir <xref:System.FormattableString.Invariant%2A> için bir sonuç dize üreten yöntem <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="618ae-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="618ae-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> belirtilen kültür için bir sonuç dize üreten yöntem.</span><span class="sxs-lookup"><span data-stu-id="618ae-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="618ae-145">Aynı zamanda <xref:System.FormattableString.ToString(System.IFormatProvider)> , kullanıcı tanımlı bir uygulama sunmak amacıyla yöntemi <xref:System.IFormatProvider> özel biçimlendirmeyi destekler arabirimi.</span><span class="sxs-lookup"><span data-stu-id="618ae-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="618ae-146">Daha fazla bilgi için bkz: [özel biçimlendirme ICustomFormatter ile](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="618ae-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="618ae-147">Ara değerli bir dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanızı sağlayan örnek dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği.</span><span class="sxs-lookup"><span data-stu-id="618ae-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="618ae-148">Aşağıdaki örnek, örtük dönüştürmeye kullanır <xref:System.FormattableString> kültüre özgü sonuç dizesi oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="618ae-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="618ae-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="618ae-149">Additional resources</span></span>

<span data-ttu-id="618ae-150">Dize ilişkilendirme yeni istiyorsanız bkz [dize ilişkilendirme C#](../../quick-starts/interpolated-strings.yml) hızlı başlangıç.</span><span class="sxs-lookup"><span data-stu-id="618ae-150">If you are new to string interpolation, see the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="618ae-151">Daha fazla örnek için bkz: [dize ilişkilendirme C#](../../tutorials/string-interpolation.md) Öğreticisi.</span><span class="sxs-lookup"><span data-stu-id="618ae-151">For more examples, see the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="see-also"></a><span data-ttu-id="618ae-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="618ae-152">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="618ae-153">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="618ae-153">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="618ae-154">Dizeler</span><span class="sxs-lookup"><span data-stu-id="618ae-154">Strings</span></span>](../../programming-guide/strings/index.md)  
 [<span data-ttu-id="618ae-155">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="618ae-155">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="618ae-156">C# Özel Karakterleri</span><span class="sxs-lookup"><span data-stu-id="618ae-156">C# Special Characters</span></span>](index.md)  
 [<span data-ttu-id="618ae-157">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="618ae-157">C# Reference</span></span>](../index.md)  
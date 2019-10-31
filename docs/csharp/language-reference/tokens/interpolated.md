---
title: $-dize ilişkilendirme- C# başvuru
ms.custom: seodec18
description: Dize ilişkilendirme, dize çıkışını geleneksel dize bileşik biçimlendirmeden biçimlendirmek için daha okunabilir ve kullanışlı bir sözdizimi sağlar.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 5f0388d90119455833eb6dba6ac808cdc8517865
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101652"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="06fe4-103">$-dize ilişkilendirme (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="06fe4-103">$ - string interpolation (C# reference)</span></span>

<span data-ttu-id="06fe4-104">`$` özel karakter, bir dize sabit değerini, *enterpolasyonlu dize*olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06fe4-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="06fe4-105">Enterpolasyonlu dize, *enterpolasyon ifadeleri*içerebilen bir dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="06fe4-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="06fe4-106">Bir enterpolasyonlu dize bir sonuç dizesine çözümlendiğinde, enterpolasyon ifadesi içeren öğeler, ifade sonuçlarının dize gösterimleriyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="06fe4-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="06fe4-107">Bu özellik C# 6 ' dan itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06fe4-107">This feature is available starting with C# 6.</span></span>

<span data-ttu-id="06fe4-108">Dize ilişkilendirme, [dize bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md) özelliğinden biçimlendirilmiş dizeler oluşturmak için daha okunabilir ve uygun bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="06fe4-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="06fe4-109">Aşağıdaki örnek, aynı çıktıyı üretmek için her iki özelliği de kullanır:</span><span class="sxs-lookup"><span data-stu-id="06fe4-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="06fe4-110">Enterpolasyonlu bir dizenin yapısı</span><span class="sxs-lookup"><span data-stu-id="06fe4-110">Structure of an interpolated string</span></span>

<span data-ttu-id="06fe4-111">Bir dize sabit değerini, enterpolasyonlu bir dize olarak tanımlamak için `$` simgesiyle önüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="06fe4-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="06fe4-112">`$` ve bir dize sabiti Başlatan `"` arasında boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="06fe4-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span>

<span data-ttu-id="06fe4-113">Enterpolasyon ifadesi içeren bir öğenin yapısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="06fe4-113">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="06fe4-114">Köşeli parantezler içindeki öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="06fe4-114">Elements in square brackets are optional.</span></span> <span data-ttu-id="06fe4-115">Aşağıdaki tabloda her öğe açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="06fe4-115">The following table describes each element:</span></span>

|<span data-ttu-id="06fe4-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="06fe4-116">Element</span></span>|<span data-ttu-id="06fe4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06fe4-117">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="06fe4-118">Biçimlendirilecek bir sonuç üreten ifade.</span><span class="sxs-lookup"><span data-stu-id="06fe4-118">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="06fe4-119">`null` dize temsili <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06fe4-119">String representation of `null` is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="06fe4-120">Değeri, ifade sonucunun dize temsilinde minimum karakter sayısını tanımlayan sabit ifade.</span><span class="sxs-lookup"><span data-stu-id="06fe4-120">The constant expression whose value defines the minimum number of characters in the string representation of the expression result.</span></span> <span data-ttu-id="06fe4-121">Pozitif ise, dize temsili sağa hizalanır; negatifse, sola hizalanır.</span><span class="sxs-lookup"><span data-stu-id="06fe4-121">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="06fe4-122">Daha fazla bilgi için bkz. [Hizalama bileşeni](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="06fe4-122">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="06fe4-123">İfade sonucunun türü tarafından desteklenen bir biçim dizesi.</span><span class="sxs-lookup"><span data-stu-id="06fe4-123">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="06fe4-124">Daha fazla bilgi için bkz. [Biçim dize bileşeni](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="06fe4-124">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="06fe4-125">Aşağıdaki örnek, yukarıda açıklanan isteğe bağlı biçimlendirme bileşenlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="06fe4-125">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="06fe4-126">Özel karakterler</span><span class="sxs-lookup"><span data-stu-id="06fe4-126">Special characters</span></span>

<span data-ttu-id="06fe4-127">"{" Veya "}" küme ayracı eklemek için, enterpolasyonlu bir dize tarafından üretilen metinde, "{{" veya "}}" iki küme ayracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="06fe4-127">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="06fe4-128">Daha fazla bilgi için bkz. [kaçış ayraçları](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="06fe4-128">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="06fe4-129">İki nokta üst üste (":"), enterpolasyon ifadesi öğesinde [koşullu bir işleç](../operators/conditional-operator.md) kullanmak için bir ilişkilendirme ifadesinde özel anlamı olduğundan, bu ifadeyi parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="06fe4-129">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="06fe4-130">Aşağıdaki örnek, bir sonuç dizesinde bir küme ayracın nasıl ekleneceğini ve bir ilişkilendirme ifadesinde koşullu işlecin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="06fe4-130">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="06fe4-131">Enterpolasyonlu bir dize `$` karakteriyle başlar ve ardından `@` karakteri gelir.</span><span class="sxs-lookup"><span data-stu-id="06fe4-131">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="06fe4-132">Tam dizeler hakkında daha fazla bilgi için bkz. [dize](../keywords/string.md) ve tam [tanımlayıcı](verbatim.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="06fe4-132">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="06fe4-133">8,0 ile C# başlayarak,`$`ve`@`belirteçlerini dilediğiniz sırada kullanabilirsiniz: her iki `$@"..."`ve`@$"..."`geçerli bir ara değerli dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="06fe4-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="06fe4-134">Önceki C# sürümlerde `$` belirtecinin `@` belirtecinden önce görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="06fe4-134">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a><span data-ttu-id="06fe4-135">Örtük dönüştürmeler ve `IFormatProvider` uygulamasını belirtme</span><span class="sxs-lookup"><span data-stu-id="06fe4-135">Implicit conversions and how to specify `IFormatProvider` implementation</span></span>

<span data-ttu-id="06fe4-136">Enterpolasyonlu bir dizeden üç örtük dönüştürme vardır:</span><span class="sxs-lookup"><span data-stu-id="06fe4-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="06fe4-137">Enterpolasyonlu bir dizenin, sonuçları doğru biçimli dize gösterimlerine göre değiştirilmekte olan enterpolasyon ifade öğeleriyle birlikte bulunan bir <xref:System.String> örneğine dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="06fe4-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="06fe4-138">Bu dönüştürme, ifade sonuçlarını biçimlendirmek için <xref:System.Globalization.CultureInfo.CurrentCulture> kullanır.</span><span class="sxs-lookup"><span data-stu-id="06fe4-138">This conversion uses the <xref:System.Globalization.CultureInfo.CurrentCulture> to format expression results.</span></span>

1. <span data-ttu-id="06fe4-139">Enterpolasyonlu bir dizenin, bir bileşik biçim dizesini temsil eden bir <xref:System.FormattableString> örneğine dönüştürülmesi ve bu ifade, biçimlendirilecek ifade sonuçlarıyla birlikte.</span><span class="sxs-lookup"><span data-stu-id="06fe4-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="06fe4-140">Bu, tek bir <xref:System.FormattableString> örneğinden kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="06fe4-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="06fe4-141">Bunu yapmak için aşağıdaki yöntemlerden birini çağırın:</span><span class="sxs-lookup"><span data-stu-id="06fe4-141">To do that, call one of the following methods:</span></span>

      - <span data-ttu-id="06fe4-142"><xref:System.Globalization.CultureInfo.CurrentCulture>için sonuç dizesi üreten <xref:System.FormattableString.ToString> aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="06fe4-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="06fe4-143"><xref:System.Globalization.CultureInfo.InvariantCulture>için sonuç dizesi üreten <xref:System.FormattableString.Invariant%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06fe4-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="06fe4-144">Belirtilen kültür için sonuç dizesi üreten <xref:System.FormattableString.ToString(System.IFormatProvider)> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06fe4-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="06fe4-145">Ayrıca, özel biçimlendirmeyi destekleyen <xref:System.IFormatProvider> arabirimine yönelik kullanıcı tanımlı bir uygulama sağlamak için <xref:System.FormattableString.ToString(System.IFormatProvider)> yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06fe4-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="06fe4-146">Daha fazla bilgi için [.net makalesindeki biçimlendirme türleri](../../../standard/base-types/formatting-types.md) konusunun [ICustomFormatter ile özel biçimlendirme](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="06fe4-146">For more information, see the [Custom formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) section of the [Formatting types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

1. <span data-ttu-id="06fe4-147">Enterpolasyonlu bir dizenin tek bir <xref:System.IFormattable> örneğinden kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza olanak sağlayan bir <xref:System.IFormattable> örneğine dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="06fe4-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="06fe4-148">Aşağıdaki örnek, kültüre özgü sonuç dizeleri oluşturmak için <xref:System.FormattableString> için örtük dönüştürmeyi kullanır:</span><span class="sxs-lookup"><span data-stu-id="06fe4-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="06fe4-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="06fe4-149">Additional resources</span></span>

<span data-ttu-id="06fe4-150">Dize ilişkilendirme konusunda yeni bir adım daha kullanıyorsanız etkileşimli öğreticide [dize ilişkilendirmeyi C# ](../../tutorials/exploration/interpolated-strings.yml) inceleyin.</span><span class="sxs-lookup"><span data-stu-id="06fe4-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="06fe4-151">Ayrıca, biçimlendirilen dizeleri oluşturmak için, enterpolasyonlu dizelerin nasıl kullanılacağını gösteren öğreticideki başka bir [dize ilişkilendirmeyi C# ](../../tutorials/string-interpolation.md) da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06fe4-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="06fe4-152">Enterpolasyonlu dizelerin derlenmesi</span><span class="sxs-lookup"><span data-stu-id="06fe4-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="06fe4-153">Bir enterpolasyonlu dize tür `string`, genellikle bir <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi çağrısına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="06fe4-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="06fe4-154">Çözümlenen davranış birleştirme ile eşdeğer olacaksa, derleyici <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType> ile değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="06fe4-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="06fe4-155">Enterpolasyonlu bir dize <xref:System.IFormattable> veya <xref:System.FormattableString>tür içeriyorsa, derleyici <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> yöntemine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06fe4-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="06fe4-156">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="06fe4-156">C# language specification</span></span>

<span data-ttu-id="06fe4-157">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [enterpolasyonlu dizeler](~/_csharplang/spec/expressions.md#interpolated-strings) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="06fe4-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06fe4-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06fe4-158">See also</span></span>

- [<span data-ttu-id="06fe4-159">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="06fe4-159">C# reference</span></span>](../index.md)
- [<span data-ttu-id="06fe4-160">C# özel karakterleri</span><span class="sxs-lookup"><span data-stu-id="06fe4-160">C# special characters</span></span>](index.md)
- [<span data-ttu-id="06fe4-161">Dizeler</span><span class="sxs-lookup"><span data-stu-id="06fe4-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="06fe4-162">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="06fe4-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="06fe4-163">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="06fe4-163">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>

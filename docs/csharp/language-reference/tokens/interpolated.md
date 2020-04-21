---
title: $ - dize enterpolasyonu - C# referans
description: Dize enterpolasyonu, dize çıktısını geleneksel dize bileşik biçimlendirmesine göre biçimlendirmek için daha okunabilir ve kullanışlı bir sözdizimi sağlar.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 2b95fa5fe5cecd4825e8c17a33f7795c6c9480c6
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738370"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="23f0b-103">$ - dize enterpolasyonu (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="23f0b-103">$ - string interpolation (C# reference)</span></span>

<span data-ttu-id="23f0b-104">Özel `$` karakter, bir dize literal *bir interpolated dize*olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="23f0b-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="23f0b-105">Enterpolasyonlu dize, *enterpolasyon ifadeleri*içerebilecek bir dize dir.</span><span class="sxs-lookup"><span data-stu-id="23f0b-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="23f0b-106">Enterpolasyonlu bir dize bir sonuç dizesine çözüldüğünde, enterpolasyon ifadeleri içeren öğeler ifade sonuçlarının dize gösterimleri ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="23f0b-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="23f0b-107">Bu özellik C# 6 ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="23f0b-107">This feature is available starting with C# 6.</span></span>

<span data-ttu-id="23f0b-108">Dize enterpolasyonu, [dize bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md) özelliğinden daha biçimlendirilmiş dizeleri oluşturmak için daha okunabilir ve kullanışlı bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="23f0b-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="23f0b-109">Aşağıdaki örnek, aynı çıktıyı üretmek için her iki özelliği de kullanır:</span><span class="sxs-lookup"><span data-stu-id="23f0b-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="23f0b-110">İnterpolated dize yapısı</span><span class="sxs-lookup"><span data-stu-id="23f0b-110">Structure of an interpolated string</span></span>

<span data-ttu-id="23f0b-111">Bir dize literal bir interpolated dize olarak `$` tanımlamak için, sembolü ile prepend.</span><span class="sxs-lookup"><span data-stu-id="23f0b-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="23f0b-112">Bir dize harfi ile `$` başlayan `"` arasında herhangi bir beyaz boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="23f0b-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span>

<span data-ttu-id="23f0b-113">Enterpolasyon ifadesi olan bir öğenin yapısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="23f0b-113">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="23f0b-114">Köşeli parantezler içindeki öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="23f0b-114">Elements in square brackets are optional.</span></span> <span data-ttu-id="23f0b-115">Aşağıdaki tabloda her öğe açıklanır:</span><span class="sxs-lookup"><span data-stu-id="23f0b-115">The following table describes each element:</span></span>

|<span data-ttu-id="23f0b-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="23f0b-116">Element</span></span>|<span data-ttu-id="23f0b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23f0b-117">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="23f0b-118">Biçimlendirilecek bir sonuç üreten ifade.</span><span class="sxs-lookup"><span data-stu-id="23f0b-118">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="23f0b-119">String `null` gösterimi <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="23f0b-119">String representation of `null` is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="23f0b-120">İfade sonucunun dize gösterimindeki en az karakter sayısını tanımlayan değer olan sabit ifade.</span><span class="sxs-lookup"><span data-stu-id="23f0b-120">The constant expression whose value defines the minimum number of characters in the string representation of the expression result.</span></span> <span data-ttu-id="23f0b-121">Pozitifse, dize gösterimi doğru hizalanmış; negatif ise, sol hizalı.</span><span class="sxs-lookup"><span data-stu-id="23f0b-121">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="23f0b-122">Daha fazla bilgi için [Hizalama Bileşeni'ne](../../../standard/base-types/composite-formatting.md#alignment-component)bakın.</span><span class="sxs-lookup"><span data-stu-id="23f0b-122">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="23f0b-123">İfade sonucunun türü tarafından desteklenen bir biçim dizesi.</span><span class="sxs-lookup"><span data-stu-id="23f0b-123">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="23f0b-124">Daha fazla bilgi için [Bkz. Biçim Dize Bileşeni.](../../../standard/base-types/composite-formatting.md#format-string-component)</span><span class="sxs-lookup"><span data-stu-id="23f0b-124">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="23f0b-125">Aşağıdaki örnekte, yukarıda açıklanan isteğe bağlı biçimlendirme bileşenleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="23f0b-125">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="23f0b-126">Özel karakterler</span><span class="sxs-lookup"><span data-stu-id="23f0b-126">Special characters</span></span>

<span data-ttu-id="23f0b-127">Enterpolasyonlu bir dize tarafından üretilen metne "{" veya "}" bir ayraç eklemek için "{{" veya "}}" olmak üzere iki ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="23f0b-127">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="23f0b-128">Daha fazla bilgi için [bkz.](../../../standard/base-types/composite-formatting.md#escaping-braces)</span><span class="sxs-lookup"><span data-stu-id="23f0b-128">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="23f0b-129">Üst üste (":") bir enterpolasyon ifade öğesinde özel bir anlamı olduğundan, bir enterpolasyon ifadesinde [koşullu işleç](../operators/conditional-operator.md) kullanmak için, bu ifadeyi parantez içine alar.</span><span class="sxs-lookup"><span data-stu-id="23f0b-129">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="23f0b-130">Aşağıdaki örnek, bir sonuç dizesine nasıl bir ayraç eklenmeyi ve bir enterpolasyon ifadesinde koşullu işlecinin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="23f0b-130">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="23f0b-131">İnterpolated verbatim dize `$` `@` karakter tarafından takip karakter ile başlar.</span><span class="sxs-lookup"><span data-stu-id="23f0b-131">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="23f0b-132">Kelime nin dizeleri hakkında daha fazla bilgi için [dize](../builtin-types/reference-types.md) ve [tam olarak tanımlayıcı](verbatim.md) konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="23f0b-132">For more information about verbatim strings, see the [string](../builtin-types/reference-types.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="23f0b-133">C# 8.0 ile başlayarak, `$` `@` belirteçleri ve belirteçleri herhangi bir sırada kullanabilirsiniz: her ikisi de `$@"..."` ve `@$"..."` geçerli enterpolasyonlu kelime dizeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="23f0b-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="23f0b-134">Önceki C# sürümlerinde `$` belirteç belirteçten `@` önce görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="23f0b-134">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a><span data-ttu-id="23f0b-135">Örtülü dönüşümler ve `IFormatProvider` uygulamanın nasıl belirtilir</span><span class="sxs-lookup"><span data-stu-id="23f0b-135">Implicit conversions and how to specify `IFormatProvider` implementation</span></span>

<span data-ttu-id="23f0b-136">Enterpolasyonlu bir dizeden üç örtük dönüşüm vardır:</span><span class="sxs-lookup"><span data-stu-id="23f0b-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="23f0b-137">Enterpolasyonlu bir dize, enterpolasyon ifade öğelerinin sonuçlarının düzgün biçimlendirilmiş dize gösterimleriyle değiştirildiği enterpolasyon lu dize çözünürlüğünün sonucu olan bir <xref:System.String> örne dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="23f0b-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="23f0b-138">Bu dönüştürme <xref:System.Globalization.CultureInfo.CurrentCulture> ifade sonuçlarını biçimlendirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="23f0b-138">This conversion uses the <xref:System.Globalization.CultureInfo.CurrentCulture> to format expression results.</span></span>

1. <span data-ttu-id="23f0b-139">Enterpolasyonlu bir dizenin biçimlendirilecek ifade sonuçlarıyla birlikte bileşik biçim dizesini temsil eden bir <xref:System.FormattableString> örne dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="23f0b-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="23f0b-140">Bu, tek <xref:System.FormattableString> bir örnekten kültüre özgü içeriğe sahip birden çok sonuç dizesi oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="23f0b-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="23f0b-141">Bunu yapmak için aşağıdaki yöntemlerden birini arayın:</span><span class="sxs-lookup"><span data-stu-id="23f0b-141">To do that, call one of the following methods:</span></span>

      - <span data-ttu-id="23f0b-142"><xref:System.Globalization.CultureInfo.CurrentCulture>Için <xref:System.FormattableString.ToString> bir sonuç dizesi üreten aşırı yük.</span><span class="sxs-lookup"><span data-stu-id="23f0b-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="23f0b-143"><xref:System.Globalization.CultureInfo.InvariantCulture>Için <xref:System.FormattableString.Invariant%2A> bir sonuç dizesi üreten bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="23f0b-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="23f0b-144">Belirli <xref:System.FormattableString.ToString(System.IFormatProvider)> bir kültür için sonuç dizesi üreten bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="23f0b-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="23f0b-145">Yöntemi, <xref:System.FormattableString.ToString(System.IFormatProvider)> özel biçimlendirmeyi destekleyen <xref:System.IFormatProvider> arabirimin kullanıcı tanımlı bir uygulamasını sağlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23f0b-145">You can also use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="23f0b-146">Daha fazla bilgi [için,.NET makalesindeki Biçimlendirme türlerinin](../../../standard/base-types/formatting-types.md) [ICustomFormatter bölümüyle Özel biçimlendirmebölümüne](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) bakın.</span><span class="sxs-lookup"><span data-stu-id="23f0b-146">For more information, see the [Custom formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) section of the [Formatting types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

1. <span data-ttu-id="23f0b-147">Enterpolasyonlu bir dizenin, tek <xref:System.IFormattable> <xref:System.IFormattable> bir örnekten kültüre özgü içeriğe sahip birden çok sonuç dizesi oluşturmanıza olanak tanıyan bir örne dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="23f0b-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="23f0b-148">Aşağıdaki örnek, kültüre <xref:System.FormattableString> özgü sonuç dizeleri oluşturmak için örtük dönüştürme kullanır:</span><span class="sxs-lookup"><span data-stu-id="23f0b-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="23f0b-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="23f0b-149">Additional resources</span></span>

<span data-ttu-id="23f0b-150">Dize enterpolasyonunda yeniyseniz, C# etkileşimli [öğreticideki String enterpolasyonuna](../../tutorials/exploration/interpolated-strings.yml) bakın.</span><span class="sxs-lookup"><span data-stu-id="23f0b-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="23f0b-151">Ayrıca, biçimlendirilmiş dizeleri oluşturmak için enterpolasyonlu dizeleri nasıl kullanılacağını gösteren C# öğreticibaşka bir [String enterpolasyon](../../tutorials/string-interpolation.md) kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23f0b-151">You can also check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="23f0b-152">Enterpolasyonlu dizelerin derlemi</span><span class="sxs-lookup"><span data-stu-id="23f0b-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="23f0b-153">Enterpolasyonlu bir dize `string`türüne sahipse, <xref:System.String.Format%2A?displayProperty=nameWithType> genellikle bir yöntem çağrısına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="23f0b-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="23f0b-154">Derleyici, çözümlenen <xref:System.String.Concat%2A?displayProperty=nameWithType> davranışın birliktemeye eşdeğer olup olmadığını değiştirebilir. <xref:System.String.Format%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="23f0b-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="23f0b-155">Enterpolasyonlu bir dize <xref:System.IFormattable> <xref:System.FormattableString>türü varsa veya derleyici <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> yönteme bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23f0b-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="23f0b-156">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="23f0b-156">C# language specification</span></span>

<span data-ttu-id="23f0b-157">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Enterpolasyonlu dizeleri](~/_csharplang/spec/expressions.md#interpolated-strings) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="23f0b-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="23f0b-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23f0b-158">See also</span></span>

- [<span data-ttu-id="23f0b-159">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="23f0b-159">C# reference</span></span>](../index.md)
- [<span data-ttu-id="23f0b-160">C# özel karakterleri</span><span class="sxs-lookup"><span data-stu-id="23f0b-160">C# special characters</span></span>](index.md)
- [<span data-ttu-id="23f0b-161">Dizeler</span><span class="sxs-lookup"><span data-stu-id="23f0b-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="23f0b-162">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="23f0b-162">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="23f0b-163">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="23f0b-163">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>

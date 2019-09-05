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
ms.author: ronpet
ms.openlocfilehash: 53a8938a373136df65e23c162b94c4d8dc1f30b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253860"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="ee41e-103">$-dize ilişkilendirme (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="ee41e-103">$ - string interpolation (C# reference)</span></span>

<span data-ttu-id="ee41e-104">Özel `$` karakter, bir dize sabit değerini, *enterpolasyonlu dize*olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee41e-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="ee41e-105">Enterpolasyonlu dize, *enterpolasyon ifadeleri*içerebilen bir dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="ee41e-105">An interpolated string is a string literal that might contain *interpolation expressions*.</span></span> <span data-ttu-id="ee41e-106">Bir enterpolasyonlu dize bir sonuç dizesine çözümlendiğinde, enterpolasyon ifadesi içeren öğeler, ifade sonuçlarının dize gösterimleriyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ee41e-106">When an interpolated string is resolved to a result string, items with interpolation expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="ee41e-107">Bu özellik C# 6 ' dan itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee41e-107">This feature is available starting with C# 6.</span></span>

<span data-ttu-id="ee41e-108">Dize ilişkilendirme, [dize bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md) özelliğinden biçimlendirilmiş dizeler oluşturmak için daha okunabilir ve uygun bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee41e-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="ee41e-109">Aşağıdaki örnek, aynı çıktıyı üretmek için her iki özelliği de kullanır:</span><span class="sxs-lookup"><span data-stu-id="ee41e-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="ee41e-110">Enterpolasyonlu bir dizenin yapısı</span><span class="sxs-lookup"><span data-stu-id="ee41e-110">Structure of an interpolated string</span></span>

<span data-ttu-id="ee41e-111">Bir dize sabit değerini, enterpolasyonlu bir dize olarak tanımlamak için, `$` simgeyi simgesiyle önüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee41e-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="ee41e-112">`$` Ve arasındabirdizesabitiBaşlatanboşlukolamaz.`"`</span><span class="sxs-lookup"><span data-stu-id="ee41e-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span>

<span data-ttu-id="ee41e-113">Enterpolasyon ifadesi içeren bir öğenin yapısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ee41e-113">The structure of an item with an interpolation expression is as follows:</span></span>

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="ee41e-114">Köşeli parantezler içindeki öğeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ee41e-114">Elements in square brackets are optional.</span></span> <span data-ttu-id="ee41e-115">Aşağıdaki tabloda her öğe açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="ee41e-115">The following table describes each element:</span></span>

|<span data-ttu-id="ee41e-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee41e-116">Element</span></span>|<span data-ttu-id="ee41e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee41e-117">Description</span></span>|
|-------------|-----------------|
|`interpolationExpression`|<span data-ttu-id="ee41e-118">Biçimlendirilecek bir sonuç üreten ifade.</span><span class="sxs-lookup"><span data-stu-id="ee41e-118">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="ee41e-119">`null` Öğesinin<xref:System.String.Empty?displayProperty=nameWithType>dize temsili.</span><span class="sxs-lookup"><span data-stu-id="ee41e-119">String representation of `null` is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="ee41e-120">Değeri, ifade sonucunun dize temsilinde minimum karakter sayısını tanımlayan sabit ifade.</span><span class="sxs-lookup"><span data-stu-id="ee41e-120">The constant expression whose value defines the minimum number of characters in the string representation of the expression result.</span></span> <span data-ttu-id="ee41e-121">Pozitif ise, dize temsili sağa hizalanır; negatifse, sola hizalanır.</span><span class="sxs-lookup"><span data-stu-id="ee41e-121">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="ee41e-122">Daha fazla bilgi için bkz. [Hizalama bileşeni](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="ee41e-122">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="ee41e-123">İfade sonucunun türü tarafından desteklenen bir biçim dizesi.</span><span class="sxs-lookup"><span data-stu-id="ee41e-123">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="ee41e-124">Daha fazla bilgi için bkz. [Biçim dize bileşeni](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="ee41e-124">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="ee41e-125">Aşağıdaki örnek, yukarıda açıklanan isteğe bağlı biçimlendirme bileşenlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="ee41e-125">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="ee41e-126">Özel karakterler</span><span class="sxs-lookup"><span data-stu-id="ee41e-126">Special characters</span></span>

<span data-ttu-id="ee41e-127">"{" Veya "}" küme ayracı eklemek için, enterpolasyonlu bir dize tarafından üretilen metinde, "{{" veya "}}" iki küme ayracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee41e-127">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="ee41e-128">Daha fazla bilgi için bkz. [kaçış ayraçları](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="ee41e-128">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="ee41e-129">İki nokta üst üste (":"), enterpolasyon ifadesi öğesinde [koşullu bir işleç](../operators/conditional-operator.md) kullanmak için bir ilişkilendirme ifadesinde özel anlamı olduğundan, bu ifadeyi parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="ee41e-129">As the colon (":") has special meaning in an interpolation expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolation expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="ee41e-130">Aşağıdaki örnek, bir sonuç dizesinde bir küme ayracın nasıl ekleneceğini ve bir ilişkilendirme ifadesinde koşullu işlecin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ee41e-130">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolation expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="ee41e-131">Ara değerli bir dize, `$` karakteriyle ve ardından `@` karakteri ile başlar.</span><span class="sxs-lookup"><span data-stu-id="ee41e-131">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="ee41e-132">Tam dizeler hakkında daha fazla bilgi için bkz. [dize](../keywords/string.md) ve tam [tanımlayıcı](verbatim.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="ee41e-132">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="ee41e-133">8,0 ' C# den başlayarak, `$` ve `@` belirteçlerinidilediğiniz`$@"..."` sırada kullanabilirsiniz: her ikisi de geçerlibiraradeğerlidizeler.`@$"..."`</span><span class="sxs-lookup"><span data-stu-id="ee41e-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="ee41e-134">Önceki C# sürümlerde, `$` belirtecin `@` belirteçten önce görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee41e-134">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a><span data-ttu-id="ee41e-135">Örtük dönüştürmeler ve uygulama belirtme `IFormatProvider`</span><span class="sxs-lookup"><span data-stu-id="ee41e-135">Implicit conversions and how to specify `IFormatProvider` implementation</span></span>

<span data-ttu-id="ee41e-136">Enterpolasyonlu bir dizeden üç örtük dönüştürme vardır:</span><span class="sxs-lookup"><span data-stu-id="ee41e-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="ee41e-137">Enterpolasyonlu bir dizenin, <xref:System.String> sonuçları doğru biçimli dize gösterimlerine göre değiştirilmekte olan enterpolasyon ifade öğeleriyle birlikte bulunan bir örneğe dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="ee41e-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolation expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="ee41e-138">Bu dönüştürme, <xref:System.Globalization.CultureInfo.CurrentCulture> ' ın biçim ifadesi sonuçlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee41e-138">This conversion uses the <xref:System.Globalization.CultureInfo.CurrentCulture> to format expression results.</span></span>

1. <span data-ttu-id="ee41e-139">Enterpolasyonlu bir dizenin <xref:System.FormattableString> , bir bileşik biçim dizesini temsil eden, ifade sonuçlarıyla birlikte bir örneğe dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="ee41e-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="ee41e-140">Bu, tek <xref:System.FormattableString> bir örnekten kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee41e-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="ee41e-141">Bunu yapmak için aşağıdaki yöntemlerden birini çağırın:</span><span class="sxs-lookup"><span data-stu-id="ee41e-141">To do that, call one of the following methods:</span></span>

      - <span data-ttu-id="ee41e-142">İçin sonuç dizesi üreten bir <xref:System.FormattableString.ToString> aşırı yükleme. <xref:System.Globalization.CultureInfo.CurrentCulture></span><span class="sxs-lookup"><span data-stu-id="ee41e-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="ee41e-143">İçin sonuç dizesi üreten bir <xref:System.FormattableString.Invariant%2A> yöntem. <xref:System.Globalization.CultureInfo.InvariantCulture></span><span class="sxs-lookup"><span data-stu-id="ee41e-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="ee41e-144">Belirtilen <xref:System.FormattableString.ToString(System.IFormatProvider)> kültür için sonuç dizesi üreten bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="ee41e-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="ee41e-145">Yöntemi, <xref:System.FormattableString.ToString(System.IFormatProvider)> özel biçimlendirmeyi destekleyen <xref:System.IFormatProvider> arabirimin Kullanıcı tanımlı bir uygulamasını sağlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee41e-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="ee41e-146">Daha fazla bilgi için [.net makalesindeki biçimlendirme türleri](../../../standard/base-types/formatting-types.md) konusunun [ICustomFormatter ile özel biçimlendirme](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ee41e-146">For more information, see the [Custom formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) section of the [Formatting types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

1. <span data-ttu-id="ee41e-147">Enterpolasyonlu bir dizenin tek <xref:System.IFormattable> <xref:System.IFormattable> bir örnekten kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza izin veren bir örneğe dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="ee41e-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="ee41e-148">Aşağıdaki örnek, kültüre özgü sonuç dizeleri <xref:System.FormattableString> oluşturmak için için örtük dönüştürmeyi kullanır:</span><span class="sxs-lookup"><span data-stu-id="ee41e-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="ee41e-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ee41e-149">Additional resources</span></span>

<span data-ttu-id="ee41e-150">Dize ilişkilendirme konusunda yeni bir adım daha kullanıyorsanız etkileşimli öğreticide [dize ilişkilendirmeyi C# ](../../tutorials/exploration/interpolated-strings.yml) inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ee41e-150">If you are new to string interpolation, see the [String interpolation in C#](../../tutorials/exploration/interpolated-strings.yml) interactive tutorial.</span></span> <span data-ttu-id="ee41e-151">Ayrıca, biçimlendirilen dizeleri oluşturmak için, enterpolasyonlu dizelerin nasıl kullanılacağını gösteren öğreticideki başka bir [dize ilişkilendirmeyi C# ](../../tutorials/string-interpolation.md) da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee41e-151">You also can check another [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial that demonstrates how to use interpolated strings to produce formatted strings.</span></span>

## <a name="compilation-of-interpolated-strings"></a><span data-ttu-id="ee41e-152">Enterpolasyonlu dizelerin derlenmesi</span><span class="sxs-lookup"><span data-stu-id="ee41e-152">Compilation of interpolated strings</span></span>

<span data-ttu-id="ee41e-153">Bir enterpolasyonlu dize türü `string`varsa, genellikle bir <xref:System.String.Format%2A?displayProperty=nameWithType> yöntem çağrısına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ee41e-153">If an interpolated string has the type `string`, it's typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="ee41e-154">Çözümlenen davranış birleştirme ile <xref:System.String.Format%2A?displayProperty=nameWithType> eşdeğer <xref:System.String.Concat%2A?displayProperty=nameWithType> olacaksa, derleyici ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee41e-154">The compiler may replace <xref:System.String.Format%2A?displayProperty=nameWithType> with <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

<span data-ttu-id="ee41e-155">Bir enterpolasyonlu dize türü <xref:System.IFormattable> veya <xref:System.FormattableString>ise, derleyici <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> yöntemine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ee41e-155">If an interpolated string has the type <xref:System.IFormattable> or <xref:System.FormattableString>, the compiler generates a call to the <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> method.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ee41e-156">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ee41e-156">C# language specification</span></span>

<span data-ttu-id="ee41e-157">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [enterpolasyonlu dizeler](~/_csharplang/spec/expressions.md#interpolated-strings) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ee41e-157">For more information, see the [Interpolated strings](~/_csharplang/spec/expressions.md#interpolated-strings) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee41e-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee41e-158">See also</span></span>

- [<span data-ttu-id="ee41e-159">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="ee41e-159">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ee41e-160">C# özel karakterleri</span><span class="sxs-lookup"><span data-stu-id="ee41e-160">C# special characters</span></span>](index.md)
- [<span data-ttu-id="ee41e-161">Dizeler</span><span class="sxs-lookup"><span data-stu-id="ee41e-161">Strings</span></span>](../../programming-guide/strings/index.md)
- [<span data-ttu-id="ee41e-162">Sayısal sonuçlar tablosunu biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="ee41e-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="ee41e-163">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="ee41e-163">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>

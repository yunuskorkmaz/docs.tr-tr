---
title: C# dize ilişkilendirme
description: Dize ilişkilendirme ile C# dilinde bir sonuç dizesi olarak biçimlendirilmiş bir ifade sonuçları eklemeyi öğrenin.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: ef4358ff61cde43998fc0dc4ba174dc0f06bc2bd
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222499"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="aae93-103">C# dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="aae93-103">String interpolation in C#</span></span> #

<span data-ttu-id="aae93-104">Bu öğreticide nasıl kullanılacağını gösterir [dize ilişkilendirme](../language-reference/tokens/interpolated.md) biçimlendirmek ve ifade sonuçları bir sonuç dizesine eklemek için.</span><span class="sxs-lookup"><span data-stu-id="aae93-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="aae93-105">Örnekler C# temel kavramları ve .NET türü biçimlendirme ile ilgili bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="aae93-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="aae93-106">Dize ilişkilendirme veya .NET türü biçimlendirme için yeni başladıysanız, kullanıma [etkileşimli dize ilişkilendirme öğretici](../tutorials/intro-to-csharp/interpolated-strings.yml) ilk.</span><span class="sxs-lookup"><span data-stu-id="aae93-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](../tutorials/intro-to-csharp/interpolated-strings.yml) first.</span></span> <span data-ttu-id="aae93-107">. NET'te türleri biçimlendirme hakkında daha fazla bilgi için bkz. [NET'teki biçimlendirme türleri](../../standard/base-types/formatting-types.md) konu.</span><span class="sxs-lookup"><span data-stu-id="aae93-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="aae93-108">Giriş</span><span class="sxs-lookup"><span data-stu-id="aae93-108">Introduction</span></span>

<span data-ttu-id="aae93-109">[Dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği üzerine kurulmuştur [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özellik ve biçimlendirilmiş bir ifade sonuçları bir sonuç dizesine eklemek için daha okunabilir ve kullanışlı bir söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="aae93-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="aae93-110">Bir dize ilişkilendirilmiş dize sabit değeri belirlemek için onunla önüne ekleyin `$` simgesi.</span><span class="sxs-lookup"><span data-stu-id="aae93-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="aae93-111">Bir aradeğerlendirme dizesinde bir değer döndüren herhangi bir geçerli C# ifade ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="aae93-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="aae93-112">Aşağıdaki örnekte, bir ifade değerlendirilir hemen sonra sonucu bir dizeye dönüştürülür ve sonuç dizesine dahil:</span><span class="sxs-lookup"><span data-stu-id="aae93-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="aae93-113">Örnekte gösterildiği gibi bir ifade bir aradeğerlendirme dizesinde küme ayraçlarıyla kapsayan tarafından şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aae93-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="aae93-114">Derleme zamanında bir aradeğerlendirme dizesinde tipik olarak dönüştürülür bir <xref:System.String.Format%2A?displayProperty=nameWithType> yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="aae93-114">At compile time, an interpolated string is typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="aae93-115">Tüm özelliklerine getiren [bileşik biçimlendirme dizesi](../../standard/base-types/composite-formatting.md) özelliği de ara değerli dizeler ile kullanmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aae93-115">That makes all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature available to you to use with interpolated strings as well.</span></span>

<span data-ttu-id="aae93-116">Derleyici yerine bir <xref:System.String.Format%2A?displayProperty=nameWithType> için <xref:System.String.Concat%2A?displayProperty=nameWithType> çözümlenen davranışı için birleştirme eşdeğeri yoksa.</span><span class="sxs-lookup"><span data-stu-id="aae93-116">The compiler may substitute a <xref:System.String.Format%2A?displayProperty=nameWithType> for <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="aae93-117">İlişkilendirilmiş ifade için bir biçim dizesi belirtme</span><span class="sxs-lookup"><span data-stu-id="aae93-117">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="aae93-118">İki nokta ile ilişkilendirilmiş ifade izleyerek ifadenin sonuç türü tarafından desteklenen bir biçim dizesi belirtin (":") ve biçim dizesi:</span><span class="sxs-lookup"><span data-stu-id="aae93-118">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="aae93-119">Aşağıdaki örnekte, tarih ve saat veya sayısal sonuçlar üreten ifadeler için standart ve özel biçim dizeleri belirtmek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="aae93-119">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="aae93-120">Daha fazla bilgi için [biçim dizesi bileşeni](../../standard/base-types/composite-formatting.md#format-string-component) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu.</span><span class="sxs-lookup"><span data-stu-id="aae93-120">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="aae93-121">Bu bölüm .NET temel türleri tarafından desteklenen standart ve özel biçim dizeleri açıklayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="aae93-121">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="aae93-122">Alan genişliğini ve hizalamasını biçimlendirilmiş ilişkilendirilmiş ifade denetleme</span><span class="sxs-lookup"><span data-stu-id="aae93-122">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="aae93-123">İlişkilendirilmiş ifade bir virgül ile izleyerek en az bir alan genişliğini ve hizalamasını biçimlendirilmiş bir ifade sonucu belirtin (",") ve sabit ifade:</span><span class="sxs-lookup"><span data-stu-id="aae93-123">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="aae93-124">Varsa *hizalama* değeri pozitif ise sağa hizalı biçimlendirilmiş bir ifade sonucu; negatif ise sola hizalanmış.</span><span class="sxs-lookup"><span data-stu-id="aae93-124">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="aae93-125">Hizalama hem bir biçim dizesi belirtmek gerekirse, hizalama bileşeni ile başlayın:</span><span class="sxs-lookup"><span data-stu-id="aae93-125">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="aae93-126">Aşağıdaki örnek hizalaması belirtmek nasıl gösterir ve kullandığı kanal karakter ("|") metin alanları sınırlandırmak için:</span><span class="sxs-lookup"><span data-stu-id="aae93-126">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="aae93-127">Örnek olarak biçimlendirilmiş bir ifade sonucunun uzunluğu aşması durumunda çıktıda gösterildiği, alan genişliğini belirtilen *hizalama* değer yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="aae93-127">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="aae93-128">Daha fazla bilgi için [hizalama bileşeni](../../standard/base-types/composite-formatting.md#alignment-component) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu.</span><span class="sxs-lookup"><span data-stu-id="aae93-128">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="aae93-129">Bir aradeğerlendirme dizesinde çıkış sıraları kullanma</span><span class="sxs-lookup"><span data-stu-id="aae93-129">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="aae93-130">İlişkilendirilmiş dizeler sıradan dize değişmez değerleri kullanılabilir tüm kaçış dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="aae93-130">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="aae93-131">Daha fazla bilgi için [dize kaçış dizileri](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="aae93-131">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="aae93-132">Kaçış dizileri tam anlamıyla yorumlanması için kullanmak bir [verbatim](../language-reference/tokens/verbatim.md) dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="aae93-132">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="aae93-133">Verbatim ilişkilendirilmiş bir dize ile başlayan `$` karakteri ve ardından `@` karakter.</span><span class="sxs-lookup"><span data-stu-id="aae93-133">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="aae93-134">Bir küme ayracı, dahil etmek için "{" veya "}", bir sonuç dizesinde iki küme ayraçları kullanın "{{" veya "}}".</span><span class="sxs-lookup"><span data-stu-id="aae93-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="aae93-135">Daha fazla bilgi için [kaçış küme ayraçları](../../standard/base-types/composite-formatting.md#escaping-braces) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu.</span><span class="sxs-lookup"><span data-stu-id="aae93-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="aae93-136">Aşağıdaki örnek, küme ayraçları bir sonuç dizesine eklemek ve bir harfi harfine ilişkilendirilmiş dize oluşturma gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="aae93-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="aae93-137">Üçlü koşullu bir işleç kullanmayı `?:` bir ilişkilendirilmiş ifadede</span><span class="sxs-lookup"><span data-stu-id="aae93-137">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="aae93-138">İki nokta üst üste olarak (":") kullanmak için bir öğesi ile ilişkilendirilmiş bir ifadenin özel anlama sahip bir [koşullu işleç](../language-reference/operators/conditional-operator.md) aşağıdaki örnekte gösterildiği gibi parantez içine bir ifadede:</span><span class="sxs-lookup"><span data-stu-id="aae93-138">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="aae93-139">Dize ilişkilendirme ile bir kültüre özgü sonuç dizesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="aae93-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="aae93-140">Varsayılan olarak, bir aradeğerlendirme dizesinde tarafından tanımlanan geçerli kültürü kullanan <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> tüm biçimlendirme işlemleri için özellik.</span><span class="sxs-lookup"><span data-stu-id="aae93-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="aae93-141">Örtük dönüştürme için bir aradeğerlendirme dizesinde kullanmak bir <xref:System.FormattableString?displayProperty=nameWithType> örneği ve çağrı kendi <xref:System.FormattableString.ToString(System.IFormatProvider)> bir kültüre özgü sonuç dizesi oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aae93-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="aae93-142">Aşağıdaki örnek bunu nasıl yapacağınız gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="aae93-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="aae93-143">Örnekte gösterildiği gibi kullanabilirsiniz <xref:System.FormattableString> örneğini çeşitli kültürler için kullanılabilecek birden fazla sonuç dizeleri üretir.</span><span class="sxs-lookup"><span data-stu-id="aae93-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="aae93-144">Sabit kültür kullanılarak bir sonuç dizesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="aae93-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="aae93-145">İle birlikte <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> yöntemi statik kullanabileceğiniz <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> yöntemi için bir sonuç dizesini bir aradeğerlendirme dizesinde çözümlemek için <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="aae93-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="aae93-146">Aşağıdaki örnek bunu nasıl yapacağınız gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="aae93-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="aae93-147">Sonuç</span><span class="sxs-lookup"><span data-stu-id="aae93-147">Conclusion</span></span>

<span data-ttu-id="aae93-148">Bu öğreticide, dize ilişkilendirme kullanım yaygın senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aae93-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="aae93-149">Dize ilişkilendirme hakkında daha fazla bilgi için bkz: [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konu.</span><span class="sxs-lookup"><span data-stu-id="aae93-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="aae93-150">. NET'te türleri biçimlendirme hakkında daha fazla bilgi için bkz. [NET'teki biçimlendirme türleri](../../standard/base-types/formatting-types.md) ve [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konuları.</span><span class="sxs-lookup"><span data-stu-id="aae93-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="aae93-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aae93-151">See Also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>  
- <xref:System.FormattableString?displayProperty=nameWithType>  
- <xref:System.IFormattable?displayProperty=nameWithType>  
- [<span data-ttu-id="aae93-152">Dizeler</span><span class="sxs-lookup"><span data-stu-id="aae93-152">Strings</span></span>](../programming-guide/strings/index.md)  

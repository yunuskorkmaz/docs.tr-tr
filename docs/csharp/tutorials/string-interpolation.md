---
title: "C'de dize enterpolasyonu #"
description: Biçimlendirilmiş ifade sonuçlarını C#'da string enterpolasyonuyla bir sonuç dizesine nasıl eklendiğini öğrenin.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73039205"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="fa004-103">C'de dize enterpolasyonu\#</span><span class="sxs-lookup"><span data-stu-id="fa004-103">String interpolation in C\#</span></span>

<span data-ttu-id="fa004-104">Bu öğretici, bir sonuç dizesinde ifade sonuçlarını biçimlendirmek ve eklemek için [dize enterpolasyonunu](../language-reference/tokens/interpolated.md) nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa004-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="fa004-105">Örnekler, temel C# kavramlarıve .NET türü biçimlendirme aşina olduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="fa004-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="fa004-106">Dize enterpolasyonu veya .NET türü biçimlendirmede yeniyseniz, önce [etkileşimli dize enterpolasyon öğreticisine](exploration/interpolated-strings.yml) göz atın.</span><span class="sxs-lookup"><span data-stu-id="fa004-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="fa004-107">.NET'teki biçimlendirme türleri hakkında daha fazla bilgi için [.NET konusundaki Biçimlendirme Türleri'ne](../../standard/base-types/formatting-types.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="fa004-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="fa004-108">Giriş</span><span class="sxs-lookup"><span data-stu-id="fa004-108">Introduction</span></span>

<span data-ttu-id="fa004-109">[Dize enterpolasyon](../language-reference/tokens/interpolated.md) özelliği bileşik [biçimlendirme](../../standard/base-types/composite-formatting.md) özelliğinin üstüne inşa edilmiştir ve bir sonuç dizesinde biçimlendirilmiş ifade sonuçlarını içerecek şekilde daha okunabilir ve kullanışlı bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa004-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="fa004-110">Bir dize literal bir interpolated dize olarak `$` tanımlamak için, sembolü ile prepend.</span><span class="sxs-lookup"><span data-stu-id="fa004-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="fa004-111">Enterpolasyonlu bir dize bir değer döndüren herhangi bir geçerli C# ifadesini katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa004-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="fa004-112">Aşağıdaki örnekte, bir ifade değerlendirilir değerlendirilmez, sonucu bir dize dönüştürülür ve bir sonuç dizesine dahil edilir:</span><span class="sxs-lookup"><span data-stu-id="fa004-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="fa004-113">Örnekte de görüldüğü gibi, bir ifadeyi ayraçlarla ekleyerek enterpolasyonlu bir dize eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="fa004-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```csharp
{<interpolationExpression>}
```

<span data-ttu-id="fa004-114">Enterpolasyonlu dizeleri [dize bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özelliğinin tüm yeteneklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="fa004-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="fa004-115">Bu onları <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemin kullanımına daha okunabilir bir alternatif yapar.</span><span class="sxs-lookup"><span data-stu-id="fa004-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a><span data-ttu-id="fa004-116">Enterpolasyon ifadesi için biçim dizesi nasıl belirtilir?</span><span class="sxs-lookup"><span data-stu-id="fa004-116">How to specify a format string for an interpolation expression</span></span>

<span data-ttu-id="fa004-117">Bir üst üste (":") ve biçim dizesi ile enterpolasyon ifadesini izleyerek ifade sonucunun türü tarafından desteklenen bir biçim dizesi belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fa004-117">You specify a format string that is supported by the type of the expression result by following the interpolation expression with a colon (":") and the format string:</span></span>

```csharp
{<interpolationExpression>:<formatString>}
```

<span data-ttu-id="fa004-118">Aşağıdaki örnek, tarih ve saat veya sayısal sonuçlar üreten ifadeler için standart ve özel biçim dizelerinin nasıl belirtilen;</span><span class="sxs-lookup"><span data-stu-id="fa004-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="fa004-119">Daha fazla bilgi [için, Bileşik Biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Biçimlendirme Bileşeni](../../standard/base-types/composite-formatting.md#format-string-component) biçimi bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fa004-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="fa004-120">Bu bölümde, .NET taban türleri tarafından desteklenen standart ve özel biçim dizelerini açıklayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa004-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a><span data-ttu-id="fa004-121">Biçimlendirilmiş enterpolasyon ifadesinin alan genişliği ve hizalaması nasıl kontrol edilebilen</span><span class="sxs-lookup"><span data-stu-id="fa004-121">How to control the field width and alignment of the formatted interpolation expression</span></span>

<span data-ttu-id="fa004-122">Enterpolasyon ifadesini virgülle (",") ve sabit ifadeyle izleyerek en az alan genişliğini ve biçimlendirilmiş ifade sonucunun hizalanmasını belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fa004-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolation expression with a comma (",") and the constant expression:</span></span>

```csharp
{<interpolationExpression>,<alignment>}
```

<span data-ttu-id="fa004-123">*Hizalama* değeri pozitifse, biçimlendirilmiş ifade sonucu sağ hizalanır; negatif ise, sol hizalı.</span><span class="sxs-lookup"><span data-stu-id="fa004-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="fa004-124">Hem hizalama hem de biçim dizesi belirtmeniz gerekiyorsa, hizalama bileşeniyle başlayın:</span><span class="sxs-lookup"><span data-stu-id="fa004-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="fa004-125">Aşağıdaki örnek, hizalamanın nasıl belirtilen ve metin alanlarını sınırlamak için boru karakterlerini ("|") nasıl kullandığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="fa004-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="fa004-126">Örnek çıktının gösterdiği gibi, biçimlendirilmiş ifade sonucunun uzunluğu belirtilen alan genişliğini aşıyorsa, *hizalama* değeri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="fa004-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="fa004-127">Daha fazla bilgi [için, Bileşik Biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Hizalama Bileşeni](../../standard/base-types/composite-formatting.md#alignment-component) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fa004-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="fa004-128">İnterpolated dize kaçış dizileri nasıl kullanılır</span><span class="sxs-lookup"><span data-stu-id="fa004-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="fa004-129">Enterpolasyonlu dizeleri sıradan dize literals kullanılabilir tüm kaçış dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="fa004-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="fa004-130">Daha fazla bilgi için [String kaçış dizilerine](../programming-guide/strings/index.md#string-escape-sequences)bakın.</span><span class="sxs-lookup"><span data-stu-id="fa004-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="fa004-131">Kaçış dizilerini kelimenin tam anlamıyla yorumlamak [için, kelimenin tam anlamıyla](../language-reference/tokens/verbatim.md) bir dize harfi kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa004-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="fa004-132">İnterpolated verbatim dize `$` `@` karakter tarafından takip karakter ile başlar.</span><span class="sxs-lookup"><span data-stu-id="fa004-132">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="fa004-133">C# 8.0 ile başlayarak, `$` `@` belirteçleri ve belirteçleri herhangi bir sırada kullanabilirsiniz: her ikisi de `$@"..."` ve `@$"..."` geçerli enterpolasyonlu kelime dizeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="fa004-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span>

<span data-ttu-id="fa004-134">Bir sonuç dizesinde "{" veya "}" bir ayraç eklemek için iki ayraç kullanın: "{{" veya "}}".</span><span class="sxs-lookup"><span data-stu-id="fa004-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="fa004-135">Daha fazla bilgi [için, Bileşik Biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Kaçan Ayraçlar](../../standard/base-types/composite-formatting.md#escaping-braces) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fa004-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="fa004-136">Aşağıdaki örnek, bir sonuç dizesi parantez dahil etmek ve bir kelimenin tam olarak enterpolasyonlu dize oluşturmak nasıl gösterir:</span><span class="sxs-lookup"><span data-stu-id="fa004-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a><span data-ttu-id="fa004-137">Bir enterpolasyon ifadesinde üçüncül `?:` koşullu işleç nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="fa004-137">How to use a ternary conditional operator `?:` in an interpolation expression</span></span>

<span data-ttu-id="fa004-138">Bir ifadede [koşullu işleci](../language-reference/operators/conditional-operator.md) kullanmak için bir enterpolasyon ifadesi olan bir öğede üst üste (":") özel bir anlamı olduğundan, aşağıdaki örnekte görüldüğü gibi, onu parantez içine avurun:</span><span class="sxs-lookup"><span data-stu-id="fa004-138">As the colon (":") has special meaning in an item with an interpolation expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="fa004-139">Dize enterpolasyonu ile kültüre özgü bir sonuç dizesi nasıl oluşturulur?</span><span class="sxs-lookup"><span data-stu-id="fa004-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="fa004-140">Varsayılan olarak, enterpolasyonlu bir dize <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> tüm biçimlendirme işlemleri için özellik tarafından tanımlanan geçerli kültürü kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa004-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="fa004-141">Enterpolasyonlu bir dizenin <xref:System.FormattableString?displayProperty=nameWithType> bir örne <xref:System.FormattableString.ToString(System.IFormatProvider)> örtük dönüşümünü kullanın ve kültüre özgü bir sonuç dizesi oluşturmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="fa004-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="fa004-142">Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="fa004-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="fa004-143">Örnekte görüldüğü gibi, çeşitli <xref:System.FormattableString> kültürler için birden çok sonuç dizeleri oluşturmak için bir örnek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa004-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="fa004-144">Değişmez kültürü kullanarak sonuç dizesi nasıl oluşturulur?</span><span class="sxs-lookup"><span data-stu-id="fa004-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="fa004-145"><xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> Yöntemle birlikte, interpollenmiş bir <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> dizeiçin <xref:System.Globalization.CultureInfo.InvariantCulture>bir sonuç dizesini çözmek için statik yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa004-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="fa004-146">Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="fa004-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="fa004-147">Sonuç</span><span class="sxs-lookup"><span data-stu-id="fa004-147">Conclusion</span></span>

<span data-ttu-id="fa004-148">Bu öğretici, dize enterpolasyon kullanımının yaygın senaryolarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="fa004-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="fa004-149">String enterpolasyonu hakkında daha fazla bilgi için [String enterpolasyon](../language-reference/tokens/interpolated.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="fa004-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="fa004-150">.NET'teki biçimlendirme türleri hakkında daha fazla bilgi için .NET ve [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) [konularındaki Biçimlendirme Türleri'ne](../../standard/base-types/formatting-types.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="fa004-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa004-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa004-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="fa004-152">Dize</span><span class="sxs-lookup"><span data-stu-id="fa004-152">Strings</span></span>](../programming-guide/strings/index.md)

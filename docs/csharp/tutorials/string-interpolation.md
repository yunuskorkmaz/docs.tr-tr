---
title: Öğesinde dize ilişkilendirmeC#
description: Dize ilişkilendirimiyle içindeki C# bir sonuç dizesinde biçimlendirilen ifade sonuçlarının nasıl ekleneceğini öğrenin.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039205"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="1da8f-103">C\# 'da dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="1da8f-103">String interpolation in C\#</span></span>

<span data-ttu-id="1da8f-104">Bu öğretici, bir sonuç dizesinde ifade sonuçlarını biçimlendirmek ve dahil etmek için [dize ilişkilendirmeyi](../language-reference/tokens/interpolated.md) nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1da8f-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="1da8f-105">Örneklerde temel C# kavramlar ve .net tür biçimlendirmesi hakkında bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="1da8f-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="1da8f-106">Dize ilişkilendirme veya .NET tür biçimlendirmesi için yeni bir adım kullanıyorsanız, önce [etkileşimli dize ilişkilendirme öğreticisine](exploration/interpolated-strings.yml) göz atın.</span><span class="sxs-lookup"><span data-stu-id="1da8f-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="1da8f-107">.NET 'teki biçimlendirme türleri hakkında daha fazla bilgi için bkz. [.net konusundaki biçimlendirme türleri](../../standard/base-types/formatting-types.md) .</span><span class="sxs-lookup"><span data-stu-id="1da8f-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="1da8f-108">Giriş</span><span class="sxs-lookup"><span data-stu-id="1da8f-108">Introduction</span></span>

<span data-ttu-id="1da8f-109">[Dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği, [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özelliğinin üzerine kurulmuştur ve biçimlendirilmiş ifade sonuçlarının bir sonuç dizesinde yer almasını sağlayan daha okunabilir ve uygun bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1da8f-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="1da8f-110">Bir dize sabit değerini, enterpolasyonlu bir dize olarak tanımlamak için `$` simgesiyle önüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1da8f-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="1da8f-111">Enterpolasyonlu bir C# dizede değer döndüren herhangi bir geçerli ifadeyi gömebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1da8f-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="1da8f-112">Aşağıdaki örnekte, bir ifade değerlendirildiği anda, sonucu bir dizeye dönüştürülür ve sonuç dizesine dahil edilir:</span><span class="sxs-lookup"><span data-stu-id="1da8f-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="1da8f-113">Örnekte gösterildiği gibi, araya alınmış dizeye bir ifadeyi küme ayraçları ile çevreleyerek dahil edersiniz:</span><span class="sxs-lookup"><span data-stu-id="1da8f-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```csharp
{<interpolationExpression>}
```

<span data-ttu-id="1da8f-114">Enterpolasyonlu dizeler, [dize bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özelliğinin tüm yeteneklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1da8f-114">Interpolated strings support all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="1da8f-115">Bu, <xref:System.String.Format%2A?displayProperty=nameWithType> yönteminin kullanımına daha okunabilir bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="1da8f-115">That makes them a more readable alternative to the use of the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a><span data-ttu-id="1da8f-116">İlişkilendirme ifadesi için biçim dizesi belirtme</span><span class="sxs-lookup"><span data-stu-id="1da8f-116">How to specify a format string for an interpolation expression</span></span>

<span data-ttu-id="1da8f-117">İki nokta üst üste (":") ve biçim dizesiyle ilişkilendirme ifadesini izleyerek, ifade sonucunun türü tarafından desteklenen bir biçim dizesi belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1da8f-117">You specify a format string that is supported by the type of the expression result by following the interpolation expression with a colon (":") and the format string:</span></span>

```csharp
{<interpolationExpression>:<formatString>}
```

<span data-ttu-id="1da8f-118">Aşağıdaki örnek, tarih ve saat veya sayısal sonuçlar üreten ifadeler için standart ve özel biçim dizelerinin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1da8f-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="1da8f-119">Daha fazla bilgi için [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Biçim dizesi bileşeni](../../standard/base-types/composite-formatting.md#format-string-component) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1da8f-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="1da8f-120">Bu bölüm, .NET temel türleri tarafından desteklenen standart ve özel biçim dizelerini tanımlayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="1da8f-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a><span data-ttu-id="1da8f-121">Biçimlendirilen enterpolasyon ifadesinin alan genişliğini ve hizalamasını denetleme</span><span class="sxs-lookup"><span data-stu-id="1da8f-121">How to control the field width and alignment of the formatted interpolation expression</span></span>

<span data-ttu-id="1da8f-122">Bir virgül (",") ve sabit ifade ile ilişkilendirme ifadesini izleyerek, biçimlendirilen ifade sonucunun en düşük alan genişliğini ve hizalamasını belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1da8f-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolation expression with a comma (",") and the constant expression:</span></span>

```csharp
{<interpolationExpression>,<alignment>}
```

<span data-ttu-id="1da8f-123">*Hizalama* değeri pozitifse, biçimlendirilen ifade sonucu sağa hizalanır; negatifse, sola hizalanır.</span><span class="sxs-lookup"><span data-stu-id="1da8f-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="1da8f-124">Hem hizalama hem de bir biçim dizesi belirtmeniz gerekiyorsa, hizalama bileşeniyle başlayın:</span><span class="sxs-lookup"><span data-stu-id="1da8f-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="1da8f-125">Aşağıdaki örnek, hizalama belirtme ve metin alanlarını sınırlandırmak için kanal karakterlerinin ("|") nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1da8f-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="1da8f-126">Örnek çıktıda gösterildiği gibi, biçimlendirilen ifade sonucunun uzunluğu belirtilen alan genişliğini aşarsa, *Hizalama* değeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="1da8f-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="1da8f-127">Daha fazla bilgi için [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Hizalama bileşeni](../../standard/base-types/composite-formatting.md#alignment-component) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1da8f-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="1da8f-128">Enterpolasyonlu bir dizede kaçış dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="1da8f-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="1da8f-129">Enterpolasyonlu dizeler, normal dize değişmez değerlerinde kullanılabilen tüm kaçış dizilerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1da8f-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="1da8f-130">Daha fazla bilgi için bkz. [dize kaçış dizileri](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="1da8f-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="1da8f-131">Kaçış dizilerini [bire bir yorumlamak](../language-reference/tokens/verbatim.md) için, tam bir dize sabiti kullanın.</span><span class="sxs-lookup"><span data-stu-id="1da8f-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="1da8f-132">Enterpolasyonlu bir dize `$` karakteriyle başlar ve ardından `@` karakteri gelir.</span><span class="sxs-lookup"><span data-stu-id="1da8f-132">An interpolated verbatim string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="1da8f-133">8,0 ile C# başlayarak,`$`ve`@`belirteçlerini dilediğiniz sırada kullanabilirsiniz: her iki `$@"..."`ve`@$"..."`geçerli bir ara değerli dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="1da8f-133">Starting with C# 8.0, you can use the `$` and `@` tokens in any order: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span>

<span data-ttu-id="1da8f-134">Bir küme ayracı eklemek için, "{" veya "}", bir sonuç dizesinde, "{{" veya "}}" iki küme ayracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="1da8f-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="1da8f-135">Daha fazla bilgi için [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [kaçış ayraçları](../../standard/base-types/composite-formatting.md#escaping-braces) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1da8f-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="1da8f-136">Aşağıdaki örnek, bir sonuç dizesinde küme ayracın nasıl ekleneceğini ve tam bir enterpolasyonlu dize nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1da8f-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a><span data-ttu-id="1da8f-137">Enterpolasyon ifadesinde Üçlü koşullu işleç `?:` kullanma</span><span class="sxs-lookup"><span data-stu-id="1da8f-137">How to use a ternary conditional operator `?:` in an interpolation expression</span></span>

<span data-ttu-id="1da8f-138">İki nokta üst üste (":") enterpolasyon ifadesi içeren bir öğe için özel anlam içerdiğinden, bir ifadede [koşullu bir işleç](../language-reference/operators/conditional-operator.md) kullanmak için aşağıdaki örnekte gösterildiği gibi, parantez içine alın:</span><span class="sxs-lookup"><span data-stu-id="1da8f-138">As the colon (":") has special meaning in an item with an interpolation expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="1da8f-139">Dize ilişkilendirme ile kültüre özgü sonuç dizesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1da8f-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="1da8f-140">Varsayılan olarak, bir enterpolasyonlu dize, tüm biçimlendirme işlemleri için <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> özelliği tarafından tanımlanan geçerli kültürü kullanır.</span><span class="sxs-lookup"><span data-stu-id="1da8f-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="1da8f-141">Bir <xref:System.FormattableString?displayProperty=nameWithType> örneğine enterpolasyonlu bir dizenin örtük dönüşümünü kullanın ve kültüre özgü bir sonuç dizesi oluşturmak için <xref:System.FormattableString.ToString(System.IFormatProvider)> metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="1da8f-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="1da8f-142">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="1da8f-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="1da8f-143">Örnekte gösterildiği gibi, çeşitli kültürler için birden çok sonuç dizesi oluşturmak üzere bir <xref:System.FormattableString> örneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1da8f-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="1da8f-144">Sabit kültür kullanarak sonuç dizesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1da8f-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="1da8f-145"><xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> yöntemiyle birlikte, <xref:System.Globalization.CultureInfo.InvariantCulture>için bir sonuç dizesine bir ara değerli dizeyi çözümlemek üzere statik <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1da8f-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="1da8f-146">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="1da8f-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="1da8f-147">Sonuç</span><span class="sxs-lookup"><span data-stu-id="1da8f-147">Conclusion</span></span>

<span data-ttu-id="1da8f-148">Bu öğreticide, dize ilişkilendirme kullanımının yaygın senaryoları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1da8f-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="1da8f-149">Dize ilişkilendirme hakkında daha fazla bilgi için bkz. [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="1da8f-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="1da8f-150">.NET 'teki biçimlendirme türleri hakkında daha fazla bilgi için bkz. .NET ve [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konularında [biçimlendirme türleri](../../standard/base-types/formatting-types.md) .</span><span class="sxs-lookup"><span data-stu-id="1da8f-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="1da8f-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1da8f-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="1da8f-152">Dizeler</span><span class="sxs-lookup"><span data-stu-id="1da8f-152">Strings</span></span>](../programming-guide/strings/index.md)

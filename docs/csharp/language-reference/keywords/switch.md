---
description: Switch (C# Başvurusu)
title: C# anahtar ekstresi
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: d8fae870bb3a6fdda735a028dc1da20213a68a31
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756045"
---
# <a name="switch-c-reference"></a><span data-ttu-id="1cf9c-103">Switch (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1cf9c-103">switch (C# reference)</span></span>

<span data-ttu-id="1cf9c-104">Bu makale, `switch` ifadesini içerir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-104">This article covers the `switch` statement.</span></span> <span data-ttu-id="1cf9c-105">İfade hakkında daha fazla bilgi için `switch` (C# 8,0 ' de tanıtılan), [ifadeler ve işleçler](../operators/index.md) bölümündeki [ `switch` ifadelerde](../operators/switch-expression.md) bulunan makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-105">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="1cf9c-106">`switch`, *Match ifadesiyle*bir model eşleşmesi temelinde aday listesinden yürütülecek tek bir *anahtar bölümü* seçen bir seçim deyimidir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-106">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="1cf9c-107">`switch`Tek bir ifade üç veya daha fazla koşula göre test edildiğinde deyim genellikle [If-Else](if-else.md) yapısına alternatif olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-107">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="1cf9c-108">Örneğin, aşağıdaki ifade, `switch` türünde bir değişkenin `Color` üç değerden birine sahip olup olmadığını belirler:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-108">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="1cf9c-109">Yapı kullanan aşağıdaki örneğe eşdeğerdir `if` - `else` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-109">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="1cf9c-110">Match ifadesi</span><span class="sxs-lookup"><span data-stu-id="1cf9c-110">The match expression</span></span>

<span data-ttu-id="1cf9c-111">Match ifadesi, etiketlerin desenleriyle eşleşecek değeri sağlar `case` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-111">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="1cf9c-112">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-112">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="1cf9c-113">C# 6 ve önceki sürümlerde, Match ifadesi aşağıdaki türlerde bir değer döndüren bir ifade olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-113">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="1cf9c-114">bir [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="1cf9c-114">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="1cf9c-115">bir [dize](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1cf9c-115">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="1cf9c-116">bir [bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="1cf9c-116">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="1cf9c-117">veya gibi bir [integral](../builtin-types/integral-numeric-types.md) değeri `int` `long` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-117">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="1cf9c-118">bir [sabit listesi](../builtin-types/enum.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-118">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="1cf9c-119">C# 7,0 ile başlayarak, Match ifadesi null olmayan herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-119">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="1cf9c-120">Anahtar bölümü</span><span class="sxs-lookup"><span data-stu-id="1cf9c-120">The switch section</span></span>

<span data-ttu-id="1cf9c-121">Bir `switch` ifade bir veya daha fazla anahtar bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-121">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="1cf9c-122">Her anahtar bölümü bir veya daha fazla *durum etiketi* (bir Case veya default etiketi) ve ardından bir veya daha fazla deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-122">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="1cf9c-123">`switch`İfade, herhangi bir switch bölümüne yerleştirilmiş en çok bir varsayılan etiket içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-123">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="1cf9c-124">Aşağıdaki örnek `switch` , her biri iki deyim içeren üç anahtar bölümü olan basit bir deyimi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-124">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="1cf9c-125">İkinci anahtar bölümü `case 2:` ve `case 3:` etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-125">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="1cf9c-126">Bir `switch` ifade herhangi bir sayıda anahtar bölümü içerebilir ve aşağıdaki örnekte gösterildiği gibi her bölümde bir veya daha fazla Case etiketi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-126">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="1cf9c-127">Ancak, iki durum etiketi de aynı ifadeyi içeremez.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-127">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="1cf9c-128">Switch deyimindeki yalnızca bir switch bölümü yürütülür.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-128">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="1cf9c-129">C#, yürütmenin bir geçiş bölümünden bir sonrakine devam etmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-129">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="1cf9c-130">Bu nedenle, aşağıdaki kod bir derleyici hatası oluşturuyor, CS0163: "Denetim bir case etiketinden () bir diğerine geçemez \<case label> ."</span><span class="sxs-lookup"><span data-stu-id="1cf9c-130">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

<span data-ttu-id="1cf9c-131">Bu gereksinim, genellikle bir [Break](break.md), [goto](goto.md)veya [Return](return.md) ifadesiyle Switch bölümünden açıkça çıkarken karşılanır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-131">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="1cf9c-132">Ancak, program denetiminin Switch bölümüne dönememesini sağladığından aşağıdaki kod de geçerlidir `default` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-132">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="1cf9c-133">Eşleştirme ifadesiyle eşleşen bir Case etiketi ile Switch bölümündeki deyim listesinin yürütülmesi ilk deyimle başlar ve genellikle,,, veya gibi bir sıçrama deyimine `break` `goto case` `goto label` `return` ulaşılana kadar deyim listesini ilerler `throw` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-133">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="1cf9c-134">Bu noktada denetim `switch` deyimin dışına veya başka bir Case etiketine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-134">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="1cf9c-135">Bir `goto` ifade kullanılıyorsa, denetim bir sabit etikete aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-135">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="1cf9c-136">Bu kısıtlama gereklidir, çünkü denetimi sabit olmayan bir etikete aktarmaya çalışmak, denetimi kodda istenmeyen bir konuma aktarmak veya sonsuz bir döngü oluşturmak gibi istenmeyen yan etkilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-136">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="1cf9c-137">Case etiketleri</span><span class="sxs-lookup"><span data-stu-id="1cf9c-137">Case labels</span></span>

<span data-ttu-id="1cf9c-138">Her Case etiketi, Match ifadesiyle Karşılaştırılacak bir model belirtir ( `caseSwitch` Önceki örneklerde bulunan değişkeni).</span><span class="sxs-lookup"><span data-stu-id="1cf9c-138">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="1cf9c-139">Eşleşiyorsa denetim, **ilk** eşleşen Case etiketini içeren Switch bölümüne aktarılır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-139">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="1cf9c-140">Hiçbir Case etiket deseninin eşleşme ifadesiyle eşleşmesi halinde, denetim varsa Case etiketi ile bölüme aktarılır `default` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-140">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="1cf9c-141">`default`Böyle bir durum yoksa, herhangi bir switch bölümünde hiçbir deyim yürütülmez ve denetim deyimin dışına aktarılır `switch` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-141">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="1cf9c-142">`switch`Deyimle ve model eşleştirme hakkında daha fazla bilgi için bkz. [ `switch` deyimle eşleşen model](#pattern-matching-with-the-switch-statement) bölümü.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-142">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern-matching-with-the-switch-statement) section.</span></span>

<span data-ttu-id="1cf9c-143">C# 6 yalnızca sabit bir stili desteklediğinden ve sabit değerlerin yinelenmesinde izin vermediğinden, Case etiketleri birbirini dışlayan değerleri tanımlar ve yalnızca bir desenler eşleştirme ifadesiyle eşleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-143">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="1cf9c-144">Sonuç olarak, `case` deyimlerin görünme sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-144">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="1cf9c-145">Ancak C# 7,0 ' de, diğer desenler desteklendiğinden, büyük/küçük harf etiketlerinin birbirini dışlayan değerler tanımlamamalıdır ve birden çok desen eşleştirme ifadesiyle eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-145">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="1cf9c-146">Yalnızca eşleşen düzeni içeren ilk anahtar bölümündeki deyimler yürütülene göre, `case` deyimlerin göründüğü sıra artık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-146">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="1cf9c-147">C#, Case deyimi veya deyimleri önceki deyimlerin alt kümelerine eşit olan bir switch bölümü algılarsa, "switch case zaten önceki bir durum tarafından işlenmiştir." bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-147">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="1cf9c-148">Aşağıdaki örnek, `switch` birbirini dışlayan farklı desenler kullanan bir ifadeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-148">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="1cf9c-149">`case 0:`Switch bölümünü deyimdeki ilk bölüm olmayacak şekilde taşırsanız `switch` , C# bir derleyici hatası oluşturur, çünkü değeri sıfır olan bir tamsayı, deyimin tanımladığı model olan tüm tamsayıların alt kümesidir `case int val` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-149">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="1cf9c-150">Bu sorunu düzeltebilir ve iki şekilde derleyici uyarısını ortadan kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-150">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="1cf9c-151">Anahtar bölümlerinin sırasını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-151">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="1cf9c-152">Etikette bir [WHERE yan tümcesi](#the-case-statement-and-the-when-clause) kullanarak `case` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-152">By using a [when clause](#the-case-statement-and-the-when-clause) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="1cf9c-153">`default`Büyük/küçük harf</span><span class="sxs-lookup"><span data-stu-id="1cf9c-153">The `default` case</span></span>

<span data-ttu-id="1cf9c-154">Bu `default` durumda, eşleşme ifadesi başka bir etiketle eşleşmezse yürütülecek Switch bölümü belirtilir `case` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-154">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="1cf9c-155">Bir `default` servis talebi yoksa ve eşleştirme ifadesi başka bir `case` etiketle eşleşmiyorsa, program akışı deyim aracılığıyla geçer `switch` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-155">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="1cf9c-156">`default`Durum, deyimdeki herhangi bir sırada görünebilir `switch` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-156">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="1cf9c-157">Kaynak kodundaki sıralarından bağımsız olarak, tüm Etiketler hesaplandıktan sonra her zaman son değerlendirilir `case` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-157">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="1cf9c-158">Deyimle eşleşen desenler `switch`</span><span class="sxs-lookup"><span data-stu-id="1cf9c-158">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="1cf9c-159">Her `case` deyim, eşleşme ifadesiyle eşleşiyorsa, kapsayan anahtar bölümünün yürütülmesine neden olan bir model tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-159">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="1cf9c-160">Tüm C# sürümleri sabit bir stili destekler.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-160">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="1cf9c-161">Kalan desenler C# 7,0 ' den başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-161">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="1cf9c-162">Sabit model</span><span class="sxs-lookup"><span data-stu-id="1cf9c-162">Constant pattern</span></span>

<span data-ttu-id="1cf9c-163">Sabit model, eşleşme ifadesinin belirtilen bir sabit değere eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-163">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="1cf9c-164">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-164">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="1cf9c-165">Burada *Constant* , test edilecek değerdir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-165">where *constant* is the value to test for.</span></span> <span data-ttu-id="1cf9c-166">*sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-166">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="1cf9c-167">Bir [bool](../builtin-types/bool.md) sabit değeri: `true` ya da `false` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-167">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="1cf9c-168">,, Veya gibi herhangi bir [integral](../builtin-types/integral-numeric-types.md) sabiti `int` `long` `byte` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-168">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="1cf9c-169">Belirtilen `const` değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-169">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="1cf9c-170">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-170">An enumeration constant.</span></span>
- <span data-ttu-id="1cf9c-171">Bir [char](../builtin-types/char.md) sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-171">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="1cf9c-172">[Dize](../builtin-types/reference-types.md) sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-172">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="1cf9c-173">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-173">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="1cf9c-174">*Expr* ve *Constant* Integral türse, C# eşitlik işleci ifadenin döndürülüp döndürülmeyeceğini `true` (yani, ne gibi `expr == constant` ) belirler.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-174">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="1cf9c-175">Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-175">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="1cf9c-176">Aşağıdaki örnek, belirli bir tarihin hafta sonu, çalışma haftasının ilk günü mi, çalışma haftasının son günü mi yoksa çalışma haftasının ortasında mi olduğunu anlamak için sabit bir düzende kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-176">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="1cf9c-177"><xref:System.DateTime.DayOfWeek?displayProperty=nameWithType>Geçerli günün özelliğini numaralandırmanın üyelerine göre değerlendirir <xref:System.DayOfWeek> .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-177">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="1cf9c-178">Aşağıdaki örnek, bir otomatik kahve makinesine benzetim yapan bir konsol uygulamasında kullanıcı girişini işlemek için sabit bir model kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-178">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="1cf9c-179">Tür stili</span><span class="sxs-lookup"><span data-stu-id="1cf9c-179">Type pattern</span></span>

<span data-ttu-id="1cf9c-180">Tür stili, kısa tür değerlendirmesi ve dönüştürmeyi mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-180">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="1cf9c-181">`switch`Model eşleştirmeyi gerçekleştirmek için ifadesiyle birlikte kullanıldığında, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülebileceğini sınar ve bu, mümkünse, bu türden bir değişkene bu değeri verebilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-181">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="1cf9c-182">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-182">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="1cf9c-183">Burada *tür* , *Expr* 'nin sonucunun dönüştürülecek türün adı ve *varname* , eşleşme başarılı olursa *ifadenin* sonucunun dönüştürüldüğü nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-183">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="1cf9c-184">*İfadenin* derleme zamanı türü, C# 7,1 ' den başlayarak genel bir tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-184">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="1cf9c-185">`case`İfadesi `true` aşağıdakilerden herhangi biri doğru ise olur:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-185">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="1cf9c-186">*Expr* , *türü*ile aynı türde bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-186">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="1cf9c-187">*Expr* *türünden*türetilen bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-187">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="1cf9c-188">Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-188">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="1cf9c-189">*ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-189">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="1cf9c-190">Bir değişkenin *derleme zamanı türü* , tür bildiriminde tanımlanan değişkenin türüdür.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-190">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="1cf9c-191">Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-191">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="1cf9c-192">*Expr* , *tür* arabirimini uygulayan bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-192">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="1cf9c-193">Case ifadesi true ise, *varname* kesinlikle atanır ve yalnızca switch bölümü içinde yerel kapsama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-193">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="1cf9c-194">`null`Bir türle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-194">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="1cf9c-195">Bir ile eşleştirmek için `null` aşağıdaki `case` etiketi kullanın:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-195">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="1cf9c-196">Aşağıdaki örnek, çeşitli türlerdeki koleksiyon türleri hakkında bilgi sağlamak için tür modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-196">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="1cf9c-197">Yerine, `object` aşağıdaki kodda gösterildiği gibi, tür parametresi olarak koleksiyonun türünü kullanarak genel bir yöntem oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1cf9c-197">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="1cf9c-198">Genel sürüm, ilk örnekten iki şekilde farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-198">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="1cf9c-199">İlk olarak, bu durumu kullanamazsınız `null` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-199">First, you can't use the `null` case.</span></span> <span data-ttu-id="1cf9c-200">Derleyici herhangi bir rastgele türü dışında herhangi bir türe dönüştüremediği için herhangi bir sabit durumu kullanamazsınız `T` `object` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-200">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="1cf9c-201">`default`Artık null olmayan bir durum için test edilmiş olabilir `object` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-201">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="1cf9c-202">Bu, `default` yalnızca için büyük/küçük harf testleri anlamına gelir `null` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-202">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="1cf9c-203">Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-203">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="1cf9c-204">Tür deseninin kullanımı, dönüştürmenin sonucunun bir `null` veya yinelenen yayınlar gerçekleştirmesini sağlamak için bir veya daha fazla okunabilir kod üretir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-204">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="1cf9c-205">`case`Deyimi ve `when` yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="1cf9c-205">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="1cf9c-206">C# 7,0 ' den itibaren, Case deyimlerinin birbirini `when` dışlanması gerektiğinden, Case ifadesinin true olarak değerlendirilmesi için karşılanması gereken ek bir koşul belirtmek üzere bir yan tümce ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-206">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="1cf9c-207">`when`Yan tümce, Boolean değer döndüren herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-207">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="1cf9c-208">Aşağıdaki örnek, bir temel `Shape` sınıf, `Rectangle` öğesinden türetilen bir sınıf `Shape` ve `Square` öğesinden türetilen bir `Rectangle` sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-208">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="1cf9c-209">`when` `ShowShapeInfo` `Rectangle` Bir nesne `Square` olarak örneği oluşturulmasa bile eşit uzunlukta ve genişlikler atanan bir nesneyi bir nesne olarak değerlendirdiğinden emin olmak için yan tümcesini kullanır `Square` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-209">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="1cf9c-210">Yöntemi, `null` veya alanı sıfır olan bir şekil gibi bir nesne hakkında bilgi görüntülemeyi denemez.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-210">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="1cf9c-211">`when`Örnekteki yan tümcesinin, bir `Shape` nesnenin yürütülüp yürütülmediğini test girişiminde bulunduğunu unutmayın `null` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-211">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="1cf9c-212">Bir için test edilecek doğru tür deseninin türü `null` `case null:` .</span><span class="sxs-lookup"><span data-stu-id="1cf9c-212">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1cf9c-213">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1cf9c-213">C# language specification</span></span>

<span data-ttu-id="1cf9c-214">Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Switch ifadesine](~/_csharplang/spec/statements.md#the-switch-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-214">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="1cf9c-215">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-215">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cf9c-216">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cf9c-216">See also</span></span>

- [<span data-ttu-id="1cf9c-217">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1cf9c-217">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1cf9c-218">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1cf9c-218">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1cf9c-219">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1cf9c-219">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1cf9c-220">if-else</span><span class="sxs-lookup"><span data-stu-id="1cf9c-220">if-else</span></span>](if-else.md)
- [<span data-ttu-id="1cf9c-221">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="1cf9c-221">Pattern Matching</span></span>](../../pattern-matching.md)

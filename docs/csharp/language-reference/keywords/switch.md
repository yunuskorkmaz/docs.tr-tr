---
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
ms.openlocfilehash: a4e6f8e43c2ec8c867af9f78bd83b435b78c73d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446769"
---
# <a name="switch-c-reference"></a><span data-ttu-id="33169-102">Switch (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="33169-102">switch (C# reference)</span></span>

<span data-ttu-id="33169-103">Bu makale, `switch` ifadesini içerir.</span><span class="sxs-lookup"><span data-stu-id="33169-103">This article covers the `switch` statement.</span></span> <span data-ttu-id="33169-104">İfade hakkında daha fazla bilgi için `switch` (C# 8,0 ' de tanıtılan), [ifadeler ve işleçler](../operators/index.md) bölümündeki [ `switch` ifadelerde](../operators/switch-expression.md) bulunan makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="33169-104">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="33169-105">`switch`, *Match ifadesiyle*bir model eşleşmesi temelinde aday listesinden yürütülecek tek bir *anahtar bölümü* seçen bir seçim deyimidir.</span><span class="sxs-lookup"><span data-stu-id="33169-105">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="33169-106">`switch`Tek bir ifade üç veya daha fazla koşula göre test edildiğinde deyim genellikle [If-Else](if-else.md) yapısına alternatif olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33169-106">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="33169-107">Örneğin, aşağıdaki ifade, `switch` türünde bir değişkenin `Color` üç değerden birine sahip olup olmadığını belirler:</span><span class="sxs-lookup"><span data-stu-id="33169-107">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="33169-108">Yapı kullanan aşağıdaki örneğe eşdeğerdir `if` - `else` .</span><span class="sxs-lookup"><span data-stu-id="33169-108">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="33169-109">Match ifadesi</span><span class="sxs-lookup"><span data-stu-id="33169-109">The match expression</span></span>

<span data-ttu-id="33169-110">Match ifadesi, etiketlerin desenleriyle eşleşecek değeri sağlar `case` .</span><span class="sxs-lookup"><span data-stu-id="33169-110">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="33169-111">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33169-111">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="33169-112">C# 6 ve önceki sürümlerde, Match ifadesi aşağıdaki türlerde bir değer döndüren bir ifade olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="33169-112">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="33169-113">bir [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="33169-113">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="33169-114">bir [dize](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="33169-114">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="33169-115">bir [bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="33169-115">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="33169-116">veya gibi bir [integral](../builtin-types/integral-numeric-types.md) değeri `int` `long` .</span><span class="sxs-lookup"><span data-stu-id="33169-116">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="33169-117">bir [sabit listesi](../builtin-types/enum.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="33169-117">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="33169-118">C# 7,0 ile başlayarak, Match ifadesi null olmayan herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="33169-118">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="33169-119">Anahtar bölümü</span><span class="sxs-lookup"><span data-stu-id="33169-119">The switch section</span></span>

<span data-ttu-id="33169-120">Bir `switch` ifade bir veya daha fazla anahtar bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="33169-120">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="33169-121">Her anahtar bölümü bir veya daha fazla *durum etiketi* (bir Case veya default etiketi) ve ardından bir veya daha fazla deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="33169-121">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="33169-122">`switch`İfade, herhangi bir switch bölümüne yerleştirilmiş en çok bir varsayılan etiket içerebilir.</span><span class="sxs-lookup"><span data-stu-id="33169-122">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="33169-123">Aşağıdaki örnek `switch` , her biri iki deyim içeren üç anahtar bölümü olan basit bir deyimi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="33169-123">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="33169-124">İkinci anahtar bölümü `case 2:` ve `case 3:` etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="33169-124">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="33169-125">Bir `switch` ifade herhangi bir sayıda anahtar bölümü içerebilir ve aşağıdaki örnekte gösterildiği gibi her bölümde bir veya daha fazla Case etiketi olabilir.</span><span class="sxs-lookup"><span data-stu-id="33169-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="33169-126">Ancak, iki durum etiketi de aynı ifadeyi içeremez.</span><span class="sxs-lookup"><span data-stu-id="33169-126">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="33169-127">Switch deyimindeki yalnızca bir switch bölümü yürütülür.</span><span class="sxs-lookup"><span data-stu-id="33169-127">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="33169-128">C#, yürütmenin bir geçiş bölümünden bir sonrakine devam etmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="33169-128">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="33169-129">Bu nedenle, aşağıdaki kod bir derleyici hatası oluşturuyor, CS0163: "Denetim bir case etiketinden () bir diğerine geçemez \<case label> ."</span><span class="sxs-lookup"><span data-stu-id="33169-129">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="33169-130">Bu gereksinim, genellikle bir [Break](break.md), [goto](goto.md)veya [Return](return.md) ifadesiyle Switch bölümünden açıkça çıkarken karşılanır.</span><span class="sxs-lookup"><span data-stu-id="33169-130">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="33169-131">Ancak, program denetiminin Switch bölümüne dönememesini sağladığından aşağıdaki kod de geçerlidir `default` .</span><span class="sxs-lookup"><span data-stu-id="33169-131">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="33169-132">Eşleştirme ifadesiyle eşleşen bir Case etiketi ile Switch bölümündeki deyim listesinin yürütülmesi ilk deyimle başlar ve genellikle,,, veya gibi bir sıçrama deyimine `break` `goto case` `goto label` `return` ulaşılana kadar deyim listesini ilerler `throw` .</span><span class="sxs-lookup"><span data-stu-id="33169-132">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="33169-133">Bu noktada denetim `switch` deyimin dışına veya başka bir Case etiketine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="33169-133">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="33169-134">Bir `goto` ifade kullanılıyorsa, denetim bir sabit etikete aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33169-134">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="33169-135">Bu kısıtlama gereklidir, çünkü denetimi sabit olmayan bir etikete aktarmaya çalışmak, denetimi kodda istenmeyen bir konuma aktarmak veya sonsuz bir döngü oluşturmak gibi istenmeyen yan etkilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="33169-135">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="33169-136">Case etiketleri</span><span class="sxs-lookup"><span data-stu-id="33169-136">Case labels</span></span>

<span data-ttu-id="33169-137">Her Case etiketi, Match ifadesiyle Karşılaştırılacak bir model belirtir ( `caseSwitch` Önceki örneklerde bulunan değişkeni).</span><span class="sxs-lookup"><span data-stu-id="33169-137">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="33169-138">Eşleşiyorsa denetim, **ilk** eşleşen Case etiketini içeren Switch bölümüne aktarılır.</span><span class="sxs-lookup"><span data-stu-id="33169-138">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="33169-139">Hiçbir Case etiket deseninin eşleşme ifadesiyle eşleşmesi halinde, denetim varsa Case etiketi ile bölüme aktarılır `default` .</span><span class="sxs-lookup"><span data-stu-id="33169-139">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="33169-140">`default`Böyle bir durum yoksa, herhangi bir switch bölümünde hiçbir deyim yürütülmez ve denetim deyimin dışına aktarılır `switch` .</span><span class="sxs-lookup"><span data-stu-id="33169-140">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="33169-141">`switch`Deyimle ve model eşleştirme hakkında daha fazla bilgi için bkz. [ `switch` deyimle eşleşen model](#pattern) bölümü.</span><span class="sxs-lookup"><span data-stu-id="33169-141">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="33169-142">C# 6 yalnızca sabit bir stili desteklediğinden ve sabit değerlerin yinelenmesinde izin vermediğinden, Case etiketleri birbirini dışlayan değerleri tanımlar ve yalnızca bir desenler eşleştirme ifadesiyle eşleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="33169-142">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="33169-143">Sonuç olarak, `case` deyimlerin görünme sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="33169-143">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="33169-144">Ancak C# 7,0 ' de, diğer desenler desteklendiğinden, büyük/küçük harf etiketlerinin birbirini dışlayan değerler tanımlamamalıdır ve birden çok desen eşleştirme ifadesiyle eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="33169-144">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="33169-145">Yalnızca eşleşen düzeni içeren ilk anahtar bölümündeki deyimler yürütülene göre, `case` deyimlerin göründüğü sıra artık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="33169-145">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="33169-146">C#, Case deyimi veya deyimleri önceki deyimlerin alt kümelerine eşit olan bir switch bölümü algılarsa, "switch case zaten önceki bir durum tarafından işlenmiştir." bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33169-146">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="33169-147">Aşağıdaki örnek, `switch` birbirini dışlayan farklı desenler kullanan bir ifadeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="33169-147">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="33169-148">`case 0:`Switch bölümünü deyimdeki ilk bölüm olmayacak şekilde taşırsanız `switch` , C# bir derleyici hatası oluşturur, çünkü değeri sıfır olan bir tamsayı, deyimin tanımladığı model olan tüm tamsayıların alt kümesidir `case int val` .</span><span class="sxs-lookup"><span data-stu-id="33169-148">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="33169-149">Bu sorunu düzeltebilir ve iki şekilde derleyici uyarısını ortadan kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="33169-149">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="33169-150">Anahtar bölümlerinin sırasını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="33169-150">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="33169-151">Etikette bir [WHERE yan tümcesi](#when) kullanarak `case` .</span><span class="sxs-lookup"><span data-stu-id="33169-151">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="33169-152">`default`Büyük/küçük harf</span><span class="sxs-lookup"><span data-stu-id="33169-152">The `default` case</span></span>

<span data-ttu-id="33169-153">Bu `default` durumda, eşleşme ifadesi başka bir etiketle eşleşmezse yürütülecek Switch bölümü belirtilir `case` .</span><span class="sxs-lookup"><span data-stu-id="33169-153">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="33169-154">Bir `default` servis talebi yoksa ve eşleştirme ifadesi başka bir `case` etiketle eşleşmiyorsa, program akışı deyim aracılığıyla geçer `switch` .</span><span class="sxs-lookup"><span data-stu-id="33169-154">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="33169-155">`default`Durum, deyimdeki herhangi bir sırada görünebilir `switch` .</span><span class="sxs-lookup"><span data-stu-id="33169-155">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="33169-156">Kaynak kodundaki sıralarından bağımsız olarak, tüm Etiketler hesaplandıktan sonra her zaman son değerlendirilir `case` .</span><span class="sxs-lookup"><span data-stu-id="33169-156">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><a name="pattern"></a><span data-ttu-id="33169-157">Deyimle eşleşen desenler `switch`</span><span class="sxs-lookup"><span data-stu-id="33169-157">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="33169-158">Her `case` deyim, eşleşme ifadesiyle eşleşiyorsa, kapsayan anahtar bölümünün yürütülmesine neden olan bir model tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33169-158">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="33169-159">Tüm C# sürümleri sabit bir stili destekler.</span><span class="sxs-lookup"><span data-stu-id="33169-159">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="33169-160">Kalan desenler C# 7,0 ' den başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="33169-160">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="33169-161">Sabit model</span><span class="sxs-lookup"><span data-stu-id="33169-161">Constant pattern</span></span>

<span data-ttu-id="33169-162">Sabit model, eşleşme ifadesinin belirtilen bir sabit değere eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="33169-162">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="33169-163">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33169-163">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="33169-164">Burada *Constant* , test edilecek değerdir.</span><span class="sxs-lookup"><span data-stu-id="33169-164">where *constant* is the value to test for.</span></span> <span data-ttu-id="33169-165">*sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="33169-165">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="33169-166">Bir [bool](../builtin-types/bool.md) sabit değeri: `true` ya da `false` .</span><span class="sxs-lookup"><span data-stu-id="33169-166">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="33169-167">,, Veya gibi herhangi bir [integral](../builtin-types/integral-numeric-types.md) sabiti `int` `long` `byte` .</span><span class="sxs-lookup"><span data-stu-id="33169-167">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="33169-168">Belirtilen `const` değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="33169-168">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="33169-169">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="33169-169">An enumeration constant.</span></span>
- <span data-ttu-id="33169-170">Bir [char](../builtin-types/char.md) sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="33169-170">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="33169-171">[Dize](../builtin-types/reference-types.md) sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="33169-171">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="33169-172">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="33169-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="33169-173">*Expr* ve *Constant* Integral türse, C# eşitlik işleci ifadenin döndürülüp döndürülmeyeceğini `true` (yani, ne gibi `expr == constant` ) belirler.</span><span class="sxs-lookup"><span data-stu-id="33169-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="33169-174">Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="33169-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="33169-175">Aşağıdaki örnek, belirli bir tarihin hafta sonu, çalışma haftasının ilk günü mi, çalışma haftasının son günü mi yoksa çalışma haftasının ortasında mi olduğunu anlamak için sabit bir düzende kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33169-175">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="33169-176"><xref:System.DateTime.DayOfWeek?displayProperty=nameWithType>Geçerli günün özelliğini numaralandırmanın üyelerine göre değerlendirir <xref:System.DayOfWeek> .</span><span class="sxs-lookup"><span data-stu-id="33169-176">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="33169-177">Aşağıdaki örnek, bir otomatik kahve makinesine benzetim yapan bir konsol uygulamasında kullanıcı girişini işlemek için sabit bir model kullanır.</span><span class="sxs-lookup"><span data-stu-id="33169-177">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="33169-178">Tür stili</span><span class="sxs-lookup"><span data-stu-id="33169-178">Type pattern</span></span>

<span data-ttu-id="33169-179">Tür stili, kısa tür değerlendirmesi ve dönüştürmeyi mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="33169-179">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="33169-180">`switch`Model eşleştirmeyi gerçekleştirmek için ifadesiyle birlikte kullanıldığında, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülebileceğini sınar ve bu, mümkünse, bu türden bir değişkene bu değeri verebilir.</span><span class="sxs-lookup"><span data-stu-id="33169-180">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="33169-181">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33169-181">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="33169-182">Burada *tür* , *Expr* 'nin sonucunun dönüştürülecek türün adı ve *varname* , eşleşme başarılı olursa *ifadenin* sonucunun dönüştürüldüğü nesnedir.</span><span class="sxs-lookup"><span data-stu-id="33169-182">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="33169-183">*İfadenin* derleme zamanı türü, C# 7,1 ' den başlayarak genel bir tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="33169-183">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="33169-184">`case`İfadesi `true` aşağıdakilerden herhangi biri doğru ise olur:</span><span class="sxs-lookup"><span data-stu-id="33169-184">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="33169-185">*Expr* , *türü*ile aynı türde bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="33169-185">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="33169-186">*Expr* *türünden*türetilen bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="33169-186">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="33169-187">Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="33169-187">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="33169-188">*ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="33169-188">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="33169-189">Bir değişkenin *derleme zamanı türü* , tür bildiriminde tanımlanan değişkenin türüdür.</span><span class="sxs-lookup"><span data-stu-id="33169-189">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="33169-190">Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="33169-190">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="33169-191">*Expr* , *tür* arabirimini uygulayan bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="33169-191">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="33169-192">Case ifadesi true ise, *varname* kesinlikle atanır ve yalnızca switch bölümü içinde yerel kapsama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="33169-192">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="33169-193">`null`Bir türle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="33169-193">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="33169-194">Bir ile eşleştirmek için `null` aşağıdaki `case` etiketi kullanın:</span><span class="sxs-lookup"><span data-stu-id="33169-194">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="33169-195">Aşağıdaki örnek, çeşitli türlerdeki koleksiyon türleri hakkında bilgi sağlamak için tür modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="33169-195">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="33169-196">Yerine, `object` aşağıdaki kodda gösterildiği gibi, tür parametresi olarak koleksiyonun türünü kullanarak genel bir yöntem oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="33169-196">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="33169-197">Genel sürüm, ilk örnekten iki şekilde farklıdır.</span><span class="sxs-lookup"><span data-stu-id="33169-197">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="33169-198">İlk olarak, bu durumu kullanamazsınız `null` .</span><span class="sxs-lookup"><span data-stu-id="33169-198">First, you can't use the `null` case.</span></span> <span data-ttu-id="33169-199">Derleyici herhangi bir rastgele türü dışında herhangi bir türe dönüştüremediği için herhangi bir sabit durumu kullanamazsınız `T` `object` .</span><span class="sxs-lookup"><span data-stu-id="33169-199">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="33169-200">`default`Artık null olmayan bir durum için test edilmiş olabilir `object` .</span><span class="sxs-lookup"><span data-stu-id="33169-200">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="33169-201">Bu, `default` yalnızca için büyük/küçük harf testleri anlamına gelir `null` .</span><span class="sxs-lookup"><span data-stu-id="33169-201">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="33169-202">Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="33169-202">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="33169-203">Tür deseninin kullanımı, dönüştürmenin sonucunun bir `null` veya yinelenen yayınlar gerçekleştirmesini sağlamak için bir veya daha fazla okunabilir kod üretir.</span><span class="sxs-lookup"><span data-stu-id="33169-203">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="33169-204"><a name="when" />`case`Deyimi ve `when` yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="33169-204"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="33169-205">C# 7,0 ' den itibaren, Case deyimlerinin birbirini `when` dışlanması gerektiğinden, Case ifadesinin true olarak değerlendirilmesi için karşılanması gereken ek bir koşul belirtmek üzere bir yan tümce ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33169-205">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="33169-206">`when`Yan tümce, Boolean değer döndüren herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="33169-206">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="33169-207">Aşağıdaki örnek, bir temel `Shape` sınıf, `Rectangle` öğesinden türetilen bir sınıf `Shape` ve `Square` öğesinden türetilen bir `Rectangle` sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33169-207">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="33169-208">`when` `ShowShapeInfo` `Rectangle` Bir nesne `Square` olarak örneği oluşturulmasa bile eşit uzunlukta ve genişlikler atanan bir nesneyi bir nesne olarak değerlendirdiğinden emin olmak için yan tümcesini kullanır `Square` .</span><span class="sxs-lookup"><span data-stu-id="33169-208">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="33169-209">Yöntemi, `null` veya alanı sıfır olan bir şekil gibi bir nesne hakkında bilgi görüntülemeyi denemez.</span><span class="sxs-lookup"><span data-stu-id="33169-209">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="33169-210">`when`Örnekteki yan tümcesinin, bir `Shape` nesnenin yürütülüp yürütülmediğini test girişiminde bulunduğunu unutmayın `null` .</span><span class="sxs-lookup"><span data-stu-id="33169-210">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="33169-211">Bir için test edilecek doğru tür deseninin türü `null` `case null:` .</span><span class="sxs-lookup"><span data-stu-id="33169-211">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="33169-212">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="33169-212">C# language specification</span></span>

<span data-ttu-id="33169-213">Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Switch ifadesine](~/_csharplang/spec/statements.md#the-switch-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="33169-213">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="33169-214">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="33169-214">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="33169-215">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33169-215">See also</span></span>

- [<span data-ttu-id="33169-216">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="33169-216">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="33169-217">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="33169-217">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="33169-218">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="33169-218">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="33169-219">if-else</span><span class="sxs-lookup"><span data-stu-id="33169-219">if-else</span></span>](if-else.md)
- [<span data-ttu-id="33169-220">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="33169-220">Pattern Matching</span></span>](../../pattern-matching.md)

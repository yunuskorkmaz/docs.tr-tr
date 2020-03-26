---
title: C# anahtar deyimi
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
ms.openlocfilehash: 49b3836f17e91ae8de10d68e97fd662aae80d1ff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249324"
---
# <a name="switch-c-reference"></a><span data-ttu-id="61d8d-102">anahtar (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="61d8d-102">switch (C# reference)</span></span>

<span data-ttu-id="61d8d-103">Bu makale, `switch` deyimi kapsar.</span><span class="sxs-lookup"><span data-stu-id="61d8d-103">This article covers the `switch` statement.</span></span> <span data-ttu-id="61d8d-104">İfade (C# `switch` 8.0'da tanıtılan) ile ilgili bilgi [için, ifadeler ve işleçler](../operators/index.md) bölümündeki [ `switch` ifadeler](../operators/switch-expression.md) hakkındaki makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="61d8d-104">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="61d8d-105">`switch`*eşleşme ifadesi*ile bir desen eşleşmesi dayalı aday listesinden yürütmek için tek bir *anahtar bölümü* seçen bir seçim deyimidir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-105">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="61d8d-106">Tek `switch` bir ifade üç veya daha fazla koşula karşı test edilirse, deyim genellikle [if-else](if-else.md) yapısına alternatif olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-106">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="61d8d-107">Örneğin, aşağıdaki `switch` deyim, tür `Color` değişkeninin üç değerden birine sahip olup olmadığını belirler:</span><span class="sxs-lookup"><span data-stu-id="61d8d-107">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="61d8d-108">Bir `if` - `else` yapıyı kullanan aşağıdaki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-108">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="61d8d-109">Maç ifadesi</span><span class="sxs-lookup"><span data-stu-id="61d8d-109">The match expression</span></span>

<span data-ttu-id="61d8d-110">Eşmatch ifadesi etiketlerdeki `case` desenlerle eşleşen değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="61d8d-110">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="61d8d-111">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="61d8d-111">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="61d8d-112">C# 6 ve daha önce, eşleşme ifadesi aşağıdaki türlerin bir değeri döndüren bir ifade olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="61d8d-112">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="61d8d-113">bir [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="61d8d-113">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="61d8d-114">bir [dize](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="61d8d-114">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="61d8d-115">bir [bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="61d8d-115">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="61d8d-116">gibi [integral](../builtin-types/integral-numeric-types.md) `int` bir integral değeri veya `long`bir .</span><span class="sxs-lookup"><span data-stu-id="61d8d-116">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="61d8d-117">bir [enum](../builtin-types/enum.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="61d8d-117">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="61d8d-118">C# 7.0 ile başlayarak, eşleşme ifadesi null olmayan herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-118">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="61d8d-119">Anahtar bölümü</span><span class="sxs-lookup"><span data-stu-id="61d8d-119">The switch section</span></span>

<span data-ttu-id="61d8d-120">Deyim, `switch` bir veya daha fazla anahtar bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-120">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="61d8d-121">Her geçiş bölümü bir veya daha fazla *büyük/küçük harf etiketi* (büyük/küçük harf veya varsayılan etiket) ve ardından bir veya daha fazla deyim içerir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-121">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="61d8d-122">İfade, `switch` herhangi bir anahtar bölümüne yerleştirilen en fazla bir varsayılan etiket içerebilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-122">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="61d8d-123">Aşağıdaki örnekte, `switch` her biri iki deyim içeren üç geçiş bölümü içeren basit bir ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-123">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="61d8d-124">İkinci anahtar bölümü `case 2:` ve `case 3:` etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-124">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="61d8d-125">Bir `switch` deyim herhangi bir sayıda geçiş bölümü içerebilir ve her bölümde aşağıdaki örnekte gösterildiği gibi bir veya daha fazla servis talebi etiketi bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="61d8d-126">Ancak, iki büyük/küçük harf etiketi aynı ifadeyi içeremez.</span><span class="sxs-lookup"><span data-stu-id="61d8d-126">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="61d8d-127">Anahtar deyiminde yalnızca bir anahtar bölümü çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-127">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="61d8d-128">C# yürütmenin bir anahtar bölümünden diğerine devam etmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="61d8d-128">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="61d8d-129">Bu nedenle, aşağıdaki kod bir derleyici hatası oluşturur, CS0163: "Denetim bir\<büyük/harf etiketinden (büyük/küçük harf etiketi>) diğerine düşemez."</span><span class="sxs-lookup"><span data-stu-id="61d8d-129">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="61d8d-130">Bu gereksinim genellikle bir [ara](break.md), [goto](goto.md)veya [iade](return.md) deyimi kullanılarak anahtar bölümünden açıkça çıkarılarak karşılanır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-130">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="61d8d-131">Ancak, program denetiminin `default` geçiş bölümüne girememesini sağladığından, aşağıdaki kod da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-131">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="61d8d-132">Eşmaç ifadesiyle eşleşen bir durum etiketiyle geçiş bölümündeki ifade listesinin yürütülmesi ilk deyimle başlar ve genellikle bir `break`atlama `goto case` `goto label`deyimi `return`, `throw`, , , , veya , gibi bir atlama deyimine ulaşılıncaya kadar, ekstre listesi boyunca ilerler.</span><span class="sxs-lookup"><span data-stu-id="61d8d-132">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="61d8d-133">Bu noktada, denetim deyimi `switch` dışında veya başka bir servis talebi etiketine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-133">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="61d8d-134">Bir `goto` deyim, kullanılırsa, denetimi sabit bir etikete aktarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-134">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="61d8d-135">Denetimi sabit olmayan bir etikete aktarmaya çalışmak istenmeyen yan etkilere sahip olabileceğinden, denetimi kodda istenmeyen bir konuma aktarmak veya sonsuz bir döngü oluşturmak gibi bu kısıtlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-135">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="61d8d-136">Büyük/küçük harf etiketleri</span><span class="sxs-lookup"><span data-stu-id="61d8d-136">Case labels</span></span>

<span data-ttu-id="61d8d-137">Her servis talebi etiketi, eşleşme ifadesiyle (önceki `caseSwitch` örneklerdeki değişken) karşılaştırmak için bir desen belirtir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-137">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="61d8d-138">Eşleşirse, denetim **ilk** eşleşen servis talebi etiketini içeren anahtar bölümüne aktarılır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-138">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="61d8d-139">Büyük/küçük harf etiketi deseni eşleşme ifadesiyle eşleşmiyorsa, denetim varsa servis talebi etiketinin `default` olduğu bölüme aktarılır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-139">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="61d8d-140">Servis talebi yoksa, `default` herhangi bir anahtar bölümündeki ifadeler yürütülür `switch` ve denetim ifadenin dışına aktarılır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-140">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="61d8d-141">Deyim ve `switch` desen eşleştirmesi hakkında bilgi için [deyim bölümüyle eşleşen Desen'e `switch` ](#pattern) bakın.</span><span class="sxs-lookup"><span data-stu-id="61d8d-141">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="61d8d-142">C# 6 yalnızca sabit deseni desteklediğinden ve sabit değerlerin tekrarına izin vermedığından, büyük/küçük harf etiketleri birbirini dışlayan değerleri tanımlar ve eşleç ifadesiyle yalnızca bir desen eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-142">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="61d8d-143">Sonuç olarak, deyimlerin `case` görüntülenme sırası önemsizdir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-143">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="61d8d-144">Ancak C# 7.0'da, diğer desenler desteklendirildik, büyük/küçük harf etiketleri birbirini dışlayan değerler tanımlamaz ve birden çok desen eşleç ifadeyle eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-144">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="61d8d-145">Yalnızca eşleşen deseni içeren ilk anahtar bölümündeki ifadeler yürütüldünlü olduğundan, deyimlerin görüntülenme `case` sırası artık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-145">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="61d8d-146">C#, servis talebi bildirimi veya deyimleri önceki deyimlerin alt kümelerine eşdeğer veya alt kümeleri olan bir anahtar bölümü algılarsa, bir derleyici hatası oluşturur, CS8120, "Anahtar durumu zaten önceki bir servis talebi tarafından işlenmiştir."</span><span class="sxs-lookup"><span data-stu-id="61d8d-146">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="61d8d-147">Aşağıdaki örnekte, `switch` birbirini dışlayan çeşitli desenler kullanan bir deyim gösterin.</span><span class="sxs-lookup"><span data-stu-id="61d8d-147">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="61d8d-148">`case 0:` Anahtar bölümünü artık `switch` deyimdeki ilk bölüm olmayacak şekilde taşırsanız, Değeri sıfır olan bir tamsayı tüm tamsayılara ait bir alt küme olduğundan C# derleyici hatası oluşturur, bu `case int val` da deyimtarafından tanımlanan desendir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-148">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="61d8d-149">Bu sorunu düzeltebilir ve derleyici uyarısını iki şekilde ortadan kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="61d8d-149">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="61d8d-150">Anahtar bölümlerinin sırasını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="61d8d-150">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="61d8d-151">Etikette bir when `case` yan [tümcesi](#when) kullanarak.</span><span class="sxs-lookup"><span data-stu-id="61d8d-151">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="61d8d-152">Dava `default`</span><span class="sxs-lookup"><span data-stu-id="61d8d-152">The `default` case</span></span>

<span data-ttu-id="61d8d-153">Servis `default` talebi, eşleşme ifadesi başka `case` bir etiketle eşleşmiyorsa, yürütülecek anahtar bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-153">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="61d8d-154">Bir `default` servis talebi yoksa ve eşleşme ifadesi başka `case` bir etiketle eşleşmiyorsa, program akışı deyimden `switch` düşer.</span><span class="sxs-lookup"><span data-stu-id="61d8d-154">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="61d8d-155">Servis `default` `switch` talebi, ifadedeki herhangi bir sırada görünebilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-155">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="61d8d-156">Kaynak kodundaki sırası ne olursa olsun, tüm `case` etiketler değerlendirildikten sonra her zaman en son değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-156">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="61d8d-157"><a name="pattern" />`switch` Deyimle eşleşen desen</span><span class="sxs-lookup"><span data-stu-id="61d8d-157"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="61d8d-158">Her `case` deyim, eşleşme ifadesiyle eşleşirse, içerdiği anahtar bölümünün yürütülmesine neden olan bir desen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="61d8d-158">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="61d8d-159">C#'nin tüm sürümleri sabit deseni destekler.</span><span class="sxs-lookup"><span data-stu-id="61d8d-159">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="61d8d-160">Kalan desenler C# 7.0 ile başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-160">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="61d8d-161">Sabit desen</span><span class="sxs-lookup"><span data-stu-id="61d8d-161">Constant pattern</span></span>

<span data-ttu-id="61d8d-162">Sabit desen, eşleşme ifadesinin belirtilen bir sabite eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="61d8d-162">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="61d8d-163">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="61d8d-163">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="61d8d-164">*sabit* için test etmek için değer olduğu.</span><span class="sxs-lookup"><span data-stu-id="61d8d-164">where *constant* is the value to test for.</span></span> <span data-ttu-id="61d8d-165">*sabit* aşağıdaki sabit ifadelerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="61d8d-165">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="61d8d-166">Bir [bool](../builtin-types/bool.md) literal: `false`ya da `true` .</span><span class="sxs-lookup"><span data-stu-id="61d8d-166">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="61d8d-167">Herhangi [integral](../builtin-types/integral-numeric-types.md) bir `int`integral sabiti, `long`a `byte`, veya bir .</span><span class="sxs-lookup"><span data-stu-id="61d8d-167">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="61d8d-168">Bildirilen `const` değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="61d8d-168">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="61d8d-169">Numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="61d8d-169">An enumeration constant.</span></span>
- <span data-ttu-id="61d8d-170">Bir [char](../builtin-types/char.md) edebi.</span><span class="sxs-lookup"><span data-stu-id="61d8d-170">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="61d8d-171">Bir [dize](../builtin-types/reference-types.md) gerçek.</span><span class="sxs-lookup"><span data-stu-id="61d8d-171">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="61d8d-172">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="61d8d-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="61d8d-173">*Expr* ve *constant* integral türleri ise, C# eşitlik işleci `true` ifadenin döndürüp döndürülmediğini (yani, olup olmadığını) `expr == constant`belirler.</span><span class="sxs-lookup"><span data-stu-id="61d8d-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="61d8d-174">Aksi takdirde, ifadenin değeri statik [Object.Equals (expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemine yapılan bir çağrı ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="61d8d-175">Aşağıdaki örnek, belirli bir tarihin hafta sonu, çalışma haftasının ilk günü, çalışma haftasının son günü veya çalışma haftasının ortası olup olmadığını belirlemek için sabit deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-175">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="61d8d-176">Bu numaralandırma <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> üyeleri <xref:System.DayOfWeek> nezdinde mevcut günün özelliğini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-176">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="61d8d-177">Aşağıdaki örnek, otomatik kahve makinesini taklit eden bir konsol uygulamasında kullanıcı girişini işlemek için sabit deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-177">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="61d8d-178">Tür deseni</span><span class="sxs-lookup"><span data-stu-id="61d8d-178">Type pattern</span></span>

<span data-ttu-id="61d8d-179">Tür deseni kısa tür değerlendirme ve dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="61d8d-179">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="61d8d-180">Desen eşleştirmesi `switch` gerçekleştirmek için deyimle kullanıldığında, bir ifadenin belirli bir türe dönüştürülüp dönüştürülemeyeceğini sınar ve olabilirse, bu tür bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="61d8d-180">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="61d8d-181">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="61d8d-181">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="61d8d-182">*tür,* *expr* sonucunun dönüştürüldüğü türün adıdır ve *varname,* eşleşme başarılı olursa *expr* sonucunun dönüştürüldüğü nesnedir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-182">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="61d8d-183">Derleme zamanı *expr* türü, C# 7.1 ile başlayan genel bir tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-183">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="61d8d-184">İfade, `case` `true` aşağıdakilerden herhangi birinin doğru olup olmadığıdır:</span><span class="sxs-lookup"><span data-stu-id="61d8d-184">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="61d8d-185">*expr* *türü*olarak aynı türde bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-185">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="61d8d-186">*expr* *türünden*türetilen bir tür örneğidir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-186">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="61d8d-187">Başka bir deyişle, *expr* sonucu *türü*bir örnek için upcast olabilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-187">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="61d8d-188">*expr* *türü*bir taban sınıf olan bir derleme-zaman türü vardır ve *expr* *türü* veya *türünden*türetilen bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-188">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="61d8d-189">Bir değişkenin *derleme zamanı türü,* değişkenin tür bildiriminde tanımlandığı şekilde türüdür.</span><span class="sxs-lookup"><span data-stu-id="61d8d-189">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="61d8d-190">Bir değişkenin *çalışma zamanı türü,* bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="61d8d-190">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="61d8d-191">*expr* *türü* arabirimi uygulayan bir tür örneğidir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-191">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="61d8d-192">Servis talebi ifadesi doğruysa, *varname* kesinlikle atanır ve yalnızca geçiş bölümünde yerel kapsama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-192">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="61d8d-193">Bir `null` türle eşleşmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61d8d-193">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="61d8d-194">Bir `null`eşlemek için aşağıdaki `case` etiketi kullanın:</span><span class="sxs-lookup"><span data-stu-id="61d8d-194">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="61d8d-195">Aşağıdaki örnek, çeşitli koleksiyon türleri hakkında bilgi sağlamak için tür deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-195">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="61d8d-196">Bunun `object`yerine, aşağıdaki kodda gösterildiği gibi, tür parametresi olarak koleksiyonun türünü kullanarak genel bir yöntem yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="61d8d-196">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="61d8d-197">Genel sürüm iki şekilde ilk örnek farklıdır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-197">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="61d8d-198">İlk olarak, çantayı `null` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="61d8d-198">First, you can't use the `null` case.</span></span> <span data-ttu-id="61d8d-199">Derleyici herhangi bir rasgele türü `T` `object`başka bir türe dönüştüremediğinden sabit bir servis talebi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="61d8d-199">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="61d8d-200">Ne `default` durumda şimdi olmayan bir null `object`için testler olmuştu .</span><span class="sxs-lookup"><span data-stu-id="61d8d-200">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="61d8d-201">Bu, `default` vaka testlerinin `null`yalnızca .</span><span class="sxs-lookup"><span data-stu-id="61d8d-201">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="61d8d-202">Desen eşleştirme olmadan, bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-202">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="61d8d-203">Tür deseni eşleştirmesinin kullanımı, dönüştürme nin sonucunun bir `null` mi yoksa tekrarlanan dökümler mi olduğunu test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-203">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="61d8d-204"><a name="when" />İfade `case` ve `when` fıkra</span><span class="sxs-lookup"><span data-stu-id="61d8d-204"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="61d8d-205">C# 7.0 ile başlayarak, büyük/küçük harf deyimleri `when` birbirini dışlamadığıiçin, servis talebi bildiriminin doğru olarak değerlendirilmesi için tatmin edilmesi gereken ek bir koşul belirtmek için bir yan tümce ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61d8d-205">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="61d8d-206">Yan `when` tümce boolean değerini döndüren herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="61d8d-206">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="61d8d-207">Aşağıdaki örnekte bir `Shape` taban sınıf, `Rectangle` ve 'den `Shape`türeyen bir sınıf `Rectangle`ve .'den türeyen bir `Square` sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-207">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="61d8d-208">Bir `Square` nesne `when` olarak anında `ShowShapeInfo` değil olsa `Rectangle` `Square` bile eşit uzunlukve genişlikleri atanmış bir nesneyi davranır sağlamak için yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-208">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="61d8d-209">Yöntem, alanı sıfır olan `null` bir nesne veya şekil hakkında bilgi görüntülemeye çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="61d8d-209">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="61d8d-210">Örnekteki `when` `Shape` nesnenin yürütülüp uygulanmadığını sınamaya `null` çalışan yan tümcesinin yürütülmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61d8d-210">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="61d8d-211">Bir `null` için test etmek için `case null:`doğru tür deseni .</span><span class="sxs-lookup"><span data-stu-id="61d8d-211">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="61d8d-212">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="61d8d-212">C# language specification</span></span>

<span data-ttu-id="61d8d-213">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [geçiş deyimine](~/_csharplang/spec/statements.md#the-switch-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="61d8d-213">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="61d8d-214">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="61d8d-214">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="61d8d-215">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61d8d-215">See also</span></span>

- [<span data-ttu-id="61d8d-216">C# Referans</span><span class="sxs-lookup"><span data-stu-id="61d8d-216">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="61d8d-217">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="61d8d-217">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="61d8d-218">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="61d8d-218">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="61d8d-219">if-else</span><span class="sxs-lookup"><span data-stu-id="61d8d-219">if-else</span></span>](if-else.md)
- [<span data-ttu-id="61d8d-220">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="61d8d-220">Pattern Matching</span></span>](../../pattern-matching.md)

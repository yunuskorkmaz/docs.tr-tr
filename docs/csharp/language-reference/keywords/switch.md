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
ms.openlocfilehash: e5580e81b9175cd95491fdba724bacbffa692a5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345388"
---
# <a name="switch-c-reference"></a><span data-ttu-id="4c13a-102">anahtar (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="4c13a-102">switch (C# reference)</span></span>

<span data-ttu-id="4c13a-103">`switch`*eşleşme ifadesi*ile bir desen eşleşmesi dayalı aday listesinden yürütmek için tek bir *anahtar bölümü* seçen bir seçim deyimidir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="4c13a-104">Tek `switch` bir ifade üç veya daha fazla koşula karşı test edilirse, deyim genellikle [if-else](if-else.md) yapısına alternatif olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="4c13a-105">Örneğin, aşağıdaki `switch` deyim, tür `Color` değişkeninin üç değerden birine sahip olup olmadığını belirler:</span><span class="sxs-lookup"><span data-stu-id="4c13a-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="4c13a-106">Bir `if` - `else` yapıyı kullanan aşağıdaki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-106">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="4c13a-107">Maç ifadesi</span><span class="sxs-lookup"><span data-stu-id="4c13a-107">The match expression</span></span>

<span data-ttu-id="4c13a-108">Eşmatch ifadesi etiketlerdeki `case` desenlerle eşleşen değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c13a-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="4c13a-109">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="4c13a-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="4c13a-110">C# 6 ve daha önce, eşleşme ifadesi aşağıdaki türlerin bir değeri döndüren bir ifade olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="4c13a-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="4c13a-111">bir [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="4c13a-111">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="4c13a-112">bir [dize](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="4c13a-112">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="4c13a-113">bir [bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="4c13a-113">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="4c13a-114">gibi [integral](../builtin-types/integral-numeric-types.md) `int` bir integral değeri veya `long`bir .</span><span class="sxs-lookup"><span data-stu-id="4c13a-114">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="4c13a-115">bir [enum](../builtin-types/enum.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="4c13a-115">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="4c13a-116">C# 7.0 ile başlayarak, eşleşme ifadesi null olmayan herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="4c13a-117">Anahtar bölümü</span><span class="sxs-lookup"><span data-stu-id="4c13a-117">The switch section</span></span>

<span data-ttu-id="4c13a-118">Deyim, `switch` bir veya daha fazla anahtar bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="4c13a-119">Her geçiş bölümü bir veya daha fazla *büyük/küçük harf etiketi* (büyük/küçük harf veya varsayılan etiket) ve ardından bir veya daha fazla deyim içerir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="4c13a-120">İfade, `switch` herhangi bir anahtar bölümüne yerleştirilen en fazla bir varsayılan etiket içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="4c13a-121">Aşağıdaki örnekte, `switch` her biri iki deyim içeren üç geçiş bölümü içeren basit bir ifade gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="4c13a-122">İkinci anahtar bölümü `case 2:` ve `case 3:` etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="4c13a-123">Bir `switch` deyim herhangi bir sayıda geçiş bölümü içerebilir ve her bölümde aşağıdaki örnekte gösterildiği gibi bir veya daha fazla servis talebi etiketi bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="4c13a-124">Ancak, iki büyük/küçük harf etiketi aynı ifadeyi içeremez.</span><span class="sxs-lookup"><span data-stu-id="4c13a-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="4c13a-125">Anahtar deyiminde yalnızca bir anahtar bölümü çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="4c13a-126">C# yürütmenin bir anahtar bölümünden diğerine devam etmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="4c13a-126">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="4c13a-127">Bu nedenle, aşağıdaki kod bir derleyici hatası oluşturur, CS0163: "Denetim bir\<büyük/harf etiketinden (büyük/küçük harf etiketi>) diğerine düşemez."</span><span class="sxs-lookup"><span data-stu-id="4c13a-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="4c13a-128">Bu gereksinim genellikle bir [ara](break.md), [goto](goto.md)veya [iade](return.md) deyimi kullanılarak anahtar bölümünden açıkça çıkarılarak karşılanır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="4c13a-129">Ancak, program denetiminin `default` geçiş bölümüne girememesini sağladığından, aşağıdaki kod da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="4c13a-130">Eşmaç ifadesiyle eşleşen bir durum etiketiyle geçiş bölümündeki ifade listesinin yürütülmesi ilk deyimle başlar ve genellikle bir `break`atlama `goto case` `goto label`deyimi `return`, `throw`, , , , veya , gibi bir atlama deyimine ulaşılıncaya kadar, ekstre listesi boyunca ilerler.</span><span class="sxs-lookup"><span data-stu-id="4c13a-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="4c13a-131">Bu noktada, denetim deyimi `switch` dışında veya başka bir servis talebi etiketine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="4c13a-132">Bir `goto` deyim, kullanılırsa, denetimi sabit bir etikete aktarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-132">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="4c13a-133">Denetimi sabit olmayan bir etikete aktarmaya çalışmak istenmeyen yan etkilere sahip olabileceğinden, denetimi kodda istenmeyen bir konuma aktarmak veya sonsuz bir döngü oluşturmak gibi bu kısıtlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="4c13a-134">Büyük/küçük harf etiketleri</span><span class="sxs-lookup"><span data-stu-id="4c13a-134">Case labels</span></span>

<span data-ttu-id="4c13a-135">Her servis talebi etiketi, eşleşme ifadesiyle (önceki `caseSwitch` örneklerdeki değişken) karşılaştırmak için bir desen belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="4c13a-136">Eşleşirse, denetim **ilk** eşleşen servis talebi etiketini içeren anahtar bölümüne aktarılır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="4c13a-137">Büyük/küçük harf etiketi deseni eşleşme ifadesiyle eşleşmiyorsa, denetim varsa servis talebi etiketinin `default` olduğu bölüme aktarılır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="4c13a-138">Servis talebi yoksa, `default` herhangi bir anahtar bölümündeki ifadeler yürütülür `switch` ve denetim ifadenin dışına aktarılır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="4c13a-139">Deyim ve `switch` desen eşleştirmesi hakkında bilgi için [deyim bölümüyle eşleşen Desen'e `switch` ](#pattern) bakın.</span><span class="sxs-lookup"><span data-stu-id="4c13a-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="4c13a-140">C# 6 yalnızca sabit deseni desteklediğinden ve sabit değerlerin tekrarına izin vermedığından, büyük/küçük harf etiketleri birbirini dışlayan değerleri tanımlar ve eşleç ifadesiyle yalnızca bir desen eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="4c13a-141">Sonuç olarak, deyimlerin `case` görüntülenme sırası önemsizdir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="4c13a-142">Ancak C# 7.0'da, diğer desenler desteklendirildik, büyük/küçük harf etiketleri birbirini dışlayan değerler tanımlamaz ve birden çok desen eşleç ifadeyle eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="4c13a-143">Yalnızca eşleşen deseni içeren ilk anahtar bölümündeki ifadeler yürütüldünlü olduğundan, deyimlerin görüntülenme `case` sırası artık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="4c13a-144">C#, servis talebi bildirimi veya deyimleri önceki deyimlerin alt kümelerine eşdeğer veya alt kümeleri olan bir anahtar bölümü algılarsa, bir derleyici hatası oluşturur, CS8120, "Anahtar durumu zaten önceki bir servis talebi tarafından işlenmiştir."</span><span class="sxs-lookup"><span data-stu-id="4c13a-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="4c13a-145">Aşağıdaki örnekte, `switch` birbirini dışlayan çeşitli desenler kullanan bir deyim gösterin.</span><span class="sxs-lookup"><span data-stu-id="4c13a-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="4c13a-146">`case 0:` Anahtar bölümünü artık `switch` deyimdeki ilk bölüm olmayacak şekilde taşırsanız, Değeri sıfır olan bir tamsayı tüm tamsayılara ait bir alt küme olduğundan C# derleyici hatası oluşturur, bu `case int val` da deyimtarafından tanımlanan desendir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="4c13a-147">Bu sorunu düzeltebilir ve derleyici uyarısını iki şekilde ortadan kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c13a-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="4c13a-148">Anahtar bölümlerinin sırasını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="4c13a-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="4c13a-149">Etikette bir when `case` yan [tümcesi](#when) kullanarak.</span><span class="sxs-lookup"><span data-stu-id="4c13a-149">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="4c13a-150">Dava `default`</span><span class="sxs-lookup"><span data-stu-id="4c13a-150">The `default` case</span></span>

<span data-ttu-id="4c13a-151">Servis `default` talebi, eşleşme ifadesi başka `case` bir etiketle eşleşmiyorsa, yürütülecek anahtar bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="4c13a-152">Bir `default` servis talebi yoksa ve eşleşme ifadesi başka `case` bir etiketle eşleşmiyorsa, program akışı deyimden `switch` düşer.</span><span class="sxs-lookup"><span data-stu-id="4c13a-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="4c13a-153">Servis `default` `switch` talebi, ifadedeki herhangi bir sırada görünebilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="4c13a-154">Kaynak kodundaki sırası ne olursa olsun, tüm `case` etiketler değerlendirildikten sonra her zaman en son değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="4c13a-155"><a name="pattern" />`switch` Deyimle eşleşen desen</span><span class="sxs-lookup"><span data-stu-id="4c13a-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="4c13a-156">Her `case` deyim, eşleşme ifadesiyle eşleşirse, içerdiği anahtar bölümünün yürütülmesine neden olan bir desen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4c13a-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="4c13a-157">C#'nin tüm sürümleri sabit deseni destekler.</span><span class="sxs-lookup"><span data-stu-id="4c13a-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="4c13a-158">Kalan desenler C# 7.0 ile başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="4c13a-159">Sabit desen</span><span class="sxs-lookup"><span data-stu-id="4c13a-159">Constant pattern</span></span>

<span data-ttu-id="4c13a-160">Sabit desen, eşleşme ifadesinin belirtilen bir sabite eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="4c13a-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="4c13a-161">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="4c13a-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="4c13a-162">*sabit* için test etmek için değer olduğu.</span><span class="sxs-lookup"><span data-stu-id="4c13a-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="4c13a-163">*sabit* aşağıdaki sabit ifadelerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="4c13a-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="4c13a-164">Bir [bool](../builtin-types/bool.md) literal: `false`ya da `true` .</span><span class="sxs-lookup"><span data-stu-id="4c13a-164">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="4c13a-165">Herhangi [integral](../builtin-types/integral-numeric-types.md) bir `int`integral sabiti, `long`a `byte`, veya bir .</span><span class="sxs-lookup"><span data-stu-id="4c13a-165">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="4c13a-166">Bildirilen `const` değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="4c13a-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="4c13a-167">Numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="4c13a-167">An enumeration constant.</span></span>
- <span data-ttu-id="4c13a-168">Bir [char](../builtin-types/char.md) edebi.</span><span class="sxs-lookup"><span data-stu-id="4c13a-168">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="4c13a-169">Bir [dize](../builtin-types/reference-types.md) gerçek.</span><span class="sxs-lookup"><span data-stu-id="4c13a-169">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="4c13a-170">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="4c13a-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="4c13a-171">*Expr* ve *constant* integral türleri ise, C# eşitlik işleci `true` ifadenin döndürüp döndürülmediğini (yani, olup olmadığını) `expr == constant`belirler.</span><span class="sxs-lookup"><span data-stu-id="4c13a-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="4c13a-172">Aksi takdirde, ifadenin değeri statik [Object.Equals (expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemine yapılan bir çağrı ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="4c13a-173">Aşağıdaki örnek, belirli bir tarihin hafta sonu, çalışma haftasının ilk günü, çalışma haftasının son günü veya çalışma haftasının ortası olup olmadığını belirlemek için sabit deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="4c13a-174">Bu numaralandırma <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> üyeleri <xref:System.DayOfWeek> nezdinde mevcut günün özelliğini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="4c13a-175">Aşağıdaki örnek, otomatik kahve makinesini taklit eden bir konsol uygulamasında kullanıcı girişini işlemek için sabit deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="4c13a-176">Tür deseni</span><span class="sxs-lookup"><span data-stu-id="4c13a-176">Type pattern</span></span>

<span data-ttu-id="4c13a-177">Tür deseni kısa tür değerlendirme ve dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c13a-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="4c13a-178">Desen eşleştirmesi `switch` gerçekleştirmek için deyimle kullanıldığında, bir ifadenin belirli bir türe dönüştürülüp dönüştürülemeyeceğini sınar ve olabilirse, bu tür bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="4c13a-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="4c13a-179">Sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="4c13a-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="4c13a-180">*tür,* *expr* sonucunun dönüştürüldüğü türün adıdır ve *varname,* eşleşme başarılı olursa *expr* sonucunun dönüştürüldüğü nesnedir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="4c13a-181">Derleme zamanı *expr* türü, C# 7.1 ile başlayan genel bir tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="4c13a-182">İfade, `case` `true` aşağıdakilerden herhangi birinin doğru olup olmadığıdır:</span><span class="sxs-lookup"><span data-stu-id="4c13a-182">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="4c13a-183">*expr* *türü*olarak aynı türde bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-183">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="4c13a-184">*expr* *türünden*türetilen bir tür örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-184">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="4c13a-185">Başka bir deyişle, *expr* sonucu *türü*bir örnek için upcast olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="4c13a-186">*expr* *türü*bir taban sınıf olan bir derleme-zaman türü vardır ve *expr* *türü* veya *türünden*türetilen bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="4c13a-187">Bir değişkenin *derleme zamanı türü,* değişkenin tür bildiriminde tanımlandığı şekilde türüdür.</span><span class="sxs-lookup"><span data-stu-id="4c13a-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="4c13a-188">Bir değişkenin *çalışma zamanı türü,* bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="4c13a-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="4c13a-189">*expr* *türü* arabirimi uygulayan bir tür örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-189">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="4c13a-190">Servis talebi ifadesi doğruysa, *varname* kesinlikle atanır ve yalnızca geçiş bölümünde yerel kapsama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="4c13a-191">Bir `null` türle eşleşmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4c13a-191">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="4c13a-192">Bir `null`eşlemek için aşağıdaki `case` etiketi kullanın:</span><span class="sxs-lookup"><span data-stu-id="4c13a-192">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="4c13a-193">Aşağıdaki örnek, çeşitli koleksiyon türleri hakkında bilgi sağlamak için tür deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-193">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="4c13a-194">Bunun `object`yerine, aşağıdaki kodda gösterildiği gibi, tür parametresi olarak koleksiyonun türünü kullanarak genel bir yöntem yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c13a-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="4c13a-195">Genel sürüm iki şekilde ilk örnek farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-195">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="4c13a-196">İlk olarak, çantayı `null` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4c13a-196">First, you can't use the `null` case.</span></span> <span data-ttu-id="4c13a-197">Derleyici herhangi bir rasgele türü `T` `object`başka bir türe dönüştüremediğinden sabit bir servis talebi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4c13a-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="4c13a-198">Ne `default` durumda şimdi olmayan bir null `object`için testler olmuştu .</span><span class="sxs-lookup"><span data-stu-id="4c13a-198">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="4c13a-199">Bu, `default` vaka testlerinin `null`yalnızca .</span><span class="sxs-lookup"><span data-stu-id="4c13a-199">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="4c13a-200">Desen eşleştirme olmadan, bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-200">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="4c13a-201">Tür deseni eşleştirmesinin kullanımı, dönüştürme nin sonucunun bir `null` mi yoksa tekrarlanan dökümler mi olduğunu test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="4c13a-202"><a name="when" />İfade `case` ve `when` fıkra</span><span class="sxs-lookup"><span data-stu-id="4c13a-202"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="4c13a-203">C# 7.0 ile başlayarak, büyük/küçük harf deyimleri `when` birbirini dışlamadığıiçin, servis talebi bildiriminin doğru olarak değerlendirilmesi için tatmin edilmesi gereken ek bir koşul belirtmek için bir yan tümce ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c13a-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="4c13a-204">Yan `when` tümce boolean değerini döndüren herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c13a-204">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="4c13a-205">Aşağıdaki örnekte bir `Shape` taban sınıf, `Rectangle` ve 'den `Shape`türeyen bir sınıf `Rectangle`ve .'den türeyen bir `Square` sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="4c13a-206">Bir `Square` nesne `when` olarak anında `ShowShapeInfo` değil olsa `Rectangle` `Square` bile eşit uzunlukve genişlikleri atanmış bir nesneyi davranır sağlamak için yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="4c13a-207">Yöntem, alanı sıfır olan `null` bir nesne veya şekil hakkında bilgi görüntülemeye çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4c13a-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="4c13a-208">Örnekteki `when` `Shape` nesnenin yürütülüp uygulanmadığını sınamaya `null` çalışan yan tümcesinin yürütülmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4c13a-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="4c13a-209">Bir `null` için test etmek için `case null:`doğru tür deseni .</span><span class="sxs-lookup"><span data-stu-id="4c13a-209">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4c13a-210">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4c13a-210">C# language specification</span></span>

<span data-ttu-id="4c13a-211">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [geçiş deyimine](~/_csharplang/spec/statements.md#the-switch-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="4c13a-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="4c13a-212">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="4c13a-212">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c13a-213">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c13a-213">See also</span></span>

- [<span data-ttu-id="4c13a-214">C# Referans</span><span class="sxs-lookup"><span data-stu-id="4c13a-214">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4c13a-215">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4c13a-215">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4c13a-216">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="4c13a-216">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4c13a-217">if-else</span><span class="sxs-lookup"><span data-stu-id="4c13a-217">if-else</span></span>](if-else.md)
- [<span data-ttu-id="4c13a-218">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="4c13a-218">Pattern Matching</span></span>](../../pattern-matching.md)

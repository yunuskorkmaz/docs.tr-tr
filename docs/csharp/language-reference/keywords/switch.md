---
title: C#Switch deyimleri
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
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345388"
---
# <a name="switch-c-reference"></a><span data-ttu-id="86688-102">anahtar (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="86688-102">switch (C# reference)</span></span>

<span data-ttu-id="86688-103">`switch`, *Match ifadesiyle*bir model eşleşmesi temelinde aday listesinden yürütülecek tek bir *anahtar bölümü* seçen bir seçim deyimidir.</span><span class="sxs-lookup"><span data-stu-id="86688-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="86688-104">Tek bir ifade üç veya daha fazla koşula göre test edildiğinde, `switch` deyimi genellikle [If-Else](if-else.md) yapısına alternatif olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86688-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="86688-105">Örneğin, aşağıdaki `switch` ifade, `Color` türünde bir değişkenin üç değerden birine sahip olup olmadığını belirler:</span><span class="sxs-lookup"><span data-stu-id="86688-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="86688-106">Bir `if`-`else` yapısını kullanan aşağıdaki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="86688-106">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="86688-107">Match ifadesi</span><span class="sxs-lookup"><span data-stu-id="86688-107">The match expression</span></span>

<span data-ttu-id="86688-108">Match ifadesi `case` etiketlerindeki desenlerle eşleşecek değeri sağlar.</span><span class="sxs-lookup"><span data-stu-id="86688-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="86688-109">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="86688-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="86688-110">C# 6 ve önceki sürümlerde, Match ifadesi aşağıdaki türlerde bir değer döndüren bir ifade olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="86688-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="86688-111">bir [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="86688-111">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="86688-112">bir [dize](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="86688-112">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="86688-113">bir [bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="86688-113">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="86688-114">`int` veya `long`gibi bir [integral](../builtin-types/integral-numeric-types.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="86688-114">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="86688-115">bir [sabit listesi](../builtin-types/enum.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="86688-115">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="86688-116">7,0 ile C# başlayarak, Match ifadesi null olmayan herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="86688-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="86688-117">Anahtar bölümü</span><span class="sxs-lookup"><span data-stu-id="86688-117">The switch section</span></span>

<span data-ttu-id="86688-118">`switch` bir ifade bir veya daha fazla anahtar bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="86688-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="86688-119">Her anahtar bölümü bir veya daha fazla *durum etiketi* (bir Case veya default etiketi) ve ardından bir veya daha fazla deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="86688-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="86688-120">`switch` deyiminiz, herhangi bir switch bölümüne yerleştirilmiş en çok bir varsayılan etiket içerebilir.</span><span class="sxs-lookup"><span data-stu-id="86688-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="86688-121">Aşağıdaki örnek, her biri iki deyim içeren üç anahtar bölümü olan basit bir `switch` deyimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="86688-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="86688-122">İkinci anahtar bölümü `case 2:` ve `case 3:` etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="86688-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="86688-123">`switch` bir ifade herhangi bir sayıda anahtar bölümü içerebilir ve aşağıdaki örnekte gösterildiği gibi her bölümde bir veya daha fazla Case etiketi olabilir.</span><span class="sxs-lookup"><span data-stu-id="86688-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="86688-124">Ancak, iki durum etiketi de aynı ifadeyi içeremez.</span><span class="sxs-lookup"><span data-stu-id="86688-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="86688-125">Switch deyimindeki yalnızca bir switch bölümü yürütülür.</span><span class="sxs-lookup"><span data-stu-id="86688-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="86688-126">C#yürütmenin bir geçiş bölümünden bir sonrakine devam etmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="86688-126">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="86688-127">Bu nedenle, aşağıdaki kod bir derleyici hatası oluşturuyor, CS0163: "Denetim bir case etiketinden (\<Case Label >) başka bir şekilde geçemez."</span><span class="sxs-lookup"><span data-stu-id="86688-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="86688-128">Bu gereksinim, genellikle bir [Break](break.md), [goto](goto.md)veya [Return](return.md) ifadesiyle Switch bölümünden açıkça çıkarken karşılanır.</span><span class="sxs-lookup"><span data-stu-id="86688-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="86688-129">Ancak, program denetiminin `default` Switch bölümüne dönememesini sağladığından aşağıdaki kod da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="86688-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="86688-130">Eşleştirme ifadesiyle eşleşen bir Case etiketi ile Switch bölümündeki deyim listesinin yürütülmesi ilk deyimle başlar ve genellikle bir `break`, `goto case`, `goto label`, `return`veya `throw`gibi bir sıçrama deyimine ulaşılana kadar deyim listesini ilerler.</span><span class="sxs-lookup"><span data-stu-id="86688-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="86688-131">Bu noktada denetim `switch` deyimin dışına veya başka bir Case etiketine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="86688-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="86688-132">`goto` bir deyimin kullanılması, denetimin bir sabit etikete aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86688-132">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="86688-133">Bu kısıtlama gereklidir, çünkü denetimi sabit olmayan bir etikete aktarmaya çalışmak, denetimi kodda istenmeyen bir konuma aktarmak veya sonsuz bir döngü oluşturmak gibi istenmeyen yan etkilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="86688-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="86688-134">Case etiketleri</span><span class="sxs-lookup"><span data-stu-id="86688-134">Case labels</span></span>

<span data-ttu-id="86688-135">Her Case etiketi, Match ifadesiyle Karşılaştırılacak bir model belirtir (önceki örneklerde `caseSwitch` değişkeni).</span><span class="sxs-lookup"><span data-stu-id="86688-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="86688-136">Eşleşiyorsa denetim, **ilk** eşleşen Case etiketini içeren Switch bölümüne aktarılır.</span><span class="sxs-lookup"><span data-stu-id="86688-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="86688-137">Hiçbir Case etiket deseninin eşleşme ifadesiyle eşleşmesi halinde, denetim varsa `default` Case etiketiyle birlikte bölümüne aktarılır.</span><span class="sxs-lookup"><span data-stu-id="86688-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="86688-138">`default` bir durum yoksa, herhangi bir anahtar bölümünde hiçbir deyim yürütülmez ve denetim `switch` deyimi dışında aktarılır.</span><span class="sxs-lookup"><span data-stu-id="86688-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="86688-139">`switch` deyimleri ve model eşleştirme hakkında daha fazla bilgi için, [`switch` deyimiyle eşleşen düzende eşleşme](#pattern) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="86688-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="86688-140">C# 6 yalnızca sabit bir stili desteklediğinden ve sabit değerlerin yinelenmesinde izin vermediğinden, Case etiketleri birbirini dışlayan değerleri tanımlar ve yalnızca bir desenler eşleştirme ifadesiyle eşleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="86688-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="86688-141">Sonuç olarak, `case` deyimlerinin göründüğü sıra önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="86688-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="86688-142">Ancak C# 7,0 ' de, diğer desenler desteklendiğinden, büyük/küçük harf etiketlerinin birbirini dışlayan değerler tanımlamamalıdır ve birden çok desen eşleştirme ifadesiyle eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="86688-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="86688-143">Yalnızca eşleşen düzeni içeren ilk anahtar bölümündeki deyimler yürütüldüğü için `case` deyimlerinin göründüğü sıra artık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="86688-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="86688-144">Case C# deyimi veya deyimleri önceki deyimlerin alt kümelerine eşit olan bir switch bölümü algılarsa, "switch case zaten önceki bir durum tarafından işlenmiştir." bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86688-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="86688-145">Aşağıdaki örnek, birbirini dışlayan farklı desenler kullanan bir `switch` ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="86688-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="86688-146">`case 0:` Switch bölümünü `switch` deyimindeki ilk bölüm olmayacak şekilde taşırsanız, C# değeri sıfır olan bir tamsayı, `case int val` ifadesiyle tanımlanan bir alt küme olan tüm tamsayıların bir alt kümesi olan bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86688-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="86688-147">Bu sorunu düzeltebilir ve iki şekilde derleyici uyarısını ortadan kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86688-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="86688-148">Anahtar bölümlerinin sırasını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="86688-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="86688-149">`case` etiketinde bir [WHERE yan tümcesi](#when) kullanarak.</span><span class="sxs-lookup"><span data-stu-id="86688-149">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="86688-150">`default` durumu</span><span class="sxs-lookup"><span data-stu-id="86688-150">The `default` case</span></span>

<span data-ttu-id="86688-151">`default` Case, Match ifadesi başka bir `case` etiketiyle eşleşmezse yürütülecek Switch bölümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="86688-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="86688-152">`default` bir durum yoksa ve eşleştirme ifadesi başka bir `case` etiketiyle eşleşmezse, program akışı `switch` ifadesiyle geçer.</span><span class="sxs-lookup"><span data-stu-id="86688-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="86688-153">`default` durum, `switch` deyimindeki herhangi bir sırada görünebilir.</span><span class="sxs-lookup"><span data-stu-id="86688-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="86688-154">Kaynak kodundaki sıralarından bağımsız olarak, tüm `case` etiketleri değerlendirildikten sonra her zaman son değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="86688-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="86688-155">`switch` ifadesiyle <a name="pattern" /> desenli eşleme</span><span class="sxs-lookup"><span data-stu-id="86688-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="86688-156">Her `case` deyimi, eşleşme ifadesiyle eşleşiyorsa, kapsayan anahtar bölümünün yürütülmesine neden olan bir model tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86688-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="86688-157">Tüm sürümleri sabit C# düzende desteklenir.</span><span class="sxs-lookup"><span data-stu-id="86688-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="86688-158">Kalan desenler C# 7,0 tarihinden itibaren desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="86688-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="86688-159">Sabit model</span><span class="sxs-lookup"><span data-stu-id="86688-159">Constant pattern</span></span>

<span data-ttu-id="86688-160">Sabit model, eşleşme ifadesinin belirtilen bir sabit değere eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="86688-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="86688-161">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="86688-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="86688-162">Burada *Constant* , test edilecek değerdir.</span><span class="sxs-lookup"><span data-stu-id="86688-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="86688-163">*sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="86688-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="86688-164">Bir [bool](../builtin-types/bool.md) sabit değeri: `true` ya da `false`.</span><span class="sxs-lookup"><span data-stu-id="86688-164">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="86688-165">`int`, `long`veya `byte`gibi herhangi bir [integral](../builtin-types/integral-numeric-types.md) sabiti.</span><span class="sxs-lookup"><span data-stu-id="86688-165">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="86688-166">Belirtilen bir `const` değişkeninin adı.</span><span class="sxs-lookup"><span data-stu-id="86688-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="86688-167">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="86688-167">An enumeration constant.</span></span>
- <span data-ttu-id="86688-168">Bir [char](../builtin-types/char.md) sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="86688-168">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="86688-169">[Dize](../builtin-types/reference-types.md) sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="86688-169">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="86688-170">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="86688-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="86688-171">*Expr* ve *Constant* integral türse, C# eşitlik işleci ifadenin `true` (yani `expr == constant`) döndürüp döndürmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="86688-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="86688-172">Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.</span><span class="sxs-lookup"><span data-stu-id="86688-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="86688-173">Aşağıdaki örnek, belirli bir tarihin hafta sonu, çalışma haftasının ilk günü mi, çalışma haftasının son günü mi yoksa çalışma haftasının ortasında mi olduğunu anlamak için sabit bir düzende kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86688-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="86688-174">Geçerli günün <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> özelliğini <xref:System.DayOfWeek> numaralandırmanın üyelerine göre değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="86688-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="86688-175">Aşağıdaki örnek, bir otomatik kahve makinesine benzetim yapan bir konsol uygulamasında kullanıcı girişini işlemek için sabit bir model kullanır.</span><span class="sxs-lookup"><span data-stu-id="86688-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="86688-176">Tür stili</span><span class="sxs-lookup"><span data-stu-id="86688-176">Type pattern</span></span>

<span data-ttu-id="86688-177">Tür stili, kısa tür değerlendirmesi ve dönüştürmeyi mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="86688-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="86688-178">Model eşleştirmeyi gerçekleştirmek için `switch` ifadesiyle birlikte kullanıldığında, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülmeyeceğini ve olup olmadığını test eder.</span><span class="sxs-lookup"><span data-stu-id="86688-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="86688-179">Sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="86688-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="86688-180">Burada *tür* , *Expr* 'nin sonucunun dönüştürülecek türün adı ve *varname* , eşleşme başarılı olursa *ifadenin* sonucunun dönüştürüldüğü nesnedir.</span><span class="sxs-lookup"><span data-stu-id="86688-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="86688-181">*İfadenin* derleme zamanı türü, 7,1 ile C# başlayan genel bir tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="86688-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="86688-182">Aşağıdakilerden biri doğruysa `case` ifadesi `true`:</span><span class="sxs-lookup"><span data-stu-id="86688-182">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="86688-183">*Expr* , *türü*ile aynı türde bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="86688-183">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="86688-184">*Expr* *türünden*türetilen bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="86688-184">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="86688-185">Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="86688-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="86688-186">*ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır.</span><span class="sxs-lookup"><span data-stu-id="86688-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="86688-187">Bir değişkenin *derleme zamanı türü* , tür bildiriminde tanımlanan değişkenin türüdür.</span><span class="sxs-lookup"><span data-stu-id="86688-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="86688-188">Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.</span><span class="sxs-lookup"><span data-stu-id="86688-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="86688-189">*Expr* , *tür* arabirimini uygulayan bir türün örneğidir.</span><span class="sxs-lookup"><span data-stu-id="86688-189">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="86688-190">Case ifadesi true ise, *varname* kesinlikle atanır ve yalnızca switch bölümü içinde yerel kapsama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="86688-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="86688-191">`null` bir türle eşleşmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="86688-191">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="86688-192">Bir `null`eşleştirmek için aşağıdaki `case` etiketini kullanın:</span><span class="sxs-lookup"><span data-stu-id="86688-192">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="86688-193">Aşağıdaki örnek, çeşitli türlerdeki koleksiyon türleri hakkında bilgi sağlamak için tür modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="86688-193">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="86688-194">`object`yerine, aşağıdaki kodda gösterildiği gibi koleksiyonun türünü tür parametresi olarak kullanarak genel bir yöntem yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86688-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="86688-195">Genel sürüm, ilk örnekten iki şekilde farklıdır.</span><span class="sxs-lookup"><span data-stu-id="86688-195">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="86688-196">İlk olarak `null` örneğini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="86688-196">First, you can't use the `null` case.</span></span> <span data-ttu-id="86688-197">Derleyici herhangi bir rastgele tür `T` `object`dışında herhangi bir türe dönüştüremediğinden herhangi bir sabit durumu kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="86688-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="86688-198">`default` durumu artık null olmayan bir `object`sınar.</span><span class="sxs-lookup"><span data-stu-id="86688-198">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="86688-199">Diğer bir deyişle, `default` durum testleri yalnızca `null`için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="86688-199">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="86688-200">Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="86688-200">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="86688-201">Tür deseninin kullanımı, bir dönüştürmenin sonucunun `null` olup olmadığını test etme veya yinelenen yayınlar gerçekleştirme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.</span><span class="sxs-lookup"><span data-stu-id="86688-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="86688-202">`case` deyimi ve `when` yan tümcesini <a name="when" /></span><span class="sxs-lookup"><span data-stu-id="86688-202"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="86688-203">7,0 ' C# den itibaren, Case deyimlerinin birbirini dışlanması gerektiğinden, Case ifadesinin true olarak değerlendirilmesi için karşılanması gereken ek bir koşul belirtmek üzere bir `when` yan tümcesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86688-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="86688-204">`when` yan tümcesi, Boolean değer döndüren herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="86688-204">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="86688-205">Aşağıdaki örnek, bir temel `Shape` sınıfını, `Shape`türetilen bir `Rectangle` sınıfını ve `Rectangle`türetilen bir `Square` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86688-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="86688-206">`ShowShapeInfo`, `Square` bir nesne olarak örneği oluşturulmasa bile, eşit uzunlukta ve genişliklerin `Square` olarak atanmış bir `Rectangle` nesnesine davrandığından emin olmak için `when` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="86688-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="86688-207">Yöntemi, `null` bir nesne veya alanı sıfır olan bir şekil hakkında bilgi görüntülemeyi denemez.</span><span class="sxs-lookup"><span data-stu-id="86688-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="86688-208">Örnekteki bir `Shape` nesnesinin `null` yürütülüp yürütülmediğini test girişiminde bulunan `when` yan tümcesinin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="86688-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="86688-209">`null` için test edilecek doğru tür deseninin `case null:`.</span><span class="sxs-lookup"><span data-stu-id="86688-209">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="86688-210">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="86688-210">C# language specification</span></span>

<span data-ttu-id="86688-211">Daha fazla bilgi için, [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Switch ifadesine](~/_csharplang/spec/statements.md#the-switch-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="86688-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="86688-212">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="86688-212">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="86688-213">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86688-213">See also</span></span>

- [<span data-ttu-id="86688-214">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="86688-214">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="86688-215">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86688-215">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="86688-216">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="86688-216">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="86688-217">if-else</span><span class="sxs-lookup"><span data-stu-id="86688-217">if-else</span></span>](if-else.md)
- [<span data-ttu-id="86688-218">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="86688-218">Pattern Matching</span></span>](../../pattern-matching.md)

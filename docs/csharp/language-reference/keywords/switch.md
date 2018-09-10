---
title: C# switch deyimi
ms.date: 08/14/2018
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
ms.openlocfilehash: 08b63d67b6175d18bee1317cc8908d876fbb4039
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252096"
---
# <a name="switch-c-reference"></a><span data-ttu-id="8ace6-102">geçiş (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8ace6-102">switch (C# reference)</span></span>

<span data-ttu-id="8ace6-103">`switch` tek bir seçtiği bir seçim deyimi *geçiş bölümüne* bir desen eşleştirme ile temel adaylar listesinden yürütülecek *eşleşen ifade*.</span><span class="sxs-lookup"><span data-stu-id="8ace6-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="8ace6-104">`switch` Deyimi bir alternatifi olarak kullanılan genellikle bir [if-else](if-else.md) tek bir ifade, üç veya daha fazla koşul karşı test edildiyse oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8ace6-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="8ace6-105">Örneğin, aşağıdaki `switch` ifadesi bir değişken türü olup olmadığını belirler `Color` üç değerden birine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8ace6-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="8ace6-106">Kullanan aşağıdaki örneğe eşdeğerdir bir `if` - `else` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8ace6-106">It is equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="8ace6-107">Eşleştirme ifadesi</span><span class="sxs-lookup"><span data-stu-id="8ace6-107">The match expression</span></span>

<span data-ttu-id="8ace6-108">Eşleşme ifade desenlerinde eşleştirilecek değer sağlar `case` etiketler.</span><span class="sxs-lookup"><span data-stu-id="8ace6-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="8ace6-109">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8ace6-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="8ace6-110">C# 6'da eşleşme ifadesi değer türlerinden birini döndüren bir ifade olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8ace6-110">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="8ace6-111">bir [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="8ace6-111">a [char](char.md).</span></span>
- <span data-ttu-id="8ace6-112">bir [dize](string.md).</span><span class="sxs-lookup"><span data-stu-id="8ace6-112">a [string](string.md).</span></span>
- <span data-ttu-id="8ace6-113">bir [bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="8ace6-113">a [bool](bool.md).</span></span>
- <span data-ttu-id="8ace6-114">bir tamsayı değeri olan gibi bir [int](int.md) veya [uzun](long.md).</span><span class="sxs-lookup"><span data-stu-id="8ace6-114">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="8ace6-115">bir [enum](enum.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="8ace6-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="8ace6-116">C# 7.0 ile başlayarak, eşleştirme ifadesi null olmayan herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="8ace6-117">Anahtar bölümü</span><span class="sxs-lookup"><span data-stu-id="8ace6-117">The switch section</span></span>

<span data-ttu-id="8ace6-118">A `switch` deyimi bir veya daha fazla anahtar bölüm içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="8ace6-119">Her anahtar bölümü bir veya daha fazla içeren *case etiketleri* (bir case veya default etiketi) ve ardından bir veya daha fazla deyim tarafından.</span><span class="sxs-lookup"><span data-stu-id="8ace6-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="8ace6-120">`switch` Deyimi herhangi bir anahtar bölümü yerleştirilen en fazla bir varsayılan etiket içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="8ace6-121">Aşağıdaki örnek, basit bir gösterir `switch` üç anahtar bölümü, her iki deyim içeren olan ifade.</span><span class="sxs-lookup"><span data-stu-id="8ace6-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="8ace6-122">İkinci bölüm anahtarını içeren `case 2:` ve `case 3:` etiketler.</span><span class="sxs-lookup"><span data-stu-id="8ace6-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="8ace6-123">A `switch` deyimi anahtar bölümlerinin sayısını içerir ve her bölüm aşağıdaki örnekte gösterildiği gibi bir veya daha fazla durum etiketi olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="8ace6-124">Ancak, hiçbir iki durum etiketi aynı ifadesi içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="8ace6-125">Switch deyimi içinde yalnızca bir anahtar bölümü yürütür.</span><span class="sxs-lookup"><span data-stu-id="8ace6-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="8ace6-126">C# bir geçiş bölümünden diğerine devam etmek için yürütmeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="8ace6-126">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="8ace6-127">Bu nedenle, aşağıdaki kod bir Derleyici Hatası CS0163 oluşturur: "denetimi olamaz atlayabilir bir case etiketinden (<case label>) diğerine."</span><span class="sxs-lookup"><span data-stu-id="8ace6-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>

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

<span data-ttu-id="8ace6-128">Bu gereksinim, genellikle açıkça kullanarak switch bölümüne çıkarak karşılanır bir [sonu](break.md), [goto](goto.md), veya [dönüş](return.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="8ace6-129">Program denetimi için geçemez sağlar ancak, aşağıdaki kod Ayrıca, geçersiz çünkü `default` bölümüne geçin.</span><span class="sxs-lookup"><span data-stu-id="8ace6-129">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="8ace6-130">Eşleştirme ifadesi ile eşleşen bir durum etiketi ile anahtar bölümdeki ifade listesinin yürütülmesi ilk deyimden başlar ve deyim listesi boyunca genellikle bir atlama deyimine ulaşılıncaya kadar devam eder bir `break`, `goto case`, `goto label`, `return`, veya `throw`, ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="8ace6-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="8ace6-131">Bu noktada, denetimi dışında aktarılan `switch` deyimi veya başka bir case etiketi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="8ace6-132">A `goto` deyimi kullanılırsa, gerekir aktarım denetimi için sabit bir etiket.</span><span class="sxs-lookup"><span data-stu-id="8ace6-132">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="8ace6-133">Sabit olmayan etiketine denetim aktarmaya çalışırken istenmeyen yan etkileri, bu tür istenmeyen bir kod konumuna denetimi aktarma veya sonsuz bir döngüye oluşturma olabileceği için bu kısıtlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="8ace6-134">Durum etiketi</span><span class="sxs-lookup"><span data-stu-id="8ace6-134">Case labels</span></span>

<span data-ttu-id="8ace6-135">Her durum etiketi eşleşen ifade karşılaştırmak için bir desen belirtir ( `caseSwitch` önceki örneklerde değişken).</span><span class="sxs-lookup"><span data-stu-id="8ace6-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="8ace6-136">Eşleşiyorlarsa denetimi içeren anahtar bölüme aktarılır **ilk** eşleşen case etiketi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="8ace6-137">Hiçbir durum etiketi desen eşleştirme ifadesi eşleşirse denetimi ile bölümüne aktarılır `default` varsa durum etiketi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="8ace6-138">Yoksa hiçbir `default` çalışması, her anahtar bölümü yok deyimlerinde yürütülür ve denetimin dışına aktarılır `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-138">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="8ace6-139">Hakkında bilgi için `switch` deyimi ve desen eşleştirme, [ile desen eşleştirme `switch` deyimi](#pattern) bölümü.</span><span class="sxs-lookup"><span data-stu-id="8ace6-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="8ace6-140">C# 6 yalnızca sabit desen destekler ve sabit değerleri tekrarını izin vermez çünkü durum etiketi birbirini dışlayan değerleri tanımlayın ve yalnızca bir desen eşleştirme ifadesi eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-140">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="8ace6-141">Sonuç olarak, bir sırayı `case` deyimlerinizin önemli olduğu.</span><span class="sxs-lookup"><span data-stu-id="8ace6-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="8ace6-142">C# 7.0, ancak diğer desenleri desteklendiğinden, case etiketleri birbirini dışlayan değerleri tanımlamanız gerekir değil ve eşleştirme ifadesi birden çok desen eşleştiğinde.</span><span class="sxs-lookup"><span data-stu-id="8ace6-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="8ace6-143">Yalnızca ilk eşleşen desen içeren anahtar bölümü deyimlerinde yürütülür çünkü sırayı `case` deyimlerinizin'ın, artık önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-143">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="8ace6-144">C#, case deyimi veya deyimler eşdeğerdir veya önceki deyimlerin kümeleridir switch bölümüne algılarsa, "anahtar durumu önceki bir case tarafından zaten işlendi." bir derleyici hatası, CS8120, oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8ace6-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="8ace6-145">Aşağıdaki örnekte bir `switch` olmayan-birbirini dışlayan desenleri çeşitli kullanan deyimi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="8ace6-146">Taşırsanız `case 0:` artık Birinci bölümde olması bölüm geçiş `switch` deyimi, C#, tanımlanan desenle olan bir alt tüm tamsayıların değeri sıfır olan bir tamsayı olduğu için bir derleyici hatası oluşturur tarafından `case int val` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-146">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="8ace6-147">Bu sorunu gidermek ve iki yoldan biriyle derleyici uyarısı ortadan kaldırır:</span><span class="sxs-lookup"><span data-stu-id="8ace6-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="8ace6-148">Anahtar bölümlerin sırası değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="8ace6-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="8ace6-149">Kullanarak bir < /a adı = "zaman" > zaman yan tümcesi</a> içinde `case` etiketi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-149">By using a </a name="when">when clause</a> in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="8ace6-150">`default` Çalışması</span><span class="sxs-lookup"><span data-stu-id="8ace6-150">The `default` case</span></span>

<span data-ttu-id="8ace6-151">`default` Çalışması belirtir eşleştirme ifadesi diğer eşleşmiyorsa yürütmek için anahtar bölümü `case` etiketi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-151">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="8ace6-152">Varsa bir `default` durumu mevcut değil ve diğer eşleştirme ifadesi eşleşmeyen `case` program akışı etiketi geçmez `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-152">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="8ace6-153">`default` Çalışması herhangi bir sırada görünebilir `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="8ace6-154">Kaynak kodunda kendi sırasını ne olursa olsun, her zaman son olarak, tüm değerlendirilmeden `case` etiketleri değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-154">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="8ace6-155"><a name="pattern" /> İle desen eşleştirme `switch` deyimi</span><span class="sxs-lookup"><span data-stu-id="8ace6-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="8ace6-156">Her `case` eşleşme ifadesi eşleşirse, yürütülecek içeren anahtar bölümü neden olan bir desen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8ace6-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="8ace6-157">Sabit desen C# ' in tüm sürümleri destekler.</span><span class="sxs-lookup"><span data-stu-id="8ace6-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="8ace6-158">Kalan desenleri, C# 7. 0'den itibaren desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="8ace6-159">Sabit desen</span><span class="sxs-lookup"><span data-stu-id="8ace6-159">Constant pattern</span></span>

<span data-ttu-id="8ace6-160">Sabit desen eşleştirme ifadesi belirtilen bir sabit eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="8ace6-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="8ace6-161">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8ace6-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="8ace6-162">Burada *sabit* sınamak için değer.</span><span class="sxs-lookup"><span data-stu-id="8ace6-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="8ace6-163">*Sabit* aşağıdaki sabit ifadeler biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="8ace6-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="8ace6-164">A [bool](bool.md) değişmez değer, ya da `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="8ace6-164">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="8ace6-165">Herhangi bir integral sabit gibi bir [int](int.md), [uzun](long.md), veya bir [bayt](byte.md).</span><span class="sxs-lookup"><span data-stu-id="8ace6-165">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span>
- <span data-ttu-id="8ace6-166">Bildirilen bir adı `const` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="8ace6-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="8ace6-167">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="8ace6-167">An enumeration constant.</span></span>
- <span data-ttu-id="8ace6-168">A [char](char.md) değişmez.</span><span class="sxs-lookup"><span data-stu-id="8ace6-168">A [char](char.md) literal.</span></span>
- <span data-ttu-id="8ace6-169">A [dize](string.md) değişmez.</span><span class="sxs-lookup"><span data-stu-id="8ace6-169">A [string](string.md) literal.</span></span>

<span data-ttu-id="8ace6-170">Sabit ifade gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="8ace6-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="8ace6-171">Varsa *expr* ve *sabit* integral türleri, C# eşitlik işlecini ifade döndürüp döndürmediğini belirler `true` (olup, diğer bir deyişle, `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="8ace6-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="8ace6-172">Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="8ace6-173">Aşağıdaki örnek, belirli bir tarihin hafta, çalışma haftası ya da ikinci iş haftanın son gününü iş haftanın ilk günü olup olmadığını belirlemek için sabit bir desen kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ace6-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="8ace6-174">Bu hesaplar <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> üyelerinin göre geçerli günün özelliği <xref:System.DayOfWeek> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="8ace6-175">Aşağıdaki örnek, kullanıcı girişini otomatik kahve makine taklit eden bir konsol uygulamasında işlemek için sabit desen kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ace6-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="8ace6-176">Tür deseni</span><span class="sxs-lookup"><span data-stu-id="8ace6-176">Type pattern</span></span>

<span data-ttu-id="8ace6-177">Tür düzeni kısa türü değerlendirme ve dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ace6-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="8ace6-178">İle kullanıldığında `switch` desen eşleştirme, gerçekleştirmek için deyimi, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve olabilir, bu türden bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="8ace6-179">Kendi sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8ace6-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="8ace6-180">Burada *türü* türün adı sonucunu *expr* Boolean'a dönüştürülecek ve *varname* hangi nesne sonucu *expr*eşleşmenin başarılı olursa dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8ace6-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span>

<span data-ttu-id="8ace6-181">`case` İfade `true` herhangi biri doğru ise:</span><span class="sxs-lookup"><span data-stu-id="8ace6-181">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="8ace6-182">*Expr* örneği aynı türde olan *türü*.</span><span class="sxs-lookup"><span data-stu-id="8ace6-182">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="8ace6-183">*Expr* türetilen türün bir örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="8ace6-183">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="8ace6-184">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="8ace6-184">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="8ace6-185">*Expr* temel bir sınıfı olan bir derleme zamanı türü sahip *türü*, ve *expr* sahip olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*.</span><span class="sxs-lookup"><span data-stu-id="8ace6-185">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="8ace6-186">*Derleme zamanı tür* değişkeninin değişkenin türü bildiriminde tanımlanan türüdür.</span><span class="sxs-lookup"><span data-stu-id="8ace6-186">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="8ace6-187">*Çalışma zamanı türü* bir değişken, bu değişkene atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="8ace6-187">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="8ace6-188">*Expr* uygulayan bir tür örneğidir *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8ace6-188">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="8ace6-189">Case ifadesi true ise *varname* kesinlikle atanır ve yalnızca anahtarı bölüm içinde yerel kapsama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-189">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="8ace6-190">Unutmayın `null` bir türle eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="8ace6-190">Note that `null` does not match a type.</span></span> <span data-ttu-id="8ace6-191">Eşleştirilecek bir `null`, kullanarak aşağıdaki `case` etiketi:</span><span class="sxs-lookup"><span data-stu-id="8ace6-191">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="8ace6-192">Aşağıdaki örnek, çeşitli koleksiyon türleri hakkında bilgi sağlamak için tür deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ace6-192">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="8ace6-193">Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-193">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="8ace6-194">Kullanım türü desen eşleştirme bir dönüştürmenin sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha kompakt ve okunabilir bir kod oluşturur bir `null` veya yinelenen atamalar gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="8ace6-194">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="8ace6-195"><a name="when" /> `case` Deyimi ve `when` yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="8ace6-195"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="8ace6-196">Ekleyebileceğiniz Case deyimleri birbirini dışlayan olması gerekmez çünkü C# 7.0 ile başlayarak, bir `when` ek bir koşulu belirtmek için yan tümcesi memnun, doğru olarak değerlendirilebilmesi case deyimi için.</span><span class="sxs-lookup"><span data-stu-id="8ace6-196">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="8ace6-197">`when` Yan tümcesi, bir Boole değeri döndüren herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ace6-197">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="8ace6-198">Aşağıdaki örnek, bir taban tanımlar `Shape` sınıfı, bir `Rectangle` türetilen sınıf `Shape`ve `Square` türetilen sınıf `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="8ace6-198">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="8ace6-199">Kullandığı `when` emin olmak için yan tümcesi `ShowShapeInfo` değerlendirir bir `Rectangle` eşit uzunlukta ve genişlikleri olarak atanmış olan bir nesne bir `Square` olarak oluşturulmadı olsa bile bir `Square` nesne.</span><span class="sxs-lookup"><span data-stu-id="8ace6-199">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="8ace6-200">Yöntem bilgileri görüntülemek denemez herhangi bir nesne hakkında `null` veya bir şekil, alan sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="8ace6-200">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="8ace6-201">Unutmayın `when` yan tümcesinde test dener örnek olup olmadığını bir `Shape` nesnedir `null` yürütme değil.</span><span class="sxs-lookup"><span data-stu-id="8ace6-201">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="8ace6-202">Test etmek için doğru türde deseni bir `null` olduğu `case null:`.</span><span class="sxs-lookup"><span data-stu-id="8ace6-202">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8ace6-203">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8ace6-203">C# language specification</span></span>

<span data-ttu-id="8ace6-204">Daha fazla bilgi için [switch deyimi](/dotnet/csharp/language-reference/language-specification/statements#the-switch-statement) içinde [C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ace6-204">For more information, see [The switch statement](/dotnet/csharp/language-reference/language-specification/statements#the-switch-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="8ace6-205">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="8ace6-205">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ace6-206">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ace6-206">See also</span></span>

- [<span data-ttu-id="8ace6-207">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8ace6-207">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8ace6-208">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8ace6-208">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8ace6-209">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8ace6-209">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8ace6-210">if-else</span><span class="sxs-lookup"><span data-stu-id="8ace6-210">if-else</span></span>](if-else.md)
- [<span data-ttu-id="8ace6-211">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="8ace6-211">Pattern Matching</span></span>](../../pattern-matching.md)
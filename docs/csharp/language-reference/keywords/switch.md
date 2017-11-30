---
title: "switch anahtar sözcüğü (C# Başvurusu)"
ms.date: 03/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1c345d0c6c935271600a386752e18c19a25cc389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="switch-c-reference"></a><span data-ttu-id="f5c38-102">switch (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f5c38-102">switch (C# Reference)</span></span>
<span data-ttu-id="f5c38-103">`switch`tek bir seçtiği seçimi açıklamadır *geçiş bölüm* bir desen eşleştirme ile temel adaylar listesinden yürütmek için *ifade ile eşleşen*.</span><span class="sxs-lookup"><span data-stu-id="f5c38-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span> 
  
 [!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

<span data-ttu-id="f5c38-104">`switch` Deyimi alternatif olarak kullanılan genellikle bir [if-else](if-else.md) tek bir ifade üç veya daha fazla koşul karşı test varsa oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5c38-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="f5c38-105">Örneğin, aşağıdaki `switch` ifadesi bir değişken türü olup olmadığını belirler `Color` üç değerden birini içeriyor:</span><span class="sxs-lookup"><span data-stu-id="f5c38-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span> 

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

<span data-ttu-id="f5c38-106">Kullanan aşağıdaki örneğe eşdeğer olan bir `if` - `else` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5c38-106">It is equivalent to the following example that uses an `if`-`else` construct.</span></span> 

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a><span data-ttu-id="f5c38-107">Eşleşme ifadesi</span><span class="sxs-lookup"><span data-stu-id="f5c38-107">The match expression</span></span>

<span data-ttu-id="f5c38-108">Eşleşme ifadesi düzenleri eşleştirilecek değer sağlar `case` etiketler.</span><span class="sxs-lookup"><span data-stu-id="f5c38-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="f5c38-109">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f5c38-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="f5c38-110">C# 6'da, aşağıdaki türlerde bir değer döndüren bir ifadeye eşleşme ifadesi olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="f5c38-110">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="f5c38-111">bir [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="f5c38-111">a [char](char.md).</span></span>
- <span data-ttu-id="f5c38-112">bir [dize](string.md).</span><span class="sxs-lookup"><span data-stu-id="f5c38-112">a [string](string.md).</span></span>
- <span data-ttu-id="f5c38-113">bir [bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="f5c38-113">a [bool](bool.md).</span></span> 
- <span data-ttu-id="f5c38-114">gibi bir integral değeri bir [int](int.md) veya [uzun](long.md).</span><span class="sxs-lookup"><span data-stu-id="f5c38-114">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="f5c38-115">bir [enum](enum.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="f5c38-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="f5c38-116">C# 7 ile başlayan, eşleşme ifadesi herhangi bir null olmayan ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-116">Starting with C# 7, the match expression can be any non-null expression.</span></span>
 
## <a name="the-switch-section"></a><span data-ttu-id="f5c38-117">Anahtar bölümü</span><span class="sxs-lookup"><span data-stu-id="f5c38-117">The switch section</span></span>
 
 <span data-ttu-id="f5c38-118">A `switch` deyimi bir veya daha fazla anahtar bölümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="f5c38-119">Bir veya daha fazla her anahtar bölüm içerir *durumda etiketler* bir veya daha fazla deyimleri tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="f5c38-119">Each switch section contains one or more *case labels* followed by one or more statements.</span></span> <span data-ttu-id="f5c38-120">Aşağıdaki örnekte basit bir `switch` üç anahtar bölümleri olan deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-120">The following example shows a simple `switch` statement that has three switch sections.</span></span> <span data-ttu-id="f5c38-121">Her anahtar bölümü gibi bir durum etiketi, sahip `case 1:`ve iki ifade.</span><span class="sxs-lookup"><span data-stu-id="f5c38-121">Each switch section has one case label, such as `case 1:`, and two statements.</span></span>
 
  <span data-ttu-id="f5c38-122">A `switch` deyimi herhangi bir sayıda anahtar bölümü içerebilir ve her bölüm aşağıdaki örnekte gösterildiği gibi durum etiketi, bir veya daha fazla olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-122">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="f5c38-123">Ancak, hiçbir iki durum etiketi aynı ifadesi içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-123">However, no two case labels may contain the same expression.</span></span>  

 [!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 <span data-ttu-id="f5c38-124">Switch deyimi yalnızca bir anahtar bölümünde yürütür.</span><span class="sxs-lookup"><span data-stu-id="f5c38-124">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="f5c38-125">C# bir anahtar bölümünden sonraki devam etmek için yürütmeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f5c38-125">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="f5c38-126">Bu nedenle, aşağıdaki kod bir Derleyici Hatası CS0163 oluşturur: "Denetim olamaz atlayabilir bir case etiketinden (<case label>) diğerine."</span><span class="sxs-lookup"><span data-stu-id="f5c38-126">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>  

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
<span data-ttu-id="f5c38-127">Bu gereksinim, genellikle açıkça kullanarak anahtar bölüm çıkılarak karşılanır bir [sonu](break.md), [goto](goto.md), veya [dönmek](return.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-127">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="f5c38-128">Program denetim için geçemez sağlar ancak, aşağıdaki kodu aynı zamanda, geçersiz çünkü `default` bölümüne geçin.</span><span class="sxs-lookup"><span data-stu-id="f5c38-128">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>
  
 [!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 <span data-ttu-id="f5c38-129">Eşleşme ifadeyle eşleşen bir servis talebi etiket anahtarı bölümle deyimi listesinde yürütülmesi ilk deyimi ile başlar ve genellikle bir atlama deyimi kadar deyimi eşlemeleri gibi devam eder bir `break`, `goto case`, `goto label`, `return`, veya `throw`, ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="f5c38-129">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="f5c38-130">Bu noktada, denetimi dışında aktarılır `switch` deyimi veya başka bir durum etiketi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-130">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="f5c38-131">A `goto` deyimi, kullanılırsa, gerekir aktarım denetimi için sabit bir etiket.</span><span class="sxs-lookup"><span data-stu-id="f5c38-131">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="f5c38-132">Bir sabit olmayan etiket denetimi aktarmaya çalışırken istenmeyen yan etkiler, bu tür denetim kodu istenmeyen bir konumda aktarılıyor veya sonsuz bir döngüde oluşturma olabileceği için bu kısıtlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-132">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="f5c38-133">Durum etiketi</span><span class="sxs-lookup"><span data-stu-id="f5c38-133">Case labels</span></span>

 <span data-ttu-id="f5c38-134">Servis talebi her etiket eşleşme ifadesi karşılaştırmak için bir desen belirtir ( `caseSwitch` önceki örneklerde değişken).</span><span class="sxs-lookup"><span data-stu-id="f5c38-134">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="f5c38-135">Eşleşirlerse, denetimi içeren anahtar bölümü aktarılır **ilk** eşleşen durum etiketi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-135">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="f5c38-136">Durum etiketi desen eşleştirme ifadesi eşleşirse, Denetim bölümle aktarılır `default` varsa durum etiketi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-136">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="f5c38-137">Varsa hiçbir `default` durumu, herhangi bir anahtar bölümü hiçbir deyimlerinde yürütülür ve denetim dışında aktarılır `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-137">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

 <span data-ttu-id="f5c38-138">Hakkında bilgi için `switch` deyimi ve desen eşleştirme, bkz: [ile desen eşleştirme `switch` deyimi](#pattern) bölümü.</span><span class="sxs-lookup"><span data-stu-id="f5c38-138">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

 <span data-ttu-id="f5c38-139">C# 6 yalnızca sabit düzeni destekler ve sabit değerleri yinelenmesinin izin verme olduğundan, birbirini dışlayan değerleri büyük küçük harf etiketleri tanımlamak ve yalnızca bir desen eşleştirme ifadesi eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5c38-139">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="f5c38-140">Sonuç olarak, hangi sırayla `case` deyimleri görünür olan önemli.</span><span class="sxs-lookup"><span data-stu-id="f5c38-140">As a result, the order in which `case` statements appear is unimportant.</span></span>

 <span data-ttu-id="f5c38-141">C# 7, ancak diğer desenleri desteklenmediğinden durum etiketi birbirini dışlayan değerleri tanımlayın olmayan ve birden çok desen eşleştirme ifadesi eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5c38-141">In C# 7, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="f5c38-142">Yalnızca ilk eşleştirme deseni içeren anahtar bölüm deyimlerinde çalıştırıldığı için hangi sırayla `case` deyimleri görünür önemlidir şimdi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-142">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="f5c38-143">C#, case deyimi deyimleri eşit olan veya önceki deyimleri kümeleridir anahtar bölüm algılarsa, "anahtar durumu önceki bir örneği tarafından zaten işlendi." bir derleyici hatası, CS8120, oluşturur</span><span class="sxs-lookup"><span data-stu-id="f5c38-143">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span> 

 <span data-ttu-id="f5c38-144">Aşağıdaki örnek gösterilmektedir bir `switch` olmayan-birbirini dışlayan desenleri çeşitli kullanan deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-144">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="f5c38-145">Taşırsanız `case 0:` böylece artık ilk bölümde değil bölüm geçiş `switch` deyimi, C# Derleyici Hatası değeri sıfır olmayan bir tamsayı tanımlanan örnekle olan bir alt tüm tamsayıların olduğundan oluşturur tarafından `case int val` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-145">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

 [!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

<span data-ttu-id="f5c38-146">Bu sorunu düzeltin ve iki yoldan biriyle derleyici uyarısı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="f5c38-146">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="f5c38-147">Anahtar bölümlerin sırasını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="f5c38-147">By changing the order of the switch sections.</span></span> 
 
- <span data-ttu-id="f5c38-148">Kullanarak bir < /a adı "zaman" = > zaman yan tümcesi</a> içinde `case` etiketi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-148">By using a </a name="when">when clause</a> in the `case` label.</span></span>
 
## <a name="the-default-case"></a><span data-ttu-id="f5c38-149">`default` Durumu</span><span class="sxs-lookup"><span data-stu-id="f5c38-149">The `default` case</span></span>

<span data-ttu-id="f5c38-150">`default` Durumda eşleşme ifadesi diğer eşleşmiyorsa yürütmek için anahtar bölüm belirtir `case` etiketi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-150">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="f5c38-151">Varsa bir `default` durumda mevcut değil ve eşleşme ifadesi diğer eşleşmiyor `case` program akışı etiketi, geçer `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-151">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="f5c38-152">`default` Durumda herhangi bir sırada görünebilir `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-152">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="f5c38-153">Kaynak kodu, sırasıyla bağımsız olarak, her zaman son olarak, tüm değerlendirilir `case` etiketleri değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-153">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="f5c38-154"><a name="pattern" />Deseni ile eşleşen `switch` deyimi</span><span class="sxs-lookup"><span data-stu-id="f5c38-154"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>
  
<span data-ttu-id="f5c38-155">Her `case` deyimi eşleşme ifadesi eşleşirse, yürütülecek içeren kendi anahtar bölüm neden olan bir desen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5c38-155">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="f5c38-156">C# ' in tüm sürümleri sabit düzenini destekler.</span><span class="sxs-lookup"><span data-stu-id="f5c38-156">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="f5c38-157">Kalan desenleri, C# 7'den başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-157">The remaining patterns are supported beginning with C# 7.</span></span> 
  
### <a name="constant-pattern"></a><span data-ttu-id="f5c38-158">Sabit düzeni</span><span class="sxs-lookup"><span data-stu-id="f5c38-158">Constant pattern</span></span> 

<span data-ttu-id="f5c38-159">Sabit desen eşleşmesi ifadesi belirtilen bir sabit eşit olup olmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="f5c38-159">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="f5c38-160">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f5c38-160">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="f5c38-161">Burada *sabit* sınamak için bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-161">where *constant* is the value to test for.</span></span> <span data-ttu-id="f5c38-162">*Sabit* aşağıdaki sabit ifadelerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="f5c38-162">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="f5c38-163">A [bool](bool.md) değişmez değer, ya da `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="f5c38-163">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="f5c38-164">Tüm integral gibi sabit bir [int](int.md), [uzun](long.md), veya bir [bayt](byte.md).</span><span class="sxs-lookup"><span data-stu-id="f5c38-164">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span> 
- <span data-ttu-id="f5c38-165">Bir bildirilen adını `const` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="f5c38-165">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="f5c38-166">Bir numaralandırma sabiti.</span><span class="sxs-lookup"><span data-stu-id="f5c38-166">An enumeration constant.</span></span>
- <span data-ttu-id="f5c38-167">A [char](char.md) değişmez.</span><span class="sxs-lookup"><span data-stu-id="f5c38-167">A [char](char.md) literal.</span></span>
- <span data-ttu-id="f5c38-168">A [dize](string.md) değişmez.</span><span class="sxs-lookup"><span data-stu-id="f5c38-168">A [string](string.md) literal.</span></span>

<span data-ttu-id="f5c38-169">Sabit ifade aşağıdaki gibi değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="f5c38-169">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="f5c38-170">Varsa *expr* ve *sabit* tam sayı türleri, C# eşitlik işleci ifade döndürüp döndürmediğini belirler `true` (diğer bir deyişle, olup olmadığını `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="f5c38-170">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="f5c38-171">Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-171">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="f5c38-172">Aşağıdaki örnek, belirli bir tarihin hafta sonu, haftanın, başında veya ortasında haftanın son gününü iş haftanın ilk günü olup olmadığını belirlemek için sabit desen kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5c38-172">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="f5c38-173">Bu hesaplar <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> özelliği üyeleri için geçerli günün <xref:System.DayOfWeek> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="f5c38-173">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span> 

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="f5c38-174">Aşağıdaki örnek, bir otomatik kahve makine taklit eden bir konsol uygulamasında kullanıcı girişini işlemek için sabit desen kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5c38-174">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>
  
 [!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a><span data-ttu-id="f5c38-175">Tür deseni</span><span class="sxs-lookup"><span data-stu-id="f5c38-175">Type pattern</span></span>

<span data-ttu-id="f5c38-176">Tür deseni kısa türü değerlendirme ve dönüştürme sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5c38-176">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="f5c38-177">İle kullanıldığında `switch` desen eşleştirme gerçekleştirmek için deyimi, bir ifade belirtilen türe dönüştürülüp dönüştürülemeyeceğini test eder ve olabiliyorsa, bu tür bir değişkene çevirir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-177">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="f5c38-178">Sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f5c38-178">Its syntax is:</span></span>

```csharp
   case type varname 
```
<span data-ttu-id="f5c38-179">Burada *türü* türün adı sonucu *expr* dönüştürülmekte olan ve *varname* hangi nesne sonucu *ifade*eşlemesi başarılı olursa dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f5c38-179">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> 

<span data-ttu-id="f5c38-180">`case` İfade `true` aşağıdakilerden biri doğruysa:</span><span class="sxs-lookup"><span data-stu-id="f5c38-180">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="f5c38-181">*Expr* aynı türde örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="f5c38-181">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="f5c38-182">*Expr* türeyen bir tür örneği *türü*.</span><span class="sxs-lookup"><span data-stu-id="f5c38-182">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="f5c38-183">Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.</span><span class="sxs-lookup"><span data-stu-id="f5c38-183">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="f5c38-184">*Expr* bir taban sınıf, derleme zamanı türüne sahip *türü*, ve *expr* olan bir çalışma zamanı türü *türü* veya türetilmiş *türü* .</span><span class="sxs-lookup"><span data-stu-id="f5c38-184">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="f5c38-185">*Derleme zamanı tür* bir değişken değişkenin türü bildiriminde tanımlandığı gibi türüdür.</span><span class="sxs-lookup"><span data-stu-id="f5c38-185">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="f5c38-186">*Çalışma zamanı tür* bir değişken bu değişkenine atanan örnek türüdür.</span><span class="sxs-lookup"><span data-stu-id="f5c38-186">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="f5c38-187">*Expr* uygulayan bir tür örneği *türü* arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-187">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="f5c38-188">Servis talebi ifade doğruysa *varname* kesinlikle atanır ve yalnızca anahtarı bölüm içinde yerel kapsama sahip.</span><span class="sxs-lookup"><span data-stu-id="f5c38-188">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="f5c38-189">Unutmayın `null` bir türle eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="f5c38-189">Note that `null` does not match a type.</span></span> <span data-ttu-id="f5c38-190">Eşleştirilecek bir `null`, aşağıdaki `case` etiketi:</span><span class="sxs-lookup"><span data-stu-id="f5c38-190">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```
 
<span data-ttu-id="f5c38-191">Aşağıdaki örnek türü desen çeşitli koleksiyon türleri hakkında bilgi sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5c38-191">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="f5c38-192">Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-192">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="f5c38-193">Bir dönüştürme sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha küçük, okunabilir kod türü desen eşleştirme kullanımını üreten bir `null` veya yinelenen atamaları gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="f5c38-193">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>  

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="f5c38-194">`case` Deyimi ve `when` yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f5c38-194">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="f5c38-195">Case deyimleri birbirini dışlayan olması gerekmez çünkü C# 7 ile başlayarak, kullanabilirsiniz eklemek bir `when` ek bir koşul belirtmek için yan tümcesi memnun, doğru olarak değerlendirilecek case deyimi için.</span><span class="sxs-lookup"><span data-stu-id="f5c38-195">Starting with C# 7, because case statements need not be mutually exclusive, you can use add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="f5c38-196">`when` Yan tümcesi bir Boole değeri döndürür herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c38-196">The `when` clause can be any expression that returns a Boolean value.</span></span> <span data-ttu-id="f5c38-197">Daha yaygın kullanımları birini `when` yan tümcesi anahtar bölüm bir eşleşme ifadesi değeri olduğunda yürütülmesini engellemek için kullanılan `null`.</span><span class="sxs-lookup"><span data-stu-id="f5c38-197">One of the more common uses for the `when` clause is used to prevent a switch section from executing when the value of a match expression is `null`.</span></span> 

 <span data-ttu-id="f5c38-198">Aşağıdaki örnek, bir taban tanımlar `Shape` sınıfı, bir `Rectangle` öğesinden türetilen sınıf `Shape`ve bir `Square` öğesinden türetilen sınıf `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="f5c38-198">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="f5c38-199">Kullandığı `when` emin olmak için yan tümcesi `ShowShapeInfo` değerlendirir bir `Rectangle` eşit uzunlukta ve genişliklerini olarak atanan nesne bir `Square` bile değiştirilmediğinden olarak örneği bir `Square` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f5c38-199">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if is has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="f5c38-200">Yöntem bilgileri görüntülemek denemez herhangi bir nesne hakkında `null` veya bir şekil, alan sıfırsa.</span><span class="sxs-lookup"><span data-stu-id="f5c38-200">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span> 

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
<span data-ttu-id="f5c38-201">Unutmayın `when` test girişiminde örnek yan tümcesinde olup bir `Shape` nesne `null` değil çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="f5c38-201">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="f5c38-202">İçin test etmek için doğru türde desen bir `null` olan `case null:`.</span><span class="sxs-lookup"><span data-stu-id="f5c38-202">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f5c38-203">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f5c38-203">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5c38-204">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5c38-204">See Also</span></span>  

 [<span data-ttu-id="f5c38-205">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f5c38-205">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="f5c38-206">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f5c38-206">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="f5c38-207">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f5c38-207">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="f5c38-208">if-else</span><span class="sxs-lookup"><span data-stu-id="f5c38-208">if-else</span></span>](if-else.md)  
 [<span data-ttu-id="f5c38-209">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="f5c38-209">Pattern Matching</span></span>](../../pattern-matching.md)  
 

 

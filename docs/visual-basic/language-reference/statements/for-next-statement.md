---
title: For...Next Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: cafd59482036a598814dcd4815fa67a791580045
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046307"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="16061-102">For...Next Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16061-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="16061-103">Bir deyim grubunu belirtilen sayıda yineler.</span><span class="sxs-lookup"><span data-stu-id="16061-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="16061-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16061-104">Syntax</span></span>

```
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="16061-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="16061-105">Parts</span></span>

|<span data-ttu-id="16061-106">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="16061-106">Part</span></span>|<span data-ttu-id="16061-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16061-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="16061-108">`For` İfadesinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="16061-108">Required in the `For` statement.</span></span> <span data-ttu-id="16061-109">Sayısal değişken.</span><span class="sxs-lookup"><span data-stu-id="16061-109">Numeric variable.</span></span> <span data-ttu-id="16061-110">Döngünün denetim değişkeni.</span><span class="sxs-lookup"><span data-stu-id="16061-110">The control variable for the loop.</span></span> <span data-ttu-id="16061-111">Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16061-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="16061-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="16061-112">Optional.</span></span> <span data-ttu-id="16061-113">Veri türü `counter`.</span><span class="sxs-lookup"><span data-stu-id="16061-113">Data type of `counter`.</span></span> <span data-ttu-id="16061-114">Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16061-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="16061-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="16061-115">Required.</span></span> <span data-ttu-id="16061-116">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="16061-116">Numeric expression.</span></span> <span data-ttu-id="16061-117">Başlangıç değeri `counter`.</span><span class="sxs-lookup"><span data-stu-id="16061-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="16061-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="16061-118">Required.</span></span> <span data-ttu-id="16061-119">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="16061-119">Numeric expression.</span></span> <span data-ttu-id="16061-120">Öğesinin `counter`son değeri.</span><span class="sxs-lookup"><span data-stu-id="16061-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="16061-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="16061-121">Optional.</span></span> <span data-ttu-id="16061-122">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="16061-122">Numeric expression.</span></span> <span data-ttu-id="16061-123">Döngü aracılığıyla her seferinde `counter` arttırılan miktar.</span><span class="sxs-lookup"><span data-stu-id="16061-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="16061-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="16061-124">Optional.</span></span> <span data-ttu-id="16061-125">`For` Ve`Next` arasındaki bir veya daha fazla deyim, belirtilen sayıda kez çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="16061-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="16061-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="16061-126">Optional.</span></span> <span data-ttu-id="16061-127">Denetimi sonraki döngü yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="16061-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="16061-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="16061-128">Optional.</span></span> <span data-ttu-id="16061-129">Denetimi `For` döngünün dışına aktarır.</span><span class="sxs-lookup"><span data-stu-id="16061-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="16061-130">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="16061-130">Required.</span></span> <span data-ttu-id="16061-131">`For` Döngünün tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="16061-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="16061-132">`To` Anahtar sözcüğü, bu bildirimde sayaç aralığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16061-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="16061-133">Bu anahtar sözcüğü Select... içinde de kullanabilirsiniz [. Case Bildirimi](../../../visual-basic/language-reference/statements/select-case-statement.md) ve dizi bildirimlerinde.</span><span class="sxs-lookup"><span data-stu-id="16061-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="16061-134">Dizi bildirimleri hakkında daha fazla bilgi için bkz. [Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="16061-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="16061-135">Basit örnekler</span><span class="sxs-lookup"><span data-stu-id="16061-135">Simple Examples</span></span>

<span data-ttu-id="16061-136">Şunu kullanıyorsunuz `For`... `Next` bir deyim kümesini bir dizi kez yinelemek istediğinizde yapı.</span><span class="sxs-lookup"><span data-stu-id="16061-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="16061-137">Aşağıdaki örnekte, `index` değişken 1 değeri ile başlar ve döngünün her yinelemeyle artırılır, bu `index` değer 5 ' e ulaştığında biter.</span><span class="sxs-lookup"><span data-stu-id="16061-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="16061-138">Aşağıdaki örnekte, `number` değişken 2 ' de başlar ve döngünün her yinelemesinde 0,25 tarafından azaltılır ve `number` değeri 0 ' dan sonra sona eriyor.</span><span class="sxs-lookup"><span data-stu-id="16061-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="16061-139">`Step` Öğesinin`-.25` bağımsız değişkeni, döngünün her yinelemede değeri 0,25 azaltır.</span><span class="sxs-lookup"><span data-stu-id="16061-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="16061-140">Bir [while... End while ekstresi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) veya [Do... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md) , döngüdeki deyimlerin kaç kez çalıştırılacağını önceden bilmiyorsanız iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="16061-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="16061-141">Ancak, döngüyü belirli sayıda kez çalıştırmayı beklediğinizi, a `For`... `Next` döngü daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="16061-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="16061-142">Döngüyü ilk kez girerken yineleme sayısını belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="16061-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="16061-143">İç içe geçme döngüleri</span><span class="sxs-lookup"><span data-stu-id="16061-143">Nesting Loops</span></span>

<span data-ttu-id="16061-144">Bir döngüyü diğerinin `For` içine yerleştirerek döngüleri iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16061-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="16061-145">Aşağıdaki örnek iç içe geçmiş `For`... `Next` farklı adım değerlerine sahip yapılar.</span><span class="sxs-lookup"><span data-stu-id="16061-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="16061-146">Dış döngü, döngünün her yinelemesi için bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="16061-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="16061-147">İç döngü, döngünün her yinelemesi için bir döngü sayacı değişkenini azaltır.</span><span class="sxs-lookup"><span data-stu-id="16061-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="16061-148">Döngüleri iç içe aktardığınızda her döngünün benzersiz `counter` bir değişkeni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16061-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="16061-149">Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16061-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="16061-150">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="16061-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="16061-151">İçin çık ve devam et</span><span class="sxs-lookup"><span data-stu-id="16061-151">Exit For and Continue For</span></span>

<span data-ttu-id="16061-152">Deyimden hemen `For`çıkar... `Exit For``Next`</span><span class="sxs-lookup"><span data-stu-id="16061-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="16061-153">öğesini Loop ve `Next` deyimden sonraki deyime aktarır.</span><span class="sxs-lookup"><span data-stu-id="16061-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="16061-154">`Continue For` İfade, denetimi döngünün bir sonraki yinelemesine hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="16061-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="16061-155">Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="16061-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>

<span data-ttu-id="16061-156">Aşağıdaki örnek, `Continue For` ve `Exit For` deyimlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16061-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="16061-157">Bir... içinde herhangi `Exit For` bir `For`sayıda deyim yerleştirebilirsiniz.`Next`</span><span class="sxs-lookup"><span data-stu-id="16061-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="16061-158">gerçekleştirmek.</span><span class="sxs-lookup"><span data-stu-id="16061-158">loop.</span></span> <span data-ttu-id="16061-159">İç içe yerleştirilmiş `For`... içinde kullanıldığında`Next`</span><span class="sxs-lookup"><span data-stu-id="16061-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="16061-160">döngüler, `Exit For` en içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="16061-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="16061-161">`Exit For`genellikle bazı koşulları değerlendirdikten sonra kullanılır (örneğin, bir `If`... `Then`... `Else` yapı).</span><span class="sxs-lookup"><span data-stu-id="16061-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="16061-162">Aşağıdaki koşullar için kullanmak `Exit For` isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="16061-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="16061-163">Tekrarlamaya devam etmek gereksiz veya imkansız.</span><span class="sxs-lookup"><span data-stu-id="16061-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="16061-164">Hatalı bir değer veya sonlandırma isteği bu durumu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="16061-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="16061-165">A `Try`... `Catch`... `Finally` ifade bir özel durumu yakalar.</span><span class="sxs-lookup"><span data-stu-id="16061-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="16061-166">Bloğunun`Finally` sonunda kullanabilirsiniz `Exit For` .</span><span class="sxs-lookup"><span data-stu-id="16061-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="16061-167">Sonsuz bir döngüyle sahipsiniz, bu, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür.</span><span class="sxs-lookup"><span data-stu-id="16061-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="16061-168">Böyle bir koşulu tespit ediyorsanız, döngüyü atlamak için kullanabilirsiniz `Exit For` .</span><span class="sxs-lookup"><span data-stu-id="16061-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="16061-169">Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="16061-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="16061-170">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="16061-170">Technical Implementation</span></span>

<span data-ttu-id="16061-171">Bir `For`... döngü başlar, Visual Basic `start` `step`değerlendirir, ve. `end` `Next`</span><span class="sxs-lookup"><span data-stu-id="16061-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="16061-172">Visual Basic bu değerleri yalnızca şu anda değerlendirir ve sonra öğesine `start` `counter`atar.</span><span class="sxs-lookup"><span data-stu-id="16061-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="16061-173">Bildirim bloğu çalıştırılmadan önce, Visual Basic ile `counter` `end`karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="16061-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="16061-174">`end` `For` Zatendeğerdendaha`Next` büyükse (ya da negatifse küçüktür ),döngüsonlanırvedenetimideyimdensonrakideyimegeçer.`step` `counter`</span><span class="sxs-lookup"><span data-stu-id="16061-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="16061-175">Aksi halde, ekstre bloğu çalışır.</span><span class="sxs-lookup"><span data-stu-id="16061-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="16061-176">Her Visual Basic `Next` ifadesiyle karşılaştığında, `counter` `step` tarafındanartarveifadeyedöner.`For`</span><span class="sxs-lookup"><span data-stu-id="16061-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="16061-177">Bu `end`, ile `counter` karşılaştırılır ve sonuca bağlı olarak bloğu çalıştırır ya da döngüden çıkar.</span><span class="sxs-lookup"><span data-stu-id="16061-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="16061-178">Bu işlem, geçişe `counter` `end` veya bir `Exit For` deyimle karşılaşılana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="16061-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="16061-179">Döngü geçene `counter` `end`kadar durmaz.</span><span class="sxs-lookup"><span data-stu-id="16061-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="16061-180">`counter` Eşitse`end`, döngü devam eder.</span><span class="sxs-lookup"><span data-stu-id="16061-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="16061-181">`counter` Bloğunun `counter` çalıştırılıpçalıştırılmadığını >=  belirleyen karşılaştırma, pozitif ise ve`end` negatifse. `step`  <=  `end` `step`</span><span class="sxs-lookup"><span data-stu-id="16061-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="16061-182">Bir döngü içinde değerini `counter` değiştirirseniz, kodunuzun okunması ve hata ayıklaması daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="16061-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="16061-183">`start` ,`end`, Veya`step` değerini değiştirmek, döngünün ilk kez girildiği zaman belirlenen yineleme değerlerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="16061-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="16061-184">Döngülerin iç içe geçirilmesi durumunda derleyici, iç düzeydeki `Next` `Next` deyimden önce dış iç içe düzeyin ifadesiyle karşılaşırsa bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="16061-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="16061-185">Ancak, derleyici bu çakışan hatayı yalnızca her `counter` `Next` ifadede belirtirseniz tespit edebilir.</span><span class="sxs-lookup"><span data-stu-id="16061-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="16061-186">Adım bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="16061-186">Step Argument</span></span>

<span data-ttu-id="16061-187">Değeri `step` pozitif veya negatif olabilir.</span><span class="sxs-lookup"><span data-stu-id="16061-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="16061-188">Bu parametre, döngü işlemeyi aşağıdaki tabloya göre belirler:</span><span class="sxs-lookup"><span data-stu-id="16061-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="16061-189">**Adım değeri**</span><span class="sxs-lookup"><span data-stu-id="16061-189">**Step value**</span></span>|<span data-ttu-id="16061-190">**Döngü şunu içeriyorsa yürütülür**</span><span class="sxs-lookup"><span data-stu-id="16061-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="16061-191">Pozitif veya sıfır</span><span class="sxs-lookup"><span data-stu-id="16061-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="16061-192">Negatif</span><span class="sxs-lookup"><span data-stu-id="16061-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="16061-193">Varsayılan değeri `step` 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="16061-193">The default value of `step` is 1.</span></span>

### <a name="BKMK_Counter"></a><span data-ttu-id="16061-194">Sayaç bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="16061-194">Counter Argument</span></span>

<span data-ttu-id="16061-195">Aşağıdaki tabloda, tüm `counter` `For…Next` döngünün kapsamına alınmış yeni bir yerel değişken oluşturulup oluşturulmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16061-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="16061-196">Bu belirleme, var olup `datatype` olmadığına `counter` ve önceden tanımlanmış olup olmadığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="16061-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="16061-197">`datatype` Var mı?</span><span class="sxs-lookup"><span data-stu-id="16061-197">Is `datatype` present?</span></span>|<span data-ttu-id="16061-198">`counter` Zaten tanımlanmış mı?</span><span class="sxs-lookup"><span data-stu-id="16061-198">Is `counter` already defined?</span></span>|<span data-ttu-id="16061-199">Sonuç ( `counter` tüm `For...Next` döngünün kapsamına alınmış yeni bir yerel değişken tanımlar)</span><span class="sxs-lookup"><span data-stu-id="16061-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="16061-200">Hayır</span><span class="sxs-lookup"><span data-stu-id="16061-200">No</span></span>|<span data-ttu-id="16061-201">Evet</span><span class="sxs-lookup"><span data-stu-id="16061-201">Yes</span></span>|<span data-ttu-id="16061-202">Hayır, `counter` zaten tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="16061-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="16061-203">Öğesinin `counter` kapsamı, yordamda yerel değilse, bir derleme zamanı uyarısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="16061-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="16061-204">Hayır</span><span class="sxs-lookup"><span data-stu-id="16061-204">No</span></span>|<span data-ttu-id="16061-205">Hayır</span><span class="sxs-lookup"><span data-stu-id="16061-205">No</span></span>|<span data-ttu-id="16061-206">Evet.</span><span class="sxs-lookup"><span data-stu-id="16061-206">Yes.</span></span> <span data-ttu-id="16061-207">Veri türü `start`, `end`, ve `step` ifadelerinden algılanır.</span><span class="sxs-lookup"><span data-stu-id="16061-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="16061-208">Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="16061-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="16061-209">Evet</span><span class="sxs-lookup"><span data-stu-id="16061-209">Yes</span></span>|<span data-ttu-id="16061-210">Evet</span><span class="sxs-lookup"><span data-stu-id="16061-210">Yes</span></span>|<span data-ttu-id="16061-211">Evet, ancak yalnızca varolan `counter` değişken yordamın dışında tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="16061-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="16061-212">Bu değişken ayrı kalır.</span><span class="sxs-lookup"><span data-stu-id="16061-212">That variable remains separate.</span></span> <span data-ttu-id="16061-213">Varolan `counter` değişkenin kapsamı yordamın yerelse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="16061-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="16061-214">Evet</span><span class="sxs-lookup"><span data-stu-id="16061-214">Yes</span></span>|<span data-ttu-id="16061-215">Hayır</span><span class="sxs-lookup"><span data-stu-id="16061-215">No</span></span>|<span data-ttu-id="16061-216">Evet.</span><span class="sxs-lookup"><span data-stu-id="16061-216">Yes.</span></span>|

<span data-ttu-id="16061-217">Veri türü `counter` , aşağıdaki türlerden biri olması gereken yinelemenin türünü belirler:</span><span class="sxs-lookup"><span data-stu-id="16061-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="16061-218">A `Byte`, `SByte`, ,`UShort` ,,`ULong`,, ,`Decimal`,, veya .`Double` `Integer` `UInteger` `Short` `Long` `Single`</span><span class="sxs-lookup"><span data-stu-id="16061-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="16061-219">Bir [enum ifadesini](../../../visual-basic/language-reference/statements/enum-statement.md)kullanarak bildirdiğiniz bir sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="16061-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

- <span data-ttu-id="16061-220">Bir `Object`.</span><span class="sxs-lookup"><span data-stu-id="16061-220">An `Object`.</span></span>

- <span data-ttu-id="16061-221">Aşağıdaki işleçlere sahip bir tür `T` , burada `B` bir `Boolean` ifadede kullanılabilecek bir tür.</span><span class="sxs-lookup"><span data-stu-id="16061-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="16061-222">Bu `counter` değişkeni isteğe bağlı olarak `Next` deyimde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16061-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="16061-223">Bu sözdizimi, özellikle iç içe `For` döngüler varsa programınızın okunabilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="16061-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="16061-224">Karşılık gelen `For` ifadede görünen değişkeni belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="16061-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="16061-225">, Ve `end`ifadeleri,türü widens olan herhangi bir `counter`veri türünü değerlendirebilir. `step` `start`</span><span class="sxs-lookup"><span data-stu-id="16061-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="16061-226">`counter`İçin Kullanıcı tanımlı bir tür kullanırsanız,, veya `step` türlerini `end` `start`türüne `counter`dönüştürmek için `CType` dönüştürme işlecini tanımlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="16061-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="16061-227">Örnek</span><span class="sxs-lookup"><span data-stu-id="16061-227">Example</span></span>

<span data-ttu-id="16061-228">Aşağıdaki örnek, genel bir listeden tüm öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="16061-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="16061-229">[Her biri için bir değil... Next Ifadesinde](../../../visual-basic/language-reference/statements/for-each-next-statement.md), örnek bir `For`... `Next` azalan düzende yinelenen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="16061-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="16061-230">Bu örnek, `removeAt` yöntemi kaldırılan öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olduğundan bu tekniği kullanır.</span><span class="sxs-lookup"><span data-stu-id="16061-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="16061-231">Örnek</span><span class="sxs-lookup"><span data-stu-id="16061-231">Example</span></span>

<span data-ttu-id="16061-232">Aşağıdaki örnek, bir sabit listesi [bildirimi](../../../visual-basic/language-reference/statements/enum-statement.md)kullanılarak tanımlanan bir numaralandırma aracılığıyla yinelenir.</span><span class="sxs-lookup"><span data-stu-id="16061-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="16061-233">Örnek</span><span class="sxs-lookup"><span data-stu-id="16061-233">Example</span></span>

<span data-ttu-id="16061-234">Aşağıdaki örnekte, `+`ifade parametreleri `>=`, `-`,, ve `<=` işleçleri için işleç aşırı yüklemeleri olan bir sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="16061-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="16061-235">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16061-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="16061-236">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="16061-236">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="16061-237">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="16061-237">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="16061-238">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="16061-238">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="16061-239">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="16061-239">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="16061-240">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="16061-240">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="16061-241">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="16061-241">Collections</span></span>](../../programming-guide/concepts/collections.md)

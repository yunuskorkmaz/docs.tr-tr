---
title: For...Next Deyimi
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
ms.openlocfilehash: 6896c6cfb4ec5d6207011e56b72639c459120e53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404647"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="7bb69-102">For...Next Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bb69-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="7bb69-103">Bir deyim grubunu belirtilen sayıda yineler.</span><span class="sxs-lookup"><span data-stu-id="7bb69-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="7bb69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bb69-104">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="7bb69-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7bb69-105">Parts</span></span>

|<span data-ttu-id="7bb69-106">Bölüm</span><span class="sxs-lookup"><span data-stu-id="7bb69-106">Part</span></span>|<span data-ttu-id="7bb69-107">Description</span><span class="sxs-lookup"><span data-stu-id="7bb69-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="7bb69-108">`For`İfadesinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-108">Required in the `For` statement.</span></span> <span data-ttu-id="7bb69-109">Sayısal değişken.</span><span class="sxs-lookup"><span data-stu-id="7bb69-109">Numeric variable.</span></span> <span data-ttu-id="7bb69-110">Döngünün denetim değişkeni.</span><span class="sxs-lookup"><span data-stu-id="7bb69-110">The control variable for the loop.</span></span> <span data-ttu-id="7bb69-111">Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7bb69-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="7bb69-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7bb69-112">Optional.</span></span> <span data-ttu-id="7bb69-113">Veri türü `counter` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-113">Data type of `counter`.</span></span> <span data-ttu-id="7bb69-114">Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7bb69-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="7bb69-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-115">Required.</span></span> <span data-ttu-id="7bb69-116">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="7bb69-116">Numeric expression.</span></span> <span data-ttu-id="7bb69-117">Başlangıç değeri `counter` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="7bb69-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-118">Required.</span></span> <span data-ttu-id="7bb69-119">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="7bb69-119">Numeric expression.</span></span> <span data-ttu-id="7bb69-120">Öğesinin son değeri `counter` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="7bb69-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7bb69-121">Optional.</span></span> <span data-ttu-id="7bb69-122">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="7bb69-122">Numeric expression.</span></span> <span data-ttu-id="7bb69-123">`counter`Döngü aracılığıyla her seferinde arttırılan miktar.</span><span class="sxs-lookup"><span data-stu-id="7bb69-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="7bb69-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7bb69-124">Optional.</span></span> <span data-ttu-id="7bb69-125">Ve arasındaki bir veya daha fazla deyim `For` `Next` , belirtilen sayıda kez çalıştırıldı.</span><span class="sxs-lookup"><span data-stu-id="7bb69-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="7bb69-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7bb69-126">Optional.</span></span> <span data-ttu-id="7bb69-127">Denetimi sonraki döngü yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="7bb69-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7bb69-128">Optional.</span></span> <span data-ttu-id="7bb69-129">Denetimi döngünün dışına aktarır `For` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="7bb69-130">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-130">Required.</span></span> <span data-ttu-id="7bb69-131">Döngünün tanımını sonlandırır `For` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="7bb69-132">`To`Anahtar sözcüğü, bu bildirimde sayaç aralığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="7bb69-133">Bu anahtar sözcüğü Select... içinde de kullanabilirsiniz [. Case Bildirimi](select-case-statement.md) ve dizi bildirimlerinde.</span><span class="sxs-lookup"><span data-stu-id="7bb69-133">You can also use this keyword in the [Select...Case Statement](select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="7bb69-134">Dizi bildirimleri hakkında daha fazla bilgi için bkz. [Dim deyimleri](dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7bb69-134">For more information about array declarations, see [Dim Statement](dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="7bb69-135">Basit örnekler</span><span class="sxs-lookup"><span data-stu-id="7bb69-135">Simple Examples</span></span>

<span data-ttu-id="7bb69-136">Bir `For` `Next` deyim kümesini bir dizi defa tekrarlamak istediğinizde bir... yapısı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="7bb69-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="7bb69-137">Aşağıdaki örnekte, `index` değişken 1 değeri ile başlar ve döngünün her yinelemeyle artırılır, bu değer 5 ' e `index` ulaştığında biter.</span><span class="sxs-lookup"><span data-stu-id="7bb69-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="7bb69-138">Aşağıdaki örnekte, `number` değişken 2 ' de başlar ve döngünün her yinelemesinde 0,25 tarafından azaltılır ve değeri 0 ' dan sonra sona eriyor `number` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="7bb69-139">`Step`Öğesinin bağımsız değişkeni, `-.25` döngünün her yinelemede değeri 0,25 azaltır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="7bb69-140">Bir [while... End while ekstresi](while-end-while-statement.md) veya [Do... Loop deyimi](do-loop-statement.md) , döngüdeki deyimlerin kaç kez çalıştırılacağını önceden bilmiyorsanız iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-140">A [While...End While Statement](while-end-while-statement.md) or [Do...Loop Statement](do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="7bb69-141">Ancak, döngüyü belirli sayıda çalıştırmayı beklediğinizi, a `For` ... `Next` döngüsü daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="7bb69-142">Döngüyü ilk kez girerken yineleme sayısını belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="7bb69-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="7bb69-143">İç içe geçme döngüleri</span><span class="sxs-lookup"><span data-stu-id="7bb69-143">Nesting Loops</span></span>

<span data-ttu-id="7bb69-144">Bir `For` döngüyü diğerinin içine yerleştirerek döngüleri iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bb69-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="7bb69-145">Aşağıdaki örnek, `For` farklı adım değerlerine sahip iç içe... `Next` yapıları gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="7bb69-146">Dış döngü, döngünün her yinelemesi için bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7bb69-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="7bb69-147">İç döngü, döngünün her yinelemesi için bir döngü sayacı değişkenini azaltır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="7bb69-148">Döngüleri iç içe aktardığınızda her döngünün benzersiz bir değişkeni olmalıdır `counter` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="7bb69-149">Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bb69-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="7bb69-150">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="7bb69-150">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="7bb69-151">İçin çık ve devam et</span><span class="sxs-lookup"><span data-stu-id="7bb69-151">Exit For and Continue For</span></span>

<span data-ttu-id="7bb69-152">`Exit For`Deyimden hemen çıkar `For` ...`Next`</span><span class="sxs-lookup"><span data-stu-id="7bb69-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="7bb69-153">öğesini Loop ve deyimden sonraki deyime aktarır `Next` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="7bb69-154">`Continue For`İfade, denetimi döngünün bir sonraki yinelemesine hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="7bb69-155">Daha fazla bilgi için bkz. [Continue bildirisi](continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7bb69-155">For more information, see [Continue Statement](continue-statement.md).</span></span>

<span data-ttu-id="7bb69-156">Aşağıdaki örnek, `Continue For` ve deyimlerinin kullanımını gösterir `Exit For` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="7bb69-157">`Exit For`Bir... içinde herhangi bir sayıda deyim yerleştirebilirsiniz. `For``Next`</span><span class="sxs-lookup"><span data-stu-id="7bb69-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="7bb69-158">gerçekleştirmek.</span><span class="sxs-lookup"><span data-stu-id="7bb69-158">loop.</span></span> <span data-ttu-id="7bb69-159">İç içe yerleştirilmiş `For` ... içinde kullanıldığında`Next`</span><span class="sxs-lookup"><span data-stu-id="7bb69-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="7bb69-160">döngüler, en `Exit For` içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="7bb69-161">`Exit For`genellikle bazı koşulları değerlendirdikten sonra kullanılır (örneğin, bir `If` . `Then` .. ...`Else` Yapı).</span><span class="sxs-lookup"><span data-stu-id="7bb69-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="7bb69-162">`Exit For`Aşağıdaki koşullar için kullanmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7bb69-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="7bb69-163">Tekrarlamaya devam etmek gereksiz veya imkansız.</span><span class="sxs-lookup"><span data-stu-id="7bb69-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="7bb69-164">Hatalı bir değer veya sonlandırma isteği bu durumu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="7bb69-165">A `Try` .. `Catch` . ...`Finally` ifade bir özel durumu yakalar.</span><span class="sxs-lookup"><span data-stu-id="7bb69-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="7bb69-166">`Exit For`Bloğunun sonunda kullanabilirsiniz `Finally` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="7bb69-167">Sonsuz bir döngüyle sahipsiniz, bu, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür.</span><span class="sxs-lookup"><span data-stu-id="7bb69-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="7bb69-168">Böyle bir koşulu tespit ediyorsanız, `Exit For` döngüyü atlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bb69-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="7bb69-169">Daha fazla bilgi için bkz [. do... Loop deyimleri](do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7bb69-169">For more information, see [Do...Loop Statement](do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="7bb69-170">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="7bb69-170">Technical Implementation</span></span>

<span data-ttu-id="7bb69-171">Bir `For` ... `Next` döngüsü başladığında Visual Basic değerlendirir, `start` `end` ve `step` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="7bb69-172">Visual Basic bu değerleri yalnızca şu anda değerlendirir ve sonra öğesine atar `start` `counter` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="7bb69-173">Bildirim bloğu çalıştırılmadan önce, Visual Basic ile karşılaştırılır `counter` `end` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="7bb69-174">`counter`Zaten değerden daha büyükse `end` (ya da `step` negatifse küçüktür), `For` döngü sonlanır ve denetimi deyimden sonraki deyime geçer `Next` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="7bb69-175">Aksi halde, ekstre bloğu çalışır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="7bb69-176">Her Visual Basic `Next` ifadesiyle karşılaştığında, `counter` tarafından artar `step` ve `For` ifadeye döner.</span><span class="sxs-lookup"><span data-stu-id="7bb69-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="7bb69-177">Bu, ile `counter` karşılaştırılır `end` ve sonuca bağlı olarak bloğu çalıştırır ya da döngüden çıkar.</span><span class="sxs-lookup"><span data-stu-id="7bb69-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="7bb69-178">Bu işlem `counter` `end` , geçişe veya bir `Exit For` deyimle karşılaşılana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="7bb69-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="7bb69-179">Döngü geçene kadar durmaz `counter` `end` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="7bb69-180">`counter`Eşitse `end` , döngü devam eder.</span><span class="sxs-lookup"><span data-stu-id="7bb69-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="7bb69-181">Bloğunun çalıştırılıp çalıştırılmadığını belirleyen karşılaştırma, `counter`  <=  `end` `step` pozitif ise ve `counter`  >=  `end` `step` negatifse.</span><span class="sxs-lookup"><span data-stu-id="7bb69-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="7bb69-182">`counter`Bir döngü içinde değerini değiştirirseniz, kodunuzun okunması ve hata ayıklaması daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="7bb69-183">`start`,, Veya değerini değiştirmek, `end` `step` döngünün ilk kez girildiği zaman belirlenen yineleme değerlerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="7bb69-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="7bb69-184">Döngülerin iç içe geçirilmesi durumunda derleyici, `Next` `Next` iç düzeydeki deyimden önce dış iç içe düzeyin ifadesiyle karşılaşırsa bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="7bb69-185">Ancak, derleyici bu çakışan hatayı yalnızca her ifadede belirtirseniz tespit edebilir `counter` `Next` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="7bb69-186">Adım bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="7bb69-186">Step Argument</span></span>

<span data-ttu-id="7bb69-187">Değeri `step` pozitif veya negatif olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="7bb69-188">Bu parametre, döngü işlemeyi aşağıdaki tabloya göre belirler:</span><span class="sxs-lookup"><span data-stu-id="7bb69-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="7bb69-189">**Adım değeri**</span><span class="sxs-lookup"><span data-stu-id="7bb69-189">**Step value**</span></span>|<span data-ttu-id="7bb69-190">**Döngü şunu içeriyorsa yürütülür**</span><span class="sxs-lookup"><span data-stu-id="7bb69-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="7bb69-191">Pozitif veya sıfır</span><span class="sxs-lookup"><span data-stu-id="7bb69-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="7bb69-192">Negatif</span><span class="sxs-lookup"><span data-stu-id="7bb69-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="7bb69-193">`step` varsayılan değeri 1'dir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-193">The default value of `step` is 1.</span></span>

### <a name="counter-argument"></a><a name="BKMK_Counter"></a><span data-ttu-id="7bb69-194">Sayaç bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="7bb69-194">Counter Argument</span></span>

<span data-ttu-id="7bb69-195">Aşağıdaki tabloda, `counter` Tüm döngünün kapsamına alınmış yeni bir yerel değişken oluşturulup oluşturulmayacağını gösterir `For…Next` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="7bb69-196">Bu belirleme `datatype` , var olup olmadığına ve önceden tanımlanmış olup olmadığına bağlıdır `counter` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="7bb69-197">`datatype`Var mı?</span><span class="sxs-lookup"><span data-stu-id="7bb69-197">Is `datatype` present?</span></span>|<span data-ttu-id="7bb69-198">`counter`Zaten tanımlanmış mı?</span><span class="sxs-lookup"><span data-stu-id="7bb69-198">Is `counter` already defined?</span></span>|<span data-ttu-id="7bb69-199">Sonuç ( `counter` Tüm döngünün kapsamına alınmış yeni bir yerel değişken tanımlar `For...Next` )</span><span class="sxs-lookup"><span data-stu-id="7bb69-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="7bb69-200">Hayır</span><span class="sxs-lookup"><span data-stu-id="7bb69-200">No</span></span>|<span data-ttu-id="7bb69-201">Evet</span><span class="sxs-lookup"><span data-stu-id="7bb69-201">Yes</span></span>|<span data-ttu-id="7bb69-202">Hayır, `counter` zaten tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="7bb69-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="7bb69-203">Öğesinin kapsamı, `counter` yordamda yerel değilse, bir derleme zamanı uyarısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="7bb69-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="7bb69-204">No</span><span class="sxs-lookup"><span data-stu-id="7bb69-204">No</span></span>|<span data-ttu-id="7bb69-205">Hayır</span><span class="sxs-lookup"><span data-stu-id="7bb69-205">No</span></span>|<span data-ttu-id="7bb69-206">Evet.</span><span class="sxs-lookup"><span data-stu-id="7bb69-206">Yes.</span></span> <span data-ttu-id="7bb69-207">Veri türü `start` ,, `end` ve `step` ifadelerinden algılanır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="7bb69-208">Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](option-infer-statement.md) ve [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="7bb69-208">For information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="7bb69-209">Yes</span><span class="sxs-lookup"><span data-stu-id="7bb69-209">Yes</span></span>|<span data-ttu-id="7bb69-210">Yes</span><span class="sxs-lookup"><span data-stu-id="7bb69-210">Yes</span></span>|<span data-ttu-id="7bb69-211">Evet, ancak yalnızca varolan `counter` değişken yordamın dışında tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="7bb69-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="7bb69-212">Bu değişken ayrı kalır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-212">That variable remains separate.</span></span> <span data-ttu-id="7bb69-213">Varolan `counter` değişkenin kapsamı yordamın yerelse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="7bb69-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="7bb69-214">Yes</span><span class="sxs-lookup"><span data-stu-id="7bb69-214">Yes</span></span>|<span data-ttu-id="7bb69-215">Hayır</span><span class="sxs-lookup"><span data-stu-id="7bb69-215">No</span></span>|<span data-ttu-id="7bb69-216">Evet.</span><span class="sxs-lookup"><span data-stu-id="7bb69-216">Yes.</span></span>|

<span data-ttu-id="7bb69-217">Veri türü, `counter` aşağıdaki türlerden biri olması gereken yinelemenin türünü belirler:</span><span class="sxs-lookup"><span data-stu-id="7bb69-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="7bb69-218">A `Byte` , `SByte` , `UShort` , `Short` , `UInteger` , `Integer` , `ULong` , `Long` , `Decimal` , `Single` , veya `Double` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="7bb69-219">Bir [enum ifadesini](enum-statement.md)kullanarak bildirdiğiniz bir sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="7bb69-219">An enumeration that you declare by using an [Enum Statement](enum-statement.md).</span></span>

- <span data-ttu-id="7bb69-220">Bir `Object` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-220">An `Object`.</span></span>

- <span data-ttu-id="7bb69-221">`T`Aşağıdaki işleçlere sahip bir tür, burada `B` bir ifadede kullanılabilecek bir tür `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="7bb69-222">Bu değişkeni isteğe bağlı olarak `counter` `Next` deyimde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bb69-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="7bb69-223">Bu sözdizimi, özellikle iç içe döngüler varsa programınızın okunabilirliğini geliştirir `For` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="7bb69-224">Karşılık gelen ifadede görünen değişkeni belirtmeniz gerekir `For` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="7bb69-225">`start`, `end` Ve ifadeleri, `step` türü widens olan herhangi bir veri türünü değerlendirebilir `counter` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="7bb69-226">İçin Kullanıcı tanımlı bir tür kullanırsanız,, `counter` `CType` veya türlerini türüne dönüştürmek için dönüştürme işlecini tanımlamanız gerekebilir `start` `end` `step` `counter` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="7bb69-227">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bb69-227">Example</span></span>

<span data-ttu-id="7bb69-228">Aşağıdaki örnek, genel bir listeden tüm öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="7bb69-229">[Her biri için bir değil... Next Ifadesinde](for-each-next-statement.md)örnek, `For` azalan düzende yinelenen bir... `Next` ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-229">Instead of a [For Each...Next Statement](for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="7bb69-230">Bu örnek, `removeAt` yöntemi kaldırılan öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olduğundan bu tekniği kullanır.</span><span class="sxs-lookup"><span data-stu-id="7bb69-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="7bb69-231">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bb69-231">Example</span></span>

<span data-ttu-id="7bb69-232">Aşağıdaki örnek, bir sabit listesi [bildirimi](enum-statement.md)kullanılarak tanımlanan bir numaralandırma aracılığıyla yinelenir.</span><span class="sxs-lookup"><span data-stu-id="7bb69-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="7bb69-233">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bb69-233">Example</span></span>

<span data-ttu-id="7bb69-234">Aşağıdaki örnekte, ifade parametreleri,,, `+` `-` `>=` ve işleçleri için işleç aşırı yüklemeleri olan bir sınıfı kullanır `<=` .</span><span class="sxs-lookup"><span data-stu-id="7bb69-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="7bb69-235">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bb69-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="7bb69-236">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="7bb69-236">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="7bb69-237">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="7bb69-237">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="7bb69-238">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="7bb69-238">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="7bb69-239">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="7bb69-239">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="7bb69-240">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="7bb69-240">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="7bb69-241">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="7bb69-241">Collections</span></span>](../../programming-guide/concepts/collections.md)

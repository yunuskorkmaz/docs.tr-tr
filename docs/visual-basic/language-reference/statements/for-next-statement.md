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
ms.openlocfilehash: 3cae44abb8e790542f11e6c5a5f1e317675ff988
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351192"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="b8b4a-102">For...Next Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b4a-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="b8b4a-103">Bir deyim grubunu belirtilen sayıda yineler.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8b4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8b4a-104">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="b8b4a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b8b4a-105">Parts</span></span>

|<span data-ttu-id="b8b4a-106">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="b8b4a-106">Part</span></span>|<span data-ttu-id="b8b4a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8b4a-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="b8b4a-108">`For` bildiriminde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-108">Required in the `For` statement.</span></span> <span data-ttu-id="b8b4a-109">Sayısal değişken.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-109">Numeric variable.</span></span> <span data-ttu-id="b8b4a-110">Döngünün denetim değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-110">The control variable for the loop.</span></span> <span data-ttu-id="b8b4a-111">Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="b8b4a-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-112">Optional.</span></span> <span data-ttu-id="b8b4a-113">`counter`veri türü.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-113">Data type of `counter`.</span></span> <span data-ttu-id="b8b4a-114">Daha fazla bilgi için bu konunun ilerleyen kısımlarında [sayaç bağımsız değişkeni](#BKMK_Counter) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="b8b4a-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-115">Required.</span></span> <span data-ttu-id="b8b4a-116">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-116">Numeric expression.</span></span> <span data-ttu-id="b8b4a-117">`counter`başlangıç değeri.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="b8b4a-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-118">Required.</span></span> <span data-ttu-id="b8b4a-119">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-119">Numeric expression.</span></span> <span data-ttu-id="b8b4a-120">`counter`son değeri.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="b8b4a-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-121">Optional.</span></span> <span data-ttu-id="b8b4a-122">Sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-122">Numeric expression.</span></span> <span data-ttu-id="b8b4a-123">`counter` döngüyle her seferinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="b8b4a-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-124">Optional.</span></span> <span data-ttu-id="b8b4a-125">`For` ve `Next` arasındaki, belirtilen sayıda kez çalışan bir veya daha fazla deyim.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="b8b4a-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-126">Optional.</span></span> <span data-ttu-id="b8b4a-127">Denetimi sonraki döngü yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="b8b4a-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-128">Optional.</span></span> <span data-ttu-id="b8b4a-129">`For` döngüsünün dışına denetimini aktarır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="b8b4a-130">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-130">Required.</span></span> <span data-ttu-id="b8b4a-131">`For` döngüsünün tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="b8b4a-132">`To` anahtar sözcüğü, bu bildirimde sayaç aralığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="b8b4a-133">Bu anahtar sözcüğü Select... içinde de kullanabilirsiniz [. Case Bildirimi](../../../visual-basic/language-reference/statements/select-case-statement.md) ve dizi bildirimlerinde.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="b8b4a-134">Dizi bildirimleri hakkında daha fazla bilgi için bkz. [Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8b4a-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="b8b4a-135">Basit örnekler</span><span class="sxs-lookup"><span data-stu-id="b8b4a-135">Simple Examples</span></span>

<span data-ttu-id="b8b4a-136">Bir dizi deyimin kümesini birkaç kez yinelemek istediğinizde `For`...`Next` yapısını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="b8b4a-137">Aşağıdaki örnekte, `index` değişkeni 1 değeriyle başlar ve döngünün her yinelemeyle artırılır, `index` değeri 5 ' e ulaştığında sona eriyor.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="b8b4a-138">Aşağıdaki örnekte, `number` değişkeni 2 ' de başlar ve döngünün her yinelemesi için 0,25 tarafından azaltılır, `number` değeri 0 ' a ulaştığında sona eriyor.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="b8b4a-139">`-.25` `Step` bağımsız değişkeni, döngünün her yinelemede değeri 0,25 azaltır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="b8b4a-140">Bir [while... End while ekstresi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) veya [Do... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md) , döngüdeki deyimlerin kaç kez çalıştırılacağını önceden bilmiyorsanız iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="b8b4a-141">Ancak, döngüyü belirli sayıda çalıştırmayı düşünüyorsanız, bir `For`...`Next` döngüsü daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="b8b4a-142">Döngüyü ilk kez girerken yineleme sayısını belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="b8b4a-143">İç içe geçme döngüleri</span><span class="sxs-lookup"><span data-stu-id="b8b4a-143">Nesting Loops</span></span>

<span data-ttu-id="b8b4a-144">Bir döngüyü diğerinin içine yerleştirerek `For` döngüleri iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="b8b4a-145">Aşağıdaki örnek, farklı adım değerlerine sahip iç içe `For`...`Next` yapılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="b8b4a-146">Dış döngü, döngünün her yinelemesi için bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="b8b4a-147">İç döngü, döngünün her yinelemesi için bir döngü sayacı değişkenini azaltır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="b8b4a-148">Döngüleri iç içe aktardığınızda her döngünün benzersiz bir `counter` değişkeni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="b8b4a-149">Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="b8b4a-150">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="b8b4a-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="b8b4a-151">İçin çık ve devam et</span><span class="sxs-lookup"><span data-stu-id="b8b4a-151">Exit For and Continue For</span></span>

<span data-ttu-id="b8b4a-152">`Exit For` deyimden hemen çıkış `For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="b8b4a-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="b8b4a-153">`Next` deyimlerini izleyen deyime döngü ve denetim aktarır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="b8b4a-154">`Continue For` bildiri, denetimi döngünün bir sonraki yinelemesine hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="b8b4a-155">Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8b4a-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>

<span data-ttu-id="b8b4a-156">Aşağıdaki örnekte `Continue For` ve `Exit For` deyimlerinin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="b8b4a-157">Bir `For`...`Next` istediğiniz sayıda `Exit For` deyimi koyabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="b8b4a-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="b8b4a-158">Gerçekleştirmek.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-158">loop.</span></span> <span data-ttu-id="b8b4a-159">İç içe geçmiş `For`içinde kullanıldığında...`Next`</span><span class="sxs-lookup"><span data-stu-id="b8b4a-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="b8b4a-160">döngüler, `Exit For` en içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="b8b4a-161">`Exit For`, genellikle bazı koşulları değerlendirdikten sonra kullanılır (örneğin, bir `If`...`Then`...`Else` yapısı).</span><span class="sxs-lookup"><span data-stu-id="b8b4a-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="b8b4a-162">Aşağıdaki koşullarda `Exit For` kullanmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b8b4a-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="b8b4a-163">Tekrarlamaya devam etmek gereksiz veya imkansız.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="b8b4a-164">Hatalı bir değer veya sonlandırma isteği bu durumu oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="b8b4a-165">Bir `Try`...`Catch`...`Finally` ifadesinde bir özel durum yakalar.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="b8b4a-166">`Finally` bloğunun sonunda `Exit For` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="b8b4a-167">Sonsuz bir döngüyle sahipsiniz, bu, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="b8b4a-168">Böyle bir koşulu tespit ediyorsanız, döngüden çıkmak için `Exit For` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="b8b4a-169">Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b8b4a-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="b8b4a-170">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="b8b4a-170">Technical Implementation</span></span>

<span data-ttu-id="b8b4a-171">Bir `For`...`Next` döngüsü başladığında Visual Basic `start`, `end`ve `step`değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="b8b4a-172">Visual Basic bu değerleri yalnızca şu anda değerlendirir ve `counter``start` atar.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="b8b4a-173">Bildirim bloğu çalıştırılmadan önce, `counter` `end`Visual Basic karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="b8b4a-174">`counter` zaten `end` değerden daha büyükse (veya `step` negatifse küçüktür), `For` döngüsü sonlanır ve denetim `Next` ifadesiyle sonraki deyime geçer.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="b8b4a-175">Aksi halde, ekstre bloğu çalışır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="b8b4a-176">Visual Basic `Next` deyimle karşılaştığında, `step` tarafından `counter` artırır ve `For` bildirimine geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="b8b4a-177">`counter`, `end`ile karşılaştırır ve sonuca bağlı olarak engellemeyi çalıştırır ya da döngüden çıkar.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="b8b4a-178">Bu işlem, `counter` `end` geçirene veya bir `Exit For` ifadesiyle karşılaşana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="b8b4a-179">`counter` `end`geçirene kadar döngü durdurulmaz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="b8b4a-180">`counter` `end`eşitse, döngü devam eder.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="b8b4a-181">Bloğunun çalıştırılıp çalıştırılmayacağını belirleyen karşılaştırma, `step` pozitif ve `counter` >= negatifse `end` `end`  <= `counter`.`step`</span><span class="sxs-lookup"><span data-stu-id="b8b4a-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="b8b4a-182">Bir döngü içinde `counter` değerini değiştirirseniz, kodunuzun okunması ve hata ayıklaması daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="b8b4a-183">`start`, `end`veya `step` değerini değiştirmek, döngünün ilk kez girildiği zaman belirlenen yineleme değerlerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="b8b4a-184">Döngüleri iç içe alırsanız derleyici bir iç düzeyin `Next` ifadesinden önce bir dış iç içe geçme düzeyinin `Next` ifadesiyle karşılaşırsa bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="b8b4a-185">Ancak, derleyici yalnızca her `Next` bildiriminde `counter` belirtirseniz bu çakışan hatayı algılayabilir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="b8b4a-186">Adım bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="b8b4a-186">Step Argument</span></span>

<span data-ttu-id="b8b4a-187">`step` değeri pozitif veya negatif olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="b8b4a-188">Bu parametre, döngü işlemeyi aşağıdaki tabloya göre belirler:</span><span class="sxs-lookup"><span data-stu-id="b8b4a-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="b8b4a-189">**Adım değeri**</span><span class="sxs-lookup"><span data-stu-id="b8b4a-189">**Step value**</span></span>|<span data-ttu-id="b8b4a-190">**Döngü şunu içeriyorsa yürütülür**</span><span class="sxs-lookup"><span data-stu-id="b8b4a-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="b8b4a-191">Pozitif veya sıfır</span><span class="sxs-lookup"><span data-stu-id="b8b4a-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="b8b4a-192">Negatif</span><span class="sxs-lookup"><span data-stu-id="b8b4a-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="b8b4a-193">`step` varsayılan değeri 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-193">The default value of `step` is 1.</span></span>

### <a name="BKMK_Counter"></a><span data-ttu-id="b8b4a-194">Sayaç bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="b8b4a-194">Counter Argument</span></span>

<span data-ttu-id="b8b4a-195">Aşağıdaki tabloda `counter`, tüm `For…Next` döngüsünün kapsamına alınmış yeni bir yerel değişken oluşturulup oluşturulmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="b8b4a-196">Bu belirleme `datatype` var olup olmadığına ve `counter` önceden tanımlanmış olup olmadığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="b8b4a-197">`datatype` var mı?</span><span class="sxs-lookup"><span data-stu-id="b8b4a-197">Is `datatype` present?</span></span>|<span data-ttu-id="b8b4a-198">`counter` zaten tanımlandı mı?</span><span class="sxs-lookup"><span data-stu-id="b8b4a-198">Is `counter` already defined?</span></span>|<span data-ttu-id="b8b4a-199">Sonuç (`counter`, tüm `For...Next` döngüsünün kapsamına alınmış yeni bir yerel değişken tanımlıyor)</span><span class="sxs-lookup"><span data-stu-id="b8b4a-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="b8b4a-200">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8b4a-200">No</span></span>|<span data-ttu-id="b8b4a-201">Evet</span><span class="sxs-lookup"><span data-stu-id="b8b4a-201">Yes</span></span>|<span data-ttu-id="b8b4a-202">Hayır, `counter` zaten tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="b8b4a-203">`counter` kapsamı yordamda yerel değilse, bir derleme zamanı uyarısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="b8b4a-204">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8b4a-204">No</span></span>|<span data-ttu-id="b8b4a-205">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8b4a-205">No</span></span>|<span data-ttu-id="b8b4a-206">Evet.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-206">Yes.</span></span> <span data-ttu-id="b8b4a-207">Veri türü `start`, `end`ve `step` ifadelerinden algılanır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="b8b4a-208">Tür çıkarımı hakkında daha fazla bilgi için bkz. [Option Infer deyimleri](../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="b8b4a-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="b8b4a-209">Evet</span><span class="sxs-lookup"><span data-stu-id="b8b4a-209">Yes</span></span>|<span data-ttu-id="b8b4a-210">Evet</span><span class="sxs-lookup"><span data-stu-id="b8b4a-210">Yes</span></span>|<span data-ttu-id="b8b4a-211">Evet, ancak yalnızca varolan `counter` değişkeni yordam dışında tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="b8b4a-212">Bu değişken ayrı kalır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-212">That variable remains separate.</span></span> <span data-ttu-id="b8b4a-213">Varolan `counter` değişkeninin kapsamı yordamda yerelse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="b8b4a-214">Evet</span><span class="sxs-lookup"><span data-stu-id="b8b4a-214">Yes</span></span>|<span data-ttu-id="b8b4a-215">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8b4a-215">No</span></span>|<span data-ttu-id="b8b4a-216">Evet.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-216">Yes.</span></span>|

<span data-ttu-id="b8b4a-217">`counter` veri türü yinelemenin türünü belirler ve bu türlerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b8b4a-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="b8b4a-218">`Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="b8b4a-219">Bir [enum ifadesini](../../../visual-basic/language-reference/statements/enum-statement.md)kullanarak bildirdiğiniz bir sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

- <span data-ttu-id="b8b4a-220">Bir `Object`.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-220">An `Object`.</span></span>

- <span data-ttu-id="b8b4a-221">`T`, `B` `Boolean` ifadesinde kullanılabilecek bir tür olan aşağıdaki işleçlere sahip bir tür.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="b8b4a-222">İsteğe bağlı olarak, `Next` bildiriminde `counter` değişkenini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="b8b4a-223">Bu sözdizimi, özellikle iç içe geçmiş `For` döngülerine sahipseniz programınızın okunabilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="b8b4a-224">Karşılık gelen `For` ifadesinde görünen değişkeni belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="b8b4a-225">`start`, `end`ve `step` ifadeleri, `counter`türüne sahip herhangi bir veri türü için değerlendirebilirler.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="b8b4a-226">`counter`için Kullanıcı tanımlı bir tür kullanıyorsanız, `start`, `end`veya `step` türlerini `counter`türüne dönüştürmek için `CType` dönüştürme işlecini tanımlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="b8b4a-227">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b4a-227">Example</span></span>

<span data-ttu-id="b8b4a-228">Aşağıdaki örnek, genel bir listeden tüm öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="b8b4a-229">[Her biri için bir değil... Next Ifadesinde](../../../visual-basic/language-reference/statements/for-each-next-statement.md)örnek, azalan düzende yinelenen bir `For`...`Next` ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="b8b4a-230">Örnek, `removeAt` yöntemi kaldırılan öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olduğundan bu tekniği kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="b8b4a-231">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b4a-231">Example</span></span>

<span data-ttu-id="b8b4a-232">Aşağıdaki örnek, bir sabit listesi [bildirimi](../../../visual-basic/language-reference/statements/enum-statement.md)kullanılarak tanımlanan bir numaralandırma aracılığıyla yinelenir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="b8b4a-233">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b4a-233">Example</span></span>

<span data-ttu-id="b8b4a-234">Aşağıdaki örnekte, ifade parametreleri `+`, `-`, `>=`ve `<=` işleçleri için işleç aşırı yüklemeleri olan bir sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="b8b4a-235">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="b8b4a-236">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="b8b4a-236">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="b8b4a-237">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="b8b4a-237">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="b8b4a-238">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="b8b4a-238">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="b8b4a-239">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="b8b4a-239">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="b8b4a-240">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="b8b4a-240">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="b8b4a-241">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="b8b4a-241">Collections</span></span>](../../programming-guide/concepts/collections.md)

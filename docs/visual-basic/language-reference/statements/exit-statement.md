---
title: Exit Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: e08d436686876a0a3d63f15167d35383e32221e7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967808"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="2038b-102">Exit Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2038b-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="2038b-103">Bir yordam ya da bloktan çıkıp ve denetim yordam çağrısı ya da blok tanımının takiben deyime hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="2038b-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2038b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2038b-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="2038b-105">Deyimler</span><span class="sxs-lookup"><span data-stu-id="2038b-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="2038b-106">Hemen çıkar `Do` döngü, bunu görünür.</span><span class="sxs-lookup"><span data-stu-id="2038b-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="2038b-107">Yürütme devam eder, deyimi aşağıdaki `Loop` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="2038b-108">`Exit Do` yalnızca içinde kullanılan bir `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="2038b-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="2038b-109">Kullanıldığında içinde iç içe geçmiş `Do` döngüleri `Exit Do` en içteki döngüden çıkılıp ve yüksek düzeye iç içe aktarır.</span><span class="sxs-lookup"><span data-stu-id="2038b-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="2038b-110">Hemen çıkar `For` döngü, bunu görünür.</span><span class="sxs-lookup"><span data-stu-id="2038b-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="2038b-111">Yürütme devam eder, deyimi aşağıdaki `Next` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="2038b-112">`Exit For` yalnızca içinde kullanılan bir `For`... `Next` veya `For Each`... `Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="2038b-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="2038b-113">Kullanıldığında içinde iç içe geçmiş `For` döngüleri `Exit For` en içteki döngüden çıkılıp ve yüksek düzeye iç içe aktarır.</span><span class="sxs-lookup"><span data-stu-id="2038b-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="2038b-114">Hemen çıkar `Function` göründüğü yordamı.</span><span class="sxs-lookup"><span data-stu-id="2038b-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="2038b-115">Yürütme devam eder, adlı deyiminin sonrasındaki deyime ile `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2038b-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="2038b-116">`Exit Function` yalnızca içinde kullanılan bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2038b-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="2038b-117">Dönüş değeri belirtmek için değer önce bir satırda işlevi adı atayabilirsiniz `Exit Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="2038b-118">Dönüş değeri atamak ve bir deyim işlev çıkmak için bunun yerine kullanabileceğiniz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2038b-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="2038b-119">Hemen çıkar `Property` göründüğü yordamı.</span><span class="sxs-lookup"><span data-stu-id="2038b-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="2038b-120">Yürütme devam eder, çağrılan deyimiyle `Property` yordamı, diğer bir deyişle, isteme veya özelliğin değerini ayarlamak deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="2038b-121">`Exit Property` yalnızca bir özelliğin içinde kullanılabilir `Get` veya `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2038b-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="2038b-122">Bir dönüş değeri belirtmek için bir `Get` yordamı, önce bir satırda işlevi adı değeri atayabilir `Exit Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="2038b-123">Çıkış ve dönüş değeri atamak `Get` bir deyim yordamda, bunun yerine kullanabileceğiniz `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="2038b-124">İçinde bir `Set` yordamı `Exit Property` deyimi, `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="2038b-125">Hemen çıkar `Select Case` hangi görünmesini engelleyin.</span><span class="sxs-lookup"><span data-stu-id="2038b-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="2038b-126">Yürütme devam eder, deyimi aşağıdaki `End Select` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="2038b-127">`Exit Select` yalnızca içinde kullanılan bir `Select Case` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="2038b-128">Hemen çıkar `Sub` göründüğü yordamı.</span><span class="sxs-lookup"><span data-stu-id="2038b-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="2038b-129">Yürütme devam eder, adlı deyiminin sonrasındaki deyime ile `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2038b-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="2038b-130">`Exit Sub` yalnızca içinde kullanılan bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="2038b-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="2038b-131">İçinde bir `Sub` yordamı `Exit Sub` deyimi, `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="2038b-132">Hemen çıkar `Try` veya `Catch` hangi görünmesini engelleyin.</span><span class="sxs-lookup"><span data-stu-id="2038b-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="2038b-133">Yürütme devam eder ile `Finally` varsa veya deyimi aşağıdaki `End Try` deyimi Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="2038b-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="2038b-134">`Exit Try` yalnızca içinde kullanılan bir `Try` veya `Catch` bloğu ve değil iç bir `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="2038b-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="2038b-135">Hemen çıkar `While` döngü, bunu görünür.</span><span class="sxs-lookup"><span data-stu-id="2038b-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="2038b-136">Yürütme devam eder, deyimi aşağıdaki `End While` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="2038b-137">`Exit While` yalnızca içinde kullanılan bir `While` döngü.</span><span class="sxs-lookup"><span data-stu-id="2038b-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="2038b-138">Kullanıldığında içinde iç içe geçmiş `While` döngüleri `Exit While` döngü yukarıda bir iç içe düzeyi döngü denetim aktarır burada `Exit While` gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="2038b-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2038b-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2038b-139">Remarks</span></span>  
 <span data-ttu-id="2038b-140">Karıştırmayın `Exit` ifadelerle `End` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="2038b-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="2038b-141">`Exit` bir deyim sonu tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="2038b-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2038b-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="2038b-142">Example</span></span>  
 <span data-ttu-id="2038b-143">Aşağıdaki örnekte, döngü koşuluna döngü durdurur, `index` değişkendir 100'den büyük.</span><span class="sxs-lookup"><span data-stu-id="2038b-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="2038b-144">`If` Döngü deyimi ancak neden `Exit Do` döngüyü dizin değişkeni 10'dan büyük olduğunda durdurmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="2038b-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="2038b-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="2038b-145">Example</span></span>  
 <span data-ttu-id="2038b-146">Aşağıdaki örnek, işlev adını dönüş değeri atar `myFunction`ve ardından `Exit Function` işlevden döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="2038b-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="2038b-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="2038b-147">Example</span></span>  
 <span data-ttu-id="2038b-148">Aşağıdaki örnekte [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) dönüş değerini atayın ve işlev çıkın.</span><span class="sxs-lookup"><span data-stu-id="2038b-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="2038b-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2038b-149">See also</span></span>
- [<span data-ttu-id="2038b-150">Continue Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
- [<span data-ttu-id="2038b-151">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="2038b-152">End Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
- [<span data-ttu-id="2038b-153">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="2038b-154">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="2038b-155">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="2038b-156">Return Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="2038b-157">Stop Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="2038b-158">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="2038b-159">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="2038b-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

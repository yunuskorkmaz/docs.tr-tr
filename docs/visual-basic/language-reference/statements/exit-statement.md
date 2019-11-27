---
title: Exit Deyimi
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
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345931"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="dc057-102">Exit Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc057-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="dc057-103">Bir yordam veya bloğundan çıkar ve denetimi yordam çağrısının veya blok tanımının ardından gelen deyime hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="dc057-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="dc057-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc057-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="dc057-105">Deyimler</span><span class="sxs-lookup"><span data-stu-id="dc057-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="dc057-106">Görüntülenen `Do` döngüsünden hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="dc057-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="dc057-107">Yürütme `Loop` deyiminden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="dc057-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="dc057-108">`Exit Do`, yalnızca bir `Do` döngüsü içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc057-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="dc057-109">İç içe geçmiş `Do` döngüleri içinde kullanıldığında, `Exit Do` en içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="dc057-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="dc057-110">Görüntülenen `For` döngüsünden hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="dc057-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="dc057-111">Yürütme `Next` deyiminden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="dc057-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="dc057-112">`Exit For`, yalnızca bir `For`...`Next` veya `For Each`...`Next` döngüsü içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc057-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="dc057-113">İç içe geçmiş `For` döngüleri içinde kullanıldığında, `Exit For` en içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="dc057-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="dc057-114">Görüntülenen `Function` yordamından hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="dc057-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="dc057-115">Yürütme `Function` yordamını çağıran deyimden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="dc057-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="dc057-116">`Exit Function`, yalnızca bir `Function` yordamı içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc057-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="dc057-117">Bir dönüş değeri belirtmek için, `Exit Function` deyimden önceki bir satırdaki işlev adına değeri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc057-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="dc057-118">Dönüş değerini atamak ve tek bir ifadede işlevinden çıkmak için, bunun yerine [return ifadesini](return-statement.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc057-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="dc057-119">Görüntülenen `Property` yordamından hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="dc057-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="dc057-120">Yürütme `Property` yordamını çağıran deyimle devam eder, diğer bir deyişle, özellik değerini talep eden veya ayarla.</span><span class="sxs-lookup"><span data-stu-id="dc057-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="dc057-121">`Exit Property`, yalnızca özelliğin `Get` veya `Set` yordamının içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc057-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="dc057-122">Bir `Get` yordamında bir dönüş değeri belirtmek için, `Exit Property` deyimden önceki bir satırdaki işlev adına değeri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc057-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="dc057-123">Dönüş değerini atamak ve tek bir ifadede `Get` yordamından çıkmak için, bunun yerine `Return` ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc057-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="dc057-124">`Set` yordamında, `Exit Property` deyimleri `Return` ifadesiyle eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="dc057-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="dc057-125">Görüntülenen `Select Case` bloğundan hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="dc057-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="dc057-126">Yürütme `End Select` deyiminden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="dc057-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="dc057-127">`Exit Select`, yalnızca bir `Select Case` bildiriminde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc057-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="dc057-128">Görüntülenen `Sub` yordamından hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="dc057-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="dc057-129">Yürütme `Sub` yordamını çağıran deyimden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="dc057-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="dc057-130">`Exit Sub`, yalnızca bir `Sub` yordamı içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc057-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="dc057-131">`Sub` yordamında, `Exit Sub` deyimleri `Return` ifadesiyle eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="dc057-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="dc057-132">Görüntülenen `Try` veya `Catch` bloğundan hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="dc057-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="dc057-133">Yürütme, varsa `Finally` bloğuyla devam eder veya `End Try` deyiminden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="dc057-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="dc057-134">`Exit Try`, `Finally` bloğu içinde değil, yalnızca bir `Try` veya `Catch` bloğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc057-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="dc057-135">Görüntülenen `While` döngüsünden hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="dc057-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="dc057-136">Yürütme `End While` deyiminden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="dc057-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="dc057-137">`Exit While`, yalnızca bir `While` döngüsü içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc057-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="dc057-138">İç içe `While` döngüleri içinde kullanıldığında, `Exit While` denetimi, döngünün üzerinde yer alan bir iç içe geçmiş düzeyi olan döngüye `Exit While` meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="dc057-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc057-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc057-139">Remarks</span></span>

<span data-ttu-id="dc057-140">`Exit` deyimlerini `End` deyimleriyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="dc057-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="dc057-141">`Exit` deyimin sonunu tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="dc057-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="dc057-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc057-142">Example</span></span>

<span data-ttu-id="dc057-143">Aşağıdaki örnekte, `index` değişken 100 ' den büyükse döngü koşulu döngüyü sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="dc057-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="dc057-144">Ancak, döngüdeki `If` ifade, dizin değişkeni 10 ' dan büyük olduğunda `Exit Do` deyimin döngüyü durdurmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="dc057-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="dc057-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc057-145">Example</span></span>

<span data-ttu-id="dc057-146">Aşağıdaki örnek, `myFunction`işlev adına döndürülen değeri atar ve sonra işlevden geri dönmek için `Exit Function` kullanır:</span><span class="sxs-lookup"><span data-stu-id="dc057-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="dc057-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc057-147">Example</span></span>

<span data-ttu-id="dc057-148">Aşağıdaki örnek, dönüş değerini atamak ve işlevden çıkmak için [return ifadesini](return-statement.md) kullanır:</span><span class="sxs-lookup"><span data-stu-id="dc057-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="dc057-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc057-149">See also</span></span>

- [<span data-ttu-id="dc057-150">Continue Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="dc057-151">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="dc057-152">End Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="dc057-153">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="dc057-154">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="dc057-155">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="dc057-156">Return Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="dc057-157">Stop Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="dc057-158">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="dc057-159">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc057-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)

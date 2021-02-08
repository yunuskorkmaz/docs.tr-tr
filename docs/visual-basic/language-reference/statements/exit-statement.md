---
description: 'Daha fazla bilgi edinin: Exit deyiminiz (Visual Basic)'
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
ms.openlocfilehash: 54af7fbf908dbad829cf6f08bf442dfe85e35610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769136"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="29933-103">Exit Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29933-103">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="29933-104">Bir yordam veya bloğundan çıkar ve denetimi yordam çağrısının veya blok tanımının ardından gelen deyime hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="29933-104">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="29933-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="29933-105">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="29933-106">Deyimler</span><span class="sxs-lookup"><span data-stu-id="29933-106">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="29933-107">`Do`Üzerinde Göründüğü döngüden hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="29933-107">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="29933-108">Yürütme, deyimden sonraki deyimle devam eder `Loop` .</span><span class="sxs-lookup"><span data-stu-id="29933-108">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="29933-109">`Exit Do` yalnızca bir döngü içinde kullanılabilir `Do` .</span><span class="sxs-lookup"><span data-stu-id="29933-109">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="29933-110">İç içe döngüler içinde kullanıldığında `Do` , en `Exit Do` içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="29933-110">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="29933-111">`For`Üzerinde Göründüğü döngüden hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="29933-111">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="29933-112">Yürütme, deyimden sonraki deyimle devam eder `Next` .</span><span class="sxs-lookup"><span data-stu-id="29933-112">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="29933-113">`Exit For` yalnızca bir `For` ... `Next` veya `For Each` ... döngüsü içinde kullanılabilir `Next` .</span><span class="sxs-lookup"><span data-stu-id="29933-113">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="29933-114">İç içe döngüler içinde kullanıldığında `For` , en `Exit For` içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="29933-114">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="29933-115">`Function`Görüntülenen yordamdan hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="29933-115">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="29933-116">Yürütme yordamı çağıran deyimden sonraki deyimle devam eder `Function` .</span><span class="sxs-lookup"><span data-stu-id="29933-116">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="29933-117">`Exit Function` yalnızca bir yordam içinde kullanılabilir `Function` .</span><span class="sxs-lookup"><span data-stu-id="29933-117">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="29933-118">Bir dönüş değeri belirtmek için, değeri deyimden önceki bir satırdaki işlev adına atayabilirsiniz `Exit Function` .</span><span class="sxs-lookup"><span data-stu-id="29933-118">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="29933-119">Dönüş değerini atamak ve tek bir ifadede işlevinden çıkmak için, bunun yerine [return ifadesini](return-statement.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29933-119">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="29933-120">`Property`Görüntülenen yordamdan hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="29933-120">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="29933-121">Yürütme, yordamı çağıran deyimle devam eder `Property` , diğer bir deyişle, özelliğin değerini talep eden veya ayarla.</span><span class="sxs-lookup"><span data-stu-id="29933-121">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="29933-122">`Exit Property` yalnızca bir özelliğin `Get` ya da yordamın içinde kullanılabilir `Set` .</span><span class="sxs-lookup"><span data-stu-id="29933-122">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="29933-123">Bir yordamda dönüş değeri belirtmek için `Get` , değeri deyimden önceki bir satırdaki işlev adına atayabilirsiniz `Exit Property` .</span><span class="sxs-lookup"><span data-stu-id="29933-123">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="29933-124">Dönüş değerini atamak ve `Get` yordamın tek bir ifadede çıkış yapmak için, bunun yerine `Return` ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29933-124">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="29933-125">Bir `Set` yordamda, `Exit Property` deyimleri `Return` ifadesiyle eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="29933-125">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="29933-126">`Select Case`Görüntülenen bloğundan hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="29933-126">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="29933-127">Yürütme, deyimden sonraki deyimle devam eder `End Select` .</span><span class="sxs-lookup"><span data-stu-id="29933-127">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="29933-128">`Exit Select` yalnızca bir deyimin içinde kullanılabilir `Select Case` .</span><span class="sxs-lookup"><span data-stu-id="29933-128">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="29933-129">`Sub`Görüntülenen yordamdan hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="29933-129">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="29933-130">Yürütme yordamı çağıran deyimden sonraki deyimle devam eder `Sub` .</span><span class="sxs-lookup"><span data-stu-id="29933-130">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="29933-131">`Exit Sub` yalnızca bir yordam içinde kullanılabilir `Sub` .</span><span class="sxs-lookup"><span data-stu-id="29933-131">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="29933-132">Bir `Sub` yordamda, `Exit Sub` deyimleri `Return` ifadesiyle eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="29933-132">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="29933-133">`Try`Görüntülenen veya bloğundan hemen çıkar `Catch` .</span><span class="sxs-lookup"><span data-stu-id="29933-133">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="29933-134">Yürütme, varsa bloğa devam eder `Finally` veya deyimden sonraki deyimle devam eder `End Try` .</span><span class="sxs-lookup"><span data-stu-id="29933-134">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="29933-135">`Exit Try` yalnızca bir veya bloğu içinde kullanılabilir `Try` `Catch` ve bir blok içinde kullanılamaz `Finally` .</span><span class="sxs-lookup"><span data-stu-id="29933-135">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="29933-136">`While`Üzerinde Göründüğü döngüden hemen çıkar.</span><span class="sxs-lookup"><span data-stu-id="29933-136">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="29933-137">Yürütme, deyimden sonraki deyimle devam eder `End While` .</span><span class="sxs-lookup"><span data-stu-id="29933-137">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="29933-138">`Exit While` yalnızca bir döngü içinde kullanılabilir `While` .</span><span class="sxs-lookup"><span data-stu-id="29933-138">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="29933-139">İç içe döngüler içinde kullanıldığında `While` , `Exit While` denetimi döngünün üzerinde bir iç içe geçmiş düzeyi olan döngüye aktarır `Exit While` .</span><span class="sxs-lookup"><span data-stu-id="29933-139">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="29933-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29933-140">Remarks</span></span>

<span data-ttu-id="29933-141">Deyimlerini `Exit` `End` deyimlerle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="29933-141">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="29933-142">`Exit` bir deyimin sonunu tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="29933-142">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="29933-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="29933-143">Example</span></span>

<span data-ttu-id="29933-144">Aşağıdaki örnekte, değişken 100 ' den büyükse döngü koşulu döngüyü sonlandırır `index` .</span><span class="sxs-lookup"><span data-stu-id="29933-144">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="29933-145">`If`Ancak, döngüdeki ifade, `Exit Do` Dizin değişkeni 10 ' dan büyük olduğunda deyimin döngüyü durdurmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="29933-145">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="29933-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="29933-146">Example</span></span>

<span data-ttu-id="29933-147">Aşağıdaki örnek, dönüş değerini işlev adına atar `myFunction` ve sonra `Exit Function` işlevden dönmek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="29933-147">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="29933-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="29933-148">Example</span></span>

<span data-ttu-id="29933-149">Aşağıdaki örnek, dönüş değerini atamak ve işlevden çıkmak için [return ifadesini](return-statement.md) kullanır:</span><span class="sxs-lookup"><span data-stu-id="29933-149">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="29933-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29933-150">See also</span></span>

- [<span data-ttu-id="29933-151">Continue Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-151">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="29933-152">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-152">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="29933-153">End ekstresi</span><span class="sxs-lookup"><span data-stu-id="29933-153">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="29933-154">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-154">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="29933-155">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-155">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="29933-156">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-156">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="29933-157">Return Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-157">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="29933-158">Stop Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-158">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="29933-159">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-159">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="29933-160">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="29933-160">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)

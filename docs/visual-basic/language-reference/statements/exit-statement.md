---
title: Exit Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df63ecbf0605d07296e1692f18b1b015e27cd03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="50fc6-102">Exit Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50fc6-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="50fc6-103">Bir yordam veya blok çıkar ve denetim hemen yordam çağrısı veya bloğu tanımı aşağıdaki deyim aktarır.</span><span class="sxs-lookup"><span data-stu-id="50fc6-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50fc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50fc6-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="50fc6-105">Deyimler</span><span class="sxs-lookup"><span data-stu-id="50fc6-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="50fc6-106">Hemen çıkar `Do` döngü onu görünen içinde.</span><span class="sxs-lookup"><span data-stu-id="50fc6-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="50fc6-107">Yürütülmeye deyimi aşağıdaki `Loop` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="50fc6-108">`Exit Do`yalnızca içinde kullanılan bir `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="50fc6-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="50fc6-109">Kullanıldığında içinde iç içe geçmiş `Do` döngüler, `Exit Do` en içteki döngüden çıkılıp ve iç içe geçme sonraki yüksek düzeyde denetim aktarır.</span><span class="sxs-lookup"><span data-stu-id="50fc6-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="50fc6-110">Hemen çıkar `For` döngü onu görünen içinde.</span><span class="sxs-lookup"><span data-stu-id="50fc6-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="50fc6-111">Yürütülmeye deyimi aşağıdaki `Next` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="50fc6-112">`Exit For`yalnızca içinde kullanılan bir `For`... `Next` veya `For Each`... `Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="50fc6-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="50fc6-113">Kullanıldığında içinde iç içe geçmiş `For` döngüler, `Exit For` en içteki döngüden çıkılıp ve iç içe geçme sonraki yüksek düzeyde denetim aktarır.</span><span class="sxs-lookup"><span data-stu-id="50fc6-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="50fc6-114">Hemen çıkar `Function` göründüğü yordamı.</span><span class="sxs-lookup"><span data-stu-id="50fc6-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="50fc6-115">Yürütülmeye adlı deyiminden deyimiyle `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="50fc6-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="50fc6-116">`Exit Function`yalnızca içinde kullanılan bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="50fc6-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="50fc6-117">Dönüş değeri belirtmek için değeri önce bir satırda işlev adı atayabilirsiniz `Exit Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="50fc6-118">Dönüş değeri atamak ve bir deyim işlevinde'ndan çıkmak için bunun yerine kullanabileceğiniz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="50fc6-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="50fc6-119">Hemen çıkar `Property` göründüğü yordamı.</span><span class="sxs-lookup"><span data-stu-id="50fc6-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="50fc6-120">Yürütülmeye adlı deyimiyle `Property` yordamı, diğer bir deyişle, isteme veya özelliğin değerini ayarlama ifadesiyle.</span><span class="sxs-lookup"><span data-stu-id="50fc6-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="50fc6-121">`Exit Property`yalnızca bir özelliğin içinde kullanılabilir `Get` veya `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="50fc6-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="50fc6-122">Bir dönüş değeri belirtmek için bir `Get` yordamı, önce bir satırda işlev adı için değer atayabilirsiniz `Exit Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="50fc6-123">Dönüş değeri ve çıkış atamak için `Get` bir deyim yordamda, bunun yerine kullanabileceğiniz `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="50fc6-124">İçinde bir `Set` yordamı, `Exit Property` deyimi eşdeğerdir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="50fc6-125">Hemen çıkar `Select Case` onu görünen içinde engelleyin.</span><span class="sxs-lookup"><span data-stu-id="50fc6-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="50fc6-126">Yürütülmeye deyimi aşağıdaki `End Select` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="50fc6-127">`Exit Select`yalnızca içinde kullanılan bir `Select Case` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="50fc6-128">Hemen çıkar `Sub` göründüğü yordamı.</span><span class="sxs-lookup"><span data-stu-id="50fc6-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="50fc6-129">Yürütülmeye adlı deyiminden deyimiyle `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="50fc6-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="50fc6-130">`Exit Sub`yalnızca içinde kullanılan bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="50fc6-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="50fc6-131">İçinde bir `Sub` yordamı, `Exit Sub` deyimi eşdeğerdir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="50fc6-132">Hemen çıkar `Try` veya `Catch` onu görünen içinde engelleyin.</span><span class="sxs-lookup"><span data-stu-id="50fc6-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="50fc6-133">Yürütülmeye ile `Finally` blok varsa veya deyimi aşağıdaki `End Try` deyimi Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="50fc6-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="50fc6-134">`Exit Try`yalnızca içinde kullanılan bir `Try` veya `Catch` bloğu ve değil iç bir `Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="50fc6-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="50fc6-135">Hemen çıkar `While` döngü onu görünen içinde.</span><span class="sxs-lookup"><span data-stu-id="50fc6-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="50fc6-136">Yürütülmeye deyimi aşağıdaki `End While` deyimi.</span><span class="sxs-lookup"><span data-stu-id="50fc6-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="50fc6-137">`Exit While`yalnızca içinde kullanılan bir `While` döngü.</span><span class="sxs-lookup"><span data-stu-id="50fc6-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="50fc6-138">Kullanıldığında içinde iç içe geçmiş `While` döngüler, `Exit While` denetimi bir iç içe düzeyi döngü yukarıda döngü aktarır nerede `Exit While` oluşur.</span><span class="sxs-lookup"><span data-stu-id="50fc6-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50fc6-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50fc6-139">Remarks</span></span>  
 <span data-ttu-id="50fc6-140">Aynı şey `Exit` deyimleri `End` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="50fc6-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="50fc6-141">`Exit`bir deyim sonu tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="50fc6-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50fc6-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="50fc6-142">Example</span></span>  
 <span data-ttu-id="50fc6-143">Aşağıdaki örnekte, döngü koşulunu döngü durur zaman `index` değişkenidir 100'den büyük.</span><span class="sxs-lookup"><span data-stu-id="50fc6-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="50fc6-144">`If` Döngüdeki deyimi ancak neden `Exit Do` deyimi dizin değişken 10'dan büyük olduğunda döngü durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="50fc6-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="50fc6-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="50fc6-145">Example</span></span>  
 <span data-ttu-id="50fc6-146">Aşağıdaki örnek, işlev adını dönüş değeri atar `myFunction`ve ardından `Exit Function` işlevinden dönün.</span><span class="sxs-lookup"><span data-stu-id="50fc6-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="50fc6-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="50fc6-147">Example</span></span>  
 <span data-ttu-id="50fc6-148">Aşağıdaki örnek kullanır [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) dönüş değeri atamak ve işlev çıkın.</span><span class="sxs-lookup"><span data-stu-id="50fc6-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="50fc6-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50fc6-149">See Also</span></span>  
 [<span data-ttu-id="50fc6-150">Continue deyimi</span><span class="sxs-lookup"><span data-stu-id="50fc6-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [<span data-ttu-id="50fc6-151">Yapın... Loop deyimi</span><span class="sxs-lookup"><span data-stu-id="50fc6-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="50fc6-152">End deyimi</span><span class="sxs-lookup"><span data-stu-id="50fc6-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="50fc6-153">For Each... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="50fc6-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="50fc6-154">İçin... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="50fc6-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="50fc6-155">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="50fc6-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="50fc6-156">Return deyimi</span><span class="sxs-lookup"><span data-stu-id="50fc6-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="50fc6-157">Stop deyimi</span><span class="sxs-lookup"><span data-stu-id="50fc6-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="50fc6-158">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="50fc6-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="50fc6-159">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="50fc6-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

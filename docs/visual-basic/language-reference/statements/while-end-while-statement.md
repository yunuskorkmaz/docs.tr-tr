---
title: While...End While Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 269a4c0f069b3837959b04f8463f96e7c5d5fdf7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970156"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="f0fbe-102">While...End While Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0fbe-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="f0fbe-103">Belirli bir koşul olduğu sürece bir deyimler serisini çalıştırır `True`.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0fbe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0fbe-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="f0fbe-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f0fbe-105">Parts</span></span>  
  
|<span data-ttu-id="f0fbe-106">Terim</span><span class="sxs-lookup"><span data-stu-id="f0fbe-106">Term</span></span>|<span data-ttu-id="f0fbe-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="f0fbe-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="f0fbe-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-108">Required.</span></span> <span data-ttu-id="f0fbe-109">`Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-109">`Boolean` expression.</span></span> <span data-ttu-id="f0fbe-110">Varsa `condition` olduğu `Nothing`, Visual Basic bunu algılar `False`.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="f0fbe-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-111">Optional.</span></span> <span data-ttu-id="f0fbe-112">Bir veya daha fazla deyimlerini aşağıdaki `While`, her zaman çalıştırdığınız `condition` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="f0fbe-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-113">Optional.</span></span> <span data-ttu-id="f0fbe-114">Denetim bir sonraki yinelemesine aktarır `While` blok.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="f0fbe-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-115">Optional.</span></span> <span data-ttu-id="f0fbe-116">Dışı denetim aktarır `While` blok.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="f0fbe-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-117">Required.</span></span> <span data-ttu-id="f0fbe-118">Tanımını sonlandırır `While` blok.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0fbe-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0fbe-119">Remarks</span></span>  
 <span data-ttu-id="f0fbe-120">Kullanım bir `While...End While` yapısı deyimleri belirsiz numarası bir kez, bir dizi yinelemek istediğinizde bir koşul devam ettiği sürece `True`.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="f0fbe-121">Daha fazla esneklikle burada koşulunu test etmek veya ne neden test Bunu tercih edebilirsiniz için isterseniz [yapın... Döngü deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0fbe-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="f0fbe-122">Bir kez sayıdaki deyimleri yinelemek istiyorsanız [için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0fbe-123">`While` Anahtar sözcüğü kullanılan ayrıca [yapın... Döngü deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Atla While yan tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md) ve [Take While tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f0fbe-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="f0fbe-124">Varsa `condition` olduğu `True`tüm, `statements` kadar çalıştırma `End While` deyimi karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="f0fbe-125">Denetim için verir `While` deyimi ve `condition` tekrar denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="f0fbe-126">Varsa `condition` hala `True`, işlem tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="f0fbe-127">Varsa `False`, Denetim izleyen deyime geçer `End While` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="f0fbe-128">`While` İfade her zaman, koşul döngünün başlamadan önce denetler.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="f0fbe-129">Döngü devam koşul kalırken `True`.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="f0fbe-130">Varsa `condition` olduğu `False` döngü ilk girdiğinizde, hatta bir kez çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="f0fbe-131">`condition` Genellikle iki değer, ancak bir karşılaştırma sonuçlarını olarak değerlendirilen herhangi bir ifade olabilir bir [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`).</span><span class="sxs-lookup"><span data-stu-id="f0fbe-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="f0fbe-132">Bu ifade için dönüştürülen sayısal tür gibi başka bir veri türünde bir değer içerebilir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="f0fbe-133">İç içe yerleştirebilirsiniz `While` içindeki başka bir döngü yerleştirerek döngüleri.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="f0fbe-134">Farklı türlerde denetim yapılarını içinde başka bir iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="f0fbe-135">Daha fazla bilgi için [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="f0fbe-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="f0fbe-136">Çıkış oluştu</span><span class="sxs-lookup"><span data-stu-id="f0fbe-136">Exit While</span></span>  
 <span data-ttu-id="f0fbe-137">[Çıkmak sırada](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi, çıkmak için başka bir yol sağlayabilir bir `While` döngü.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="f0fbe-138">`Exit While` Denetim takip eden deyime hemen aktarır `End While` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="f0fbe-139">Tipik olarak kullandığınız `Exit While` bazı koşullar değerlendirildikten sonra (örneğin, bir `If...Then...Else` yapısı).</span><span class="sxs-lookup"><span data-stu-id="f0fbe-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="f0fbe-140">Gereksiz veya hatalı bir değer veya bir sonlandırma isteği gibi yineleme devam etmek mümkün kılan bir koşul algılama bir döngüden çıkma isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="f0fbe-141">Kullanabileceğiniz `Exit While` test ettiğinizde, neden olabilecek bir koşul için bir *sonsuz bir döngüye*, bir son derece büyük veya hatta sonsuz sayıda çalıştırabileceğiniz bir döngü olduğu.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="f0fbe-142">Ardından `Exit While` döngüden çıkma.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="f0fbe-143">Herhangi bir sayıda yerleştirebilirsiniz `Exit While` herhangi bir yere deyimleri `While` döngü.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="f0fbe-144">Kullanıldığında içinde iç içe geçmiş `While` döngüleri `Exit While` denetimi iç döngü dışında ve iç içe geçme daha yüksek düzeydeki içine aktarır.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="f0fbe-145">`Continue While` Deyime hemen denetimi döngünün sonraki yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="f0fbe-146">Daha fazla bilgi için [Continue deyimi](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0fbe-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0fbe-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0fbe-147">Example</span></span>  
 <span data-ttu-id="f0fbe-148">Aşağıdaki örnekte, Döngüdeki deyimler kadar çalışmaya devam `index` değişkendir 10'dan büyük.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="f0fbe-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0fbe-149">Example</span></span>  
 <span data-ttu-id="f0fbe-150">Aşağıdaki örnek, kullanımını gösterir `Continue While` ve `Exit While` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="f0fbe-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0fbe-151">Example</span></span>  
 <span data-ttu-id="f0fbe-152">Aşağıdaki örnek, bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="f0fbe-153"><xref:System.IO.File.OpenText%2A> Yöntemi dosyayı açar ve döndüren bir <xref:System.IO.StreamReader> , bir karakter okur.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="f0fbe-154">İçinde `While` koşulu <xref:System.IO.StreamReader.Peek%2A> yöntemi `StreamReader` dosya ek karakterler içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="f0fbe-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0fbe-155">See also</span></span>
- [<span data-ttu-id="f0fbe-156">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="f0fbe-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="f0fbe-157">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="f0fbe-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="f0fbe-158">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="f0fbe-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="f0fbe-159">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f0fbe-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="f0fbe-160">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="f0fbe-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="f0fbe-161">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="f0fbe-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="f0fbe-162">Continue Deyimi</span><span class="sxs-lookup"><span data-stu-id="f0fbe-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)

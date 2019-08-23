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
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965806"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="0d9c9-102">While...End While Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d9c9-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="0d9c9-103">Belirli bir koşul olduğu `True`sürece bir dizi deyim çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d9c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d9c9-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="0d9c9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0d9c9-105">Parts</span></span>  
  
|<span data-ttu-id="0d9c9-106">Terim</span><span class="sxs-lookup"><span data-stu-id="0d9c9-106">Term</span></span>|<span data-ttu-id="0d9c9-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="0d9c9-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="0d9c9-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-108">Required.</span></span> <span data-ttu-id="0d9c9-109">`Boolean`ifadesini.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-109">`Boolean` expression.</span></span> <span data-ttu-id="0d9c9-110">İse, Visual Basic olduğu gibi `False`davranır. `Nothing` `condition`</span><span class="sxs-lookup"><span data-stu-id="0d9c9-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="0d9c9-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-111">Optional.</span></span> <span data-ttu-id="0d9c9-112">Aşağıdaki `While` `condition` her`True`seferinde çalıştırılan bir veya daha fazla deyim.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="0d9c9-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-113">Optional.</span></span> <span data-ttu-id="0d9c9-114">Denetimi `While` bloğun bir sonraki yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="0d9c9-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-115">Optional.</span></span> <span data-ttu-id="0d9c9-116">Denetimi `While` bloğunun dışına aktarır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="0d9c9-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-117">Required.</span></span> <span data-ttu-id="0d9c9-118">`While` Bloğunun tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d9c9-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d9c9-119">Remarks</span></span>  
 <span data-ttu-id="0d9c9-120">Bir koşul `While...End While` , bir koşulun kaldığı `True`sürece belirsiz sayıda deyim yinelemek istediğinizde bir yapı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="0d9c9-121">Koşulu test ettiğiniz veya ne sonuçla test ettiğiniz hakkında daha fazla esneklik istiyorsanız [Do... seçeneğini tercih edebilirsiniz. Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0d9c9-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="0d9c9-122">Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d9c9-123">`While` Anahtar sözcüğü de [Do... içinde kullanılır. Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While yan tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md) ve [Take While yan tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0d9c9-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="0d9c9-124">İse, `End While` deyimle karşılaşana kadar tüm `statements`çalıştırmayasahipolur. `condition` `True`</span><span class="sxs-lookup"><span data-stu-id="0d9c9-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="0d9c9-125">Sonra Denetim `While` ifadeye döner ve `condition` tekrar denetlenir.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="0d9c9-126">`condition` Hala`True`varsa, işlem tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="0d9c9-127">Eğer ise denetim, `End While` ifadesiyle takip eden deyime geçer. `False`</span><span class="sxs-lookup"><span data-stu-id="0d9c9-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="0d9c9-128">`While` İfade, döngüyü başlamadan önce her zaman koşulu denetler.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="0d9c9-129">Durum, koşul kaldığı `True`sürece devam eder.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="0d9c9-130">`condition` Döngüyüilkkezgirdiğinizde,`False` bir kez daha çalışır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="0d9c9-131">Genellikle iki değerin karşılaştırılmasının sonuçları, ancak [Boolean veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`) olarak değerlendirilen herhangi bir ifade olabilir. `condition`</span><span class="sxs-lookup"><span data-stu-id="0d9c9-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="0d9c9-132">Bu ifade, olarak dönüştürülmüş `Boolean`bir sayısal tür gibi başka bir veri türünün değerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="0d9c9-133">Bir döngüyü diğerinin `While` içine yerleştirerek iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="0d9c9-134">Ayrıca, farklı türlerde denetim yapılarını bir diğeri içinde iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="0d9c9-135">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="0d9c9-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="0d9c9-136">Çıkış sırasında çıkış</span><span class="sxs-lookup"><span data-stu-id="0d9c9-136">Exit While</span></span>  
 <span data-ttu-id="0d9c9-137">[Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri, bir `While` döngüden çıkmak için başka bir yol sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="0d9c9-138">`Exit While`, `End While` denetimi hemen takip eden deyime aktarır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="0d9c9-139">Genellikle bir koşul `Exit While` hesaplandıktan sonra (örneğin, bir `If...Then...Else` yapıda) kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="0d9c9-140">Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="0d9c9-141">Sonsuz döngüye neden `Exit While` olabilecek bir koşul için test ettiğinizde kullanabilirsiniz. Bu,son derece büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="0d9c9-142">Ardından, döngüyü atlamak `Exit While` için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="0d9c9-143">Döngüde herhangi bir yere herhangi bir `Exit While` sayıda deyim yerleştirebilirsiniz. `While`</span><span class="sxs-lookup"><span data-stu-id="0d9c9-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="0d9c9-144">İç içe `While` döngüler içinde kullanıldığında, `Exit While` denetimi en içteki döngünün dışına ve sonraki yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="0d9c9-145">`Continue While` Ekstre, denetimi hemen döngüsünün bir sonraki yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="0d9c9-146">Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0d9c9-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d9c9-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d9c9-147">Example</span></span>  
 <span data-ttu-id="0d9c9-148">Aşağıdaki örnekte, döngü içindeki deyimler, `index` değişken 10 ' dan büyük olana kadar çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="0d9c9-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d9c9-149">Example</span></span>  
 <span data-ttu-id="0d9c9-150">Aşağıdaki örnek, `Continue While` ve `Exit While` deyimlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="0d9c9-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d9c9-151">Example</span></span>  
 <span data-ttu-id="0d9c9-152">Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="0d9c9-153">Yöntemi dosyayı açar ve karakterleri okuyan bir <xref:System.IO.StreamReader> döndürür. <xref:System.IO.File.OpenText%2A></span><span class="sxs-lookup"><span data-stu-id="0d9c9-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="0d9c9-154">Koşulunda, öğesinin`StreamReader` yöntemi dosyanın ek karakterler içerip içermediğini belirler. <xref:System.IO.StreamReader.Peek%2A> `While`</span><span class="sxs-lookup"><span data-stu-id="0d9c9-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="0d9c9-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d9c9-155">See also</span></span>

- [<span data-ttu-id="0d9c9-156">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="0d9c9-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="0d9c9-157">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="0d9c9-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="0d9c9-158">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="0d9c9-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="0d9c9-159">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0d9c9-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="0d9c9-160">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="0d9c9-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="0d9c9-161">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="0d9c9-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="0d9c9-162">Continue Deyimi</span><span class="sxs-lookup"><span data-stu-id="0d9c9-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)

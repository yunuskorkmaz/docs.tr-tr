---
title: While...End While Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 87f6fbd6147b6dbfbe08c93e862d58b9868f9201
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352745"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="7294f-102">While...End While Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7294f-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="7294f-103">Belirli bir koşul `True`olduğu sürece bir dizi deyim çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7294f-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7294f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7294f-104">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="7294f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7294f-105">Parts</span></span>  
  
|<span data-ttu-id="7294f-106">Terim</span><span class="sxs-lookup"><span data-stu-id="7294f-106">Term</span></span>|<span data-ttu-id="7294f-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="7294f-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="7294f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7294f-108">Required.</span></span> <span data-ttu-id="7294f-109">`Boolean` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="7294f-109">`Boolean` expression.</span></span> <span data-ttu-id="7294f-110">`condition` `Nothing`, Visual Basic `False`olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7294f-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="7294f-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7294f-111">Optional.</span></span> <span data-ttu-id="7294f-112">`While`aşağıdaki `condition` her seferinde çalışan bir veya daha fazla deyim `True`.</span><span class="sxs-lookup"><span data-stu-id="7294f-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="7294f-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7294f-113">Optional.</span></span> <span data-ttu-id="7294f-114">Denetimi `While` bloğunun bir sonraki yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="7294f-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="7294f-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7294f-115">Optional.</span></span> <span data-ttu-id="7294f-116">`While` bloğunun denetimini aktarır.</span><span class="sxs-lookup"><span data-stu-id="7294f-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="7294f-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7294f-117">Required.</span></span> <span data-ttu-id="7294f-118">`While` bloğunun tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="7294f-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7294f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7294f-119">Remarks</span></span>  
 <span data-ttu-id="7294f-120">Bir koşulun bir kümesini sınırsız sayıda yinelemek istediğinizde, bir koşul `True`kaldığı sürece bir `While...End While` yapısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7294f-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="7294f-121">Koşulu test ettiğiniz veya ne sonuçla test ettiğiniz hakkında daha fazla esneklik istiyorsanız [Do... seçeneğini tercih edebilirsiniz. Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7294f-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="7294f-122">Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="7294f-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7294f-123">`While` anahtar sözcüğü de [Do... içinde kullanılır. Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While yan tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md) ve [Take While yan tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7294f-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="7294f-124">`condition` `True`, `statements` `End While` ifadesiyle karşılaşana kadar çalışır.</span><span class="sxs-lookup"><span data-stu-id="7294f-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="7294f-125">Sonra Denetim `While` ifadeye döner ve `condition` yeniden denetlenir.</span><span class="sxs-lookup"><span data-stu-id="7294f-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="7294f-126">`condition` hala `True`, işlem tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="7294f-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="7294f-127">`False`, denetim `End While` bildirisini izleyen ifadeye geçer.</span><span class="sxs-lookup"><span data-stu-id="7294f-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="7294f-128">`While` ifade, döngüyü başlamadan önce her zaman koşulu kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="7294f-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="7294f-129">Koşul `True`kaldığı sürece döngü devam eder.</span><span class="sxs-lookup"><span data-stu-id="7294f-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="7294f-130">Döngüyü ilk girdiğinizde `condition` `False` bir kez çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="7294f-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="7294f-131">`condition` genellikle iki değerin karşılaştırılmasının sonucunu verir, ancak [Boolean veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`) değerlendirilen herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="7294f-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="7294f-132">Bu ifade, `Boolean`dönüştürülmüş bir sayısal tür gibi başka bir veri türünün değerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7294f-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="7294f-133">Bir döngüyü diğerinin içine yerleştirerek `While` döngüleri iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7294f-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="7294f-134">Ayrıca, farklı türlerde denetim yapılarını bir diğeri içinde iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7294f-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="7294f-135">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="7294f-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="7294f-136">Çıkış sırasında çıkış</span><span class="sxs-lookup"><span data-stu-id="7294f-136">Exit While</span></span>  
 <span data-ttu-id="7294f-137">[Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri `While` döngüsünden çıkmak için başka bir yol sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7294f-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="7294f-138">`Exit While`, denetimi hemen `End While` bildirisini izleyen deyime aktarır.</span><span class="sxs-lookup"><span data-stu-id="7294f-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="7294f-139">Genellikle `Exit While` bir koşul hesaplandıktan sonra (örneğin, bir `If...Then...Else` yapısında) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7294f-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="7294f-140">Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7294f-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="7294f-141">Sonsuz *döngüye*neden olabilecek bir durum için test ettiğinizde `Exit While` kullanabilirsiniz. Bu, son derece büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür.</span><span class="sxs-lookup"><span data-stu-id="7294f-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="7294f-142">Sonra döngüyü atlamak için `Exit While` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7294f-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="7294f-143">Herhangi bir sayıda `Exit While` deyimi `While` döngüsünde yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7294f-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="7294f-144">İç içe geçmiş `While` döngüleri içinde kullanıldığında, `Exit While` denetimi en içteki döngüden ve sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="7294f-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="7294f-145">`Continue While` deyimleri, denetimi hemen döngüsünün bir sonraki yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="7294f-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="7294f-146">Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7294f-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7294f-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="7294f-147">Example</span></span>  
 <span data-ttu-id="7294f-148">Aşağıdaki örnekte, döngü içindeki deyimler `index` değişkeni 10 ' dan büyük olana kadar çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="7294f-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="7294f-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="7294f-149">Example</span></span>  
 <span data-ttu-id="7294f-150">Aşağıdaki örnekte `Continue While` ve `Exit While` deyimlerinin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7294f-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="7294f-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="7294f-151">Example</span></span>  
 <span data-ttu-id="7294f-152">Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="7294f-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="7294f-153"><xref:System.IO.File.OpenText%2A> yöntemi dosyayı açar ve karakterleri okuyan bir <xref:System.IO.StreamReader> döndürür.</span><span class="sxs-lookup"><span data-stu-id="7294f-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="7294f-154">`While` koşulunda, `StreamReader` <xref:System.IO.StreamReader.Peek%2A> yöntemi dosyanın ek karakterler içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="7294f-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="7294f-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7294f-155">See also</span></span>

- [<span data-ttu-id="7294f-156">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="7294f-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="7294f-157">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="7294f-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="7294f-158">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="7294f-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="7294f-159">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7294f-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="7294f-160">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="7294f-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="7294f-161">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="7294f-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="7294f-162">Continue Deyimi</span><span class="sxs-lookup"><span data-stu-id="7294f-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)

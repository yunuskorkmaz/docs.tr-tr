---
description: 'Hakkında daha fazla bilgi edinin: while... End while (Visual Basic) ekstresi'
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
ms.openlocfilehash: ab452e2d9446c9c44b952c6ebf026f7a6f9080cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787584"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="ec1d3-103">While...End While Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec1d3-103">While...End While Statement (Visual Basic)</span></span>

<span data-ttu-id="ec1d3-104">Belirli bir koşul olduğu sürece bir dizi deyim çalıştırır `True` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-104">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec1d3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec1d3-105">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="ec1d3-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ec1d3-106">Parts</span></span>  
  
|<span data-ttu-id="ec1d3-107">Süre</span><span class="sxs-lookup"><span data-stu-id="ec1d3-107">Term</span></span>|<span data-ttu-id="ec1d3-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="ec1d3-108">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="ec1d3-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-109">Required.</span></span> <span data-ttu-id="ec1d3-110">`Boolean` ifadesini.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-110">`Boolean` expression.</span></span> <span data-ttu-id="ec1d3-111">İse `condition` `Nothing` , Visual Basic olduğu gibi davranır `False` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-111">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="ec1d3-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-112">Optional.</span></span> <span data-ttu-id="ec1d3-113">Aşağıdaki her seferinde çalıştırılan bir veya daha fazla deyim `While` `condition` `True` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-113">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="ec1d3-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-114">Optional.</span></span> <span data-ttu-id="ec1d3-115">Denetimi bloğun bir sonraki yinelemesine aktarır `While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-115">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="ec1d3-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-116">Optional.</span></span> <span data-ttu-id="ec1d3-117">Denetimi bloğunun dışına aktarır `While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-117">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="ec1d3-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-118">Required.</span></span> <span data-ttu-id="ec1d3-119">Bloğunun tanımını sonlandırır `While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-119">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec1d3-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec1d3-120">Remarks</span></span>  

 <span data-ttu-id="ec1d3-121">Bir `While...End While` koşul, bir koşulun kaldığı sürece belirsiz sayıda deyim yinelemek istediğinizde bir yapı kullanın `True` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-121">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="ec1d3-122">Koşulu test ettiğiniz veya ne sonuçla test ettiğiniz hakkında daha fazla esneklik istiyorsanız [Do... seçeneğini tercih edebilirsiniz. Loop deyimleri](do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ec1d3-122">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](do-loop-statement.md).</span></span> <span data-ttu-id="ec1d3-123">Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-123">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec1d3-124">`While`Anahtar sözcüğü de [Do... içinde kullanılır. Loop deyimi](do-loop-statement.md), [Skip While yan tümcesi](../queries/skip-while-clause.md) ve [Take While yan tümcesi](../queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ec1d3-124">The `While` keyword is also used in the [Do...Loop Statement](do-loop-statement.md), the [Skip While Clause](../queries/skip-while-clause.md) and the [Take While Clause](../queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="ec1d3-125">İse `condition` , `True` `statements` deyimle karşılaşana kadar tüm çalıştırmaya sahip olur `End While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-125">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="ec1d3-126">Sonra Denetim `While` ifadeye döner ve `condition` tekrar denetlenir.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-126">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="ec1d3-127">`condition`Hala varsa `True` , işlem tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-127">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="ec1d3-128">Eğer ise `False` Denetim, ifadesiyle takip eden deyime geçer `End While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-128">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="ec1d3-129">`While`İfade, döngüyü başlamadan önce her zaman koşulu denetler.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-129">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="ec1d3-130">Durum, koşul kaldığı sürece devam eder `True` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-130">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="ec1d3-131">`condition` `False` Döngüyü ilk kez girdiğinizde, bir kez daha çalışır.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-131">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="ec1d3-132">`condition`Genellikle iki değerin karşılaştırılmasının sonuçları, ancak [Boolean veri türü](../data-types/boolean-data-type.md) değeri (veya) olarak değerlendirilen herhangi bir ifade olabilir `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-132">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="ec1d3-133">Bu ifade, olarak dönüştürülmüş bir sayısal tür gibi başka bir veri türünün değerini içerebilir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-133">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="ec1d3-134">Bir `While` döngüyü diğerinin içine yerleştirerek iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-134">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="ec1d3-135">Ayrıca, farklı türlerde denetim yapılarını bir diğeri içinde iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-135">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="ec1d3-136">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="ec1d3-136">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="ec1d3-137">Çıkış sırasında çıkış</span><span class="sxs-lookup"><span data-stu-id="ec1d3-137">Exit While</span></span>  

 <span data-ttu-id="ec1d3-138">[Exit While](exit-statement.md) deyimleri, bir döngüden çıkmak için başka bir yol sağlayabilir `While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-138">The [Exit While](exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="ec1d3-139">`Exit While` , denetimi hemen takip eden deyime aktarır `End While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-139">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="ec1d3-140">Genellikle `Exit While` bir koşul hesaplandıktan sonra (örneğin, bir `If...Then...Else` yapıda) kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-140">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="ec1d3-141">Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-141">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="ec1d3-142">Sonsuz `Exit While` *döngüye* neden olabilecek bir koşul için test ettiğinizde kullanabilirsiniz. Bu, son derece büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-142">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="ec1d3-143">Ardından, `Exit While` döngüyü atlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-143">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="ec1d3-144">`Exit While`Döngüde herhangi bir yere herhangi bir sayıda deyim yerleştirebilirsiniz `While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-144">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="ec1d3-145">İç içe döngüler içinde kullanıldığında `While` , `Exit While` denetimi en içteki döngünün dışına ve sonraki yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-145">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="ec1d3-146">`Continue While`Ekstre, denetimi hemen döngüsünün bir sonraki yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-146">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="ec1d3-147">Daha fazla bilgi için bkz. [Continue bildirisi](continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ec1d3-147">For more information, see [Continue Statement](continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec1d3-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec1d3-148">Example</span></span>  

 <span data-ttu-id="ec1d3-149">Aşağıdaki örnekte, döngü içindeki deyimler, değişken 10 ' dan büyük olana kadar çalışmaya devam eder `index` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="ec1d3-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec1d3-150">Example</span></span>  

 <span data-ttu-id="ec1d3-151">Aşağıdaki örnek, `Continue While` ve deyimlerinin kullanımını gösterir `Exit While` .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-151">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="ec1d3-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec1d3-152">Example</span></span>  

 <span data-ttu-id="ec1d3-153">Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-153">The following example reads all lines in a text file.</span></span> <span data-ttu-id="ec1d3-154"><xref:System.IO.File.OpenText%2A>Yöntemi dosyayı açar ve karakterleri okuyan bir döndürür <xref:System.IO.StreamReader> .</span><span class="sxs-lookup"><span data-stu-id="ec1d3-154">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="ec1d3-155">Koşulunda, `While` <xref:System.IO.StreamReader.Peek%2A> öğesinin yöntemi `StreamReader` dosyanın ek karakterler içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-155">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="ec1d3-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec1d3-156">See also</span></span>

- [<span data-ttu-id="ec1d3-157">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="ec1d3-157">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="ec1d3-158">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec1d3-158">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="ec1d3-159">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec1d3-159">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="ec1d3-160">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ec1d3-160">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="ec1d3-161">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="ec1d3-161">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="ec1d3-162">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec1d3-162">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="ec1d3-163">Continue Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec1d3-163">Continue Statement</span></span>](continue-statement.md)

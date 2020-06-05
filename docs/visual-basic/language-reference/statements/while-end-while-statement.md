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
ms.openlocfilehash: d9eb8cb95d46e860aa127954d7b44e37991d4a13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391592"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="bc560-102">While...End While Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc560-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="bc560-103">Belirli bir koşul olduğu sürece bir dizi deyim çalıştırır `True` .</span><span class="sxs-lookup"><span data-stu-id="bc560-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc560-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc560-104">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="bc560-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="bc560-105">Parts</span></span>  
  
|<span data-ttu-id="bc560-106">Terim</span><span class="sxs-lookup"><span data-stu-id="bc560-106">Term</span></span>|<span data-ttu-id="bc560-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="bc560-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="bc560-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc560-108">Required.</span></span> <span data-ttu-id="bc560-109">`Boolean`ifadesini.</span><span class="sxs-lookup"><span data-stu-id="bc560-109">`Boolean` expression.</span></span> <span data-ttu-id="bc560-110">İse `condition` `Nothing` , Visual Basic olduğu gibi davranır `False` .</span><span class="sxs-lookup"><span data-stu-id="bc560-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="bc560-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bc560-111">Optional.</span></span> <span data-ttu-id="bc560-112">Aşağıdaki her seferinde çalıştırılan bir veya daha fazla deyim `While` `condition` `True` .</span><span class="sxs-lookup"><span data-stu-id="bc560-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="bc560-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bc560-113">Optional.</span></span> <span data-ttu-id="bc560-114">Denetimi bloğun bir sonraki yinelemesine aktarır `While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="bc560-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bc560-115">Optional.</span></span> <span data-ttu-id="bc560-116">Denetimi bloğunun dışına aktarır `While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="bc560-117">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc560-117">Required.</span></span> <span data-ttu-id="bc560-118">Bloğunun tanımını sonlandırır `While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc560-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc560-119">Remarks</span></span>  
 <span data-ttu-id="bc560-120">Bir `While...End While` koşul, bir koşulun kaldığı sürece belirsiz sayıda deyim yinelemek istediğinizde bir yapı kullanın `True` .</span><span class="sxs-lookup"><span data-stu-id="bc560-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="bc560-121">Koşulu test ettiğiniz veya ne sonuçla test ettiğiniz hakkında daha fazla esneklik istiyorsanız [Do... seçeneğini tercih edebilirsiniz. Loop deyimleri](do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bc560-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](do-loop-statement.md).</span></span> <span data-ttu-id="bc560-122">Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="bc560-122">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc560-123">`While`Anahtar sözcüğü de [Do... içinde kullanılır. Loop deyimi](do-loop-statement.md), [Skip While yan tümcesi](../queries/skip-while-clause.md) ve [Take While yan tümcesi](../queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bc560-123">The `While` keyword is also used in the [Do...Loop Statement](do-loop-statement.md), the [Skip While Clause](../queries/skip-while-clause.md) and the [Take While Clause](../queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="bc560-124">İse `condition` , `True` `statements` deyimle karşılaşana kadar tüm çalıştırmaya sahip olur `End While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="bc560-125">Sonra Denetim `While` ifadeye döner ve `condition` tekrar denetlenir.</span><span class="sxs-lookup"><span data-stu-id="bc560-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="bc560-126">`condition`Hala varsa `True` , işlem tekrarlanır.</span><span class="sxs-lookup"><span data-stu-id="bc560-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="bc560-127">Eğer ise `False` Denetim, ifadesiyle takip eden deyime geçer `End While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="bc560-128">`While`İfade, döngüyü başlamadan önce her zaman koşulu denetler.</span><span class="sxs-lookup"><span data-stu-id="bc560-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="bc560-129">Durum, koşul kaldığı sürece devam eder `True` .</span><span class="sxs-lookup"><span data-stu-id="bc560-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="bc560-130">`condition` `False` Döngüyü ilk kez girdiğinizde, bir kez daha çalışır.</span><span class="sxs-lookup"><span data-stu-id="bc560-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="bc560-131">`condition`Genellikle iki değerin karşılaştırılmasının sonuçları, ancak [Boolean veri türü](../data-types/boolean-data-type.md) değeri (veya) olarak değerlendirilen herhangi bir ifade olabilir `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="bc560-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="bc560-132">Bu ifade, olarak dönüştürülmüş bir sayısal tür gibi başka bir veri türünün değerini içerebilir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="bc560-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="bc560-133">Bir `While` döngüyü diğerinin içine yerleştirerek iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc560-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="bc560-134">Ayrıca, farklı türlerde denetim yapılarını bir diğeri içinde iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc560-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="bc560-135">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="bc560-135">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="bc560-136">Çıkış sırasında çıkış</span><span class="sxs-lookup"><span data-stu-id="bc560-136">Exit While</span></span>  
 <span data-ttu-id="bc560-137">[Exit While](exit-statement.md) deyimleri, bir döngüden çıkmak için başka bir yol sağlayabilir `While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-137">The [Exit While](exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="bc560-138">`Exit While`, denetimi hemen takip eden deyime aktarır `End While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="bc560-139">Genellikle `Exit While` bir koşul hesaplandıktan sonra (örneğin, bir `If...Then...Else` yapıda) kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bc560-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="bc560-140">Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc560-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="bc560-141">Sonsuz `Exit While` *döngüye*neden olabilecek bir koşul için test ettiğinizde kullanabilirsiniz. Bu, son derece büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür.</span><span class="sxs-lookup"><span data-stu-id="bc560-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="bc560-142">Ardından, `Exit While` döngüyü atlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc560-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="bc560-143">`Exit While`Döngüde herhangi bir yere herhangi bir sayıda deyim yerleştirebilirsiniz `While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="bc560-144">İç içe döngüler içinde kullanıldığında `While` , `Exit While` denetimi en içteki döngünün dışına ve sonraki yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="bc560-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="bc560-145">`Continue While`Ekstre, denetimi hemen döngüsünün bir sonraki yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="bc560-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="bc560-146">Daha fazla bilgi için bkz. [Continue bildirisi](continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bc560-146">For more information, see [Continue Statement](continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc560-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc560-147">Example</span></span>  
 <span data-ttu-id="bc560-148">Aşağıdaki örnekte, döngü içindeki deyimler, değişken 10 ' dan büyük olana kadar çalışmaya devam eder `index` .</span><span class="sxs-lookup"><span data-stu-id="bc560-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="bc560-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc560-149">Example</span></span>  
 <span data-ttu-id="bc560-150">Aşağıdaki örnek, `Continue While` ve deyimlerinin kullanımını gösterir `Exit While` .</span><span class="sxs-lookup"><span data-stu-id="bc560-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="bc560-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc560-151">Example</span></span>  
 <span data-ttu-id="bc560-152">Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="bc560-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="bc560-153"><xref:System.IO.File.OpenText%2A>Yöntemi dosyayı açar ve karakterleri okuyan bir döndürür <xref:System.IO.StreamReader> .</span><span class="sxs-lookup"><span data-stu-id="bc560-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="bc560-154">Koşulunda, `While` <xref:System.IO.StreamReader.Peek%2A> öğesinin yöntemi `StreamReader` dosyanın ek karakterler içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bc560-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="bc560-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc560-155">See also</span></span>

- [<span data-ttu-id="bc560-156">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="bc560-156">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="bc560-157">Do...Loop Deyimi</span><span class="sxs-lookup"><span data-stu-id="bc560-157">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="bc560-158">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="bc560-158">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="bc560-159">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="bc560-159">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="bc560-160">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="bc560-160">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="bc560-161">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="bc560-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="bc560-162">Continue bildirisi</span><span class="sxs-lookup"><span data-stu-id="bc560-162">Continue Statement</span></span>](continue-statement.md)

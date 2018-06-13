---
title: Do...Loop Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: e12cdc1ae405b877d4d27d1947c98dcb51938ba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604945"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="e205d-102">Do...Loop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e205d-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="e205d-103">While deyimleri bloğunu yinelenen bir `Boolean` koşul `True` veya koşul olana kadar `True`.</span><span class="sxs-lookup"><span data-stu-id="e205d-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e205d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e205d-104">Syntax</span></span>  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="e205d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e205d-105">Parts</span></span>  
  
|<span data-ttu-id="e205d-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e205d-106">Term</span></span>|<span data-ttu-id="e205d-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e205d-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="e205d-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e205d-108">Required.</span></span> <span data-ttu-id="e205d-109">Tanımını başlatır `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="e205d-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="e205d-110">Sürece gerekli `Until` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e205d-110">Required unless `Until` is used.</span></span> <span data-ttu-id="e205d-111">Döngüyü kadar `condition` olan `False`.</span><span class="sxs-lookup"><span data-stu-id="e205d-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="e205d-112">Sürece gerekli `While` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e205d-112">Required unless `While` is used.</span></span> <span data-ttu-id="e205d-113">Döngüyü kadar `condition` olan `True`.</span><span class="sxs-lookup"><span data-stu-id="e205d-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="e205d-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e205d-114">Optional.</span></span> <span data-ttu-id="e205d-115">`Boolean` İfade.</span><span class="sxs-lookup"><span data-stu-id="e205d-115">`Boolean` expression.</span></span> <span data-ttu-id="e205d-116">Varsa `condition` olan `Nothing`, Visual Basic da işler `False`.</span><span class="sxs-lookup"><span data-stu-id="e205d-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="e205d-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e205d-117">Optional.</span></span> <span data-ttu-id="e205d-118">Sırasında veya kadar yinelenen bir veya daha fazla deyimleri `condition` olan `True`.</span><span class="sxs-lookup"><span data-stu-id="e205d-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="e205d-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e205d-119">Optional.</span></span> <span data-ttu-id="e205d-120">Sonraki yinelemesini denetim aktarır `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="e205d-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="e205d-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e205d-121">Optional.</span></span> <span data-ttu-id="e205d-122">Denetimin dışarı aktarır `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="e205d-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="e205d-123">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e205d-123">Required.</span></span> <span data-ttu-id="e205d-124">Tanımını sonlandırır `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="e205d-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e205d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e205d-125">Remarks</span></span>  
 <span data-ttu-id="e205d-126">Kullanım bir `Do...Loop` yapısı belirsiz numarası bir deyimleri bir koşul sağlanırsa kadar kaç kez, bir dizi yineleyin istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="e205d-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="e205d-127">İfadeler kümesi birkaç kez yineleyin istiyorsanız [için... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="e205d-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="e205d-128">Kullanabilirsiniz `While` veya `Until` belirtmek için `condition`, ancak ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="e205d-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="e205d-129">Test edebilirsiniz `condition` başlangıç veya döngüsünün sonuna yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="e205d-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="e205d-130">Test ederseniz `condition` döngü başlangıcında (içinde `Do` deyimi), döngü bile bir kez çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e205d-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="e205d-131">Döngü sonunda test ederseniz (içinde `Loop` deyimi), döngünün her zaman en az bir kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="e205d-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="e205d-132">Koşul genellikle iki değer karşılaştırmadan olur, ancak veren herhangi bir ifade olabilir bir [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`).</span><span class="sxs-lookup"><span data-stu-id="e205d-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="e205d-133">Bu değerleri için dönüştürülen sayısal türler gibi diğer veri türleri içerir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e205d-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="e205d-134">Geçirebilmenize `Do` döngüler içinde başka bir döngü koyarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e205d-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="e205d-135">Ayrıca, değişik birbirine içindeki denetim yapıları yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e205d-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="e205d-136">Daha fazla bilgi için bkz: [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="e205d-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e205d-137">`Do...Loop` Yapısı size daha fazla esneklik [sırada... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , döngü sona erdirmek karar vermek sağladığından, `condition` olan durdurur `True` veya zaman ilk olacağını `True`.</span><span class="sxs-lookup"><span data-stu-id="e205d-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="e205d-138">Ayrıca, test etmek sağlar `condition` başlangıç veya döngüsü sonu.</span><span class="sxs-lookup"><span data-stu-id="e205d-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="e205d-139">Çık</span><span class="sxs-lookup"><span data-stu-id="e205d-139">Exit Do</span></span>  
 <span data-ttu-id="e205d-140">[Çıkış yapmak](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi, çıkmak için alternatif bir yol sağlayabilir bir `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="e205d-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="e205d-141">`Exit Do` aşağıdaki deyim denetimi hemen aktarır `Loop` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e205d-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="e205d-142">`Exit Do` Bazı koşul örnekte değerlendirildikten sonra sık kullanılan bir `If...Then...Else` yapısı.</span><span class="sxs-lookup"><span data-stu-id="e205d-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="e205d-143">Gereksiz veya hatalı bir değer veya bir sonlandırma isteği gibi yineleme devam mümkün kılan bir koşul algılama döngü çıkmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e205d-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="e205d-144">Bir kullanımını `Exit Do` neden olabilecek bir koşulu sınamak için bir *sonsuz bir döngüde*, bir büyük veya hatta sonsuz sayıda çalışacak bir döngü değil.</span><span class="sxs-lookup"><span data-stu-id="e205d-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="e205d-145">Kullanabileceğiniz `Exit Do` döngü kaçınmak için.</span><span class="sxs-lookup"><span data-stu-id="e205d-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="e205d-146">Herhangi bir sayıda içerebilir `Exit Do` deyimlerinde herhangi bir yerden bir `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="e205d-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="e205d-147">Kullanıldığında içinde iç içe geçmiş `Do` döngüler, `Exit Do` denetimi en içteki döngü dışında ve iç içe geçme sonraki daha yüksek düzeyde uygulamasına aktarır.</span><span class="sxs-lookup"><span data-stu-id="e205d-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e205d-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="e205d-148">Example</span></span>  
 <span data-ttu-id="e205d-149">Aşağıdaki örnekte, döngü deyimlerinde kadar çalışmaya devam `index` değişkenidir 10'dan büyük.</span><span class="sxs-lookup"><span data-stu-id="e205d-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="e205d-150">`Until` Yan tümcesi olan döngü sonunda.</span><span class="sxs-lookup"><span data-stu-id="e205d-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e205d-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="e205d-151">Example</span></span>  
 <span data-ttu-id="e205d-152">Aşağıdaki örnek kullanan bir `While` yan tümcesi yerine bir `Until` yan tümcesi ve `condition` yerine döngü sonunda başlangıcında test.</span><span class="sxs-lookup"><span data-stu-id="e205d-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="e205d-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="e205d-153">Example</span></span>  
 <span data-ttu-id="e205d-154">Aşağıdaki örnekte, `condition` döngü durur zaman `index` değişkenidir 100'den büyük.</span><span class="sxs-lookup"><span data-stu-id="e205d-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="e205d-155">`If` Döngüdeki deyimi ancak neden `Exit Do` deyimi dizin değişken 10'dan büyük olduğunda döngü durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="e205d-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="e205d-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="e205d-156">Example</span></span>  
 <span data-ttu-id="e205d-157">Aşağıdaki örnek, bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="e205d-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="e205d-158"><xref:System.IO.File.OpenText%2A> Yöntemi dosyayı açar ve döndürür bir <xref:System.IO.StreamReader> karakterleri okur.</span><span class="sxs-lookup"><span data-stu-id="e205d-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="e205d-159">İçinde `Do...Loop` koşulu <xref:System.IO.StreamReader.Peek%2A> yöntemi `StreamReader` herhangi bir ek karakter olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="e205d-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e205d-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e205d-160">See Also</span></span>  
 [<span data-ttu-id="e205d-161">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="e205d-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="e205d-162">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="e205d-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="e205d-163">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e205d-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="e205d-164">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="e205d-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="e205d-165">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="e205d-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="e205d-166">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="e205d-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)

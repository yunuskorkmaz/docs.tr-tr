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
ms.openlocfilehash: 8c965dc89794654127e4b872c6aebf55c8902468
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525161"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="3fd57-102">Do...Loop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fd57-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="3fd57-103">Bir while deyimleri bloğunu bir `Boolean` koşul `True` veya koşulu olana kadar `True`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd57-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fd57-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="3fd57-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3fd57-105">Parts</span></span>  
  
|<span data-ttu-id="3fd57-106">Terim</span><span class="sxs-lookup"><span data-stu-id="3fd57-106">Term</span></span>|<span data-ttu-id="3fd57-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="3fd57-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="3fd57-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3fd57-108">Required.</span></span> <span data-ttu-id="3fd57-109">Tanımı başlar `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="3fd57-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="3fd57-110">Sürece gerekli `Until` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fd57-110">Required unless `Until` is used.</span></span> <span data-ttu-id="3fd57-111">Döngüyü kadar `condition` olduğu `False`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="3fd57-112">Sürece gerekli `While` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fd57-112">Required unless `While` is used.</span></span> <span data-ttu-id="3fd57-113">Döngüyü kadar `condition` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="3fd57-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3fd57-114">Optional.</span></span> <span data-ttu-id="3fd57-115">`Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="3fd57-115">`Boolean` expression.</span></span> <span data-ttu-id="3fd57-116">Varsa `condition` olduğu `Nothing`, Visual Basic bunu algılar `False`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="3fd57-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3fd57-117">Optional.</span></span> <span data-ttu-id="3fd57-118">Sırasında veya kadar yinelenen bir veya daha fazla deyimleri `condition` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="3fd57-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3fd57-119">Optional.</span></span> <span data-ttu-id="3fd57-120">Denetim bir sonraki yinelemesine aktarır `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="3fd57-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="3fd57-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3fd57-121">Optional.</span></span> <span data-ttu-id="3fd57-122">Dışı denetim aktarır `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="3fd57-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="3fd57-123">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3fd57-123">Required.</span></span> <span data-ttu-id="3fd57-124">Tanımını sonlandırır `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="3fd57-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fd57-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fd57-125">Remarks</span></span>  
 <span data-ttu-id="3fd57-126">Kullanım bir `Do...Loop` yapısı deyimleri belirsiz numarası bir kez, bir koşul sağlanana kadar bir dizi yinelemek istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="3fd57-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="3fd57-127">Bir kez sayıdaki deyimleri yinelemek istiyorsanız [için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="3fd57-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="3fd57-128">Kullanabilirsiniz `While` veya `Until` belirtmek için `condition`, ikisini birden belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="3fd57-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="3fd57-129">Test edebilirsiniz `condition` başlangıç veya bitiş döngünün yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="3fd57-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="3fd57-130">Test, `condition` döngünün başında (içinde `Do` deyimi), döngü bile bir kez çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fd57-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="3fd57-131">Döngü, sonunda test ederseniz (içinde `Loop` deyimi), döngü, her zaman en az bir kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="3fd57-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="3fd57-132">Koşul genellikle iki değer karşılaştırması sonuçları ancak olarak değerlendirilen herhangi bir ifade olabilir bir [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`).</span><span class="sxs-lookup"><span data-stu-id="3fd57-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="3fd57-133">Bu değerler için dönüştürülen sayısal türleri gibi diğer veri türleri içerir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="3fd57-134">İç içe yerleştirebilirsiniz `Do` içindeki başka bir döngü koyarak döngüleri.</span><span class="sxs-lookup"><span data-stu-id="3fd57-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="3fd57-135">Farklı türlerde denetim yapılarını birbirine içinde iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd57-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="3fd57-136">Daha fazla bilgi için [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="3fd57-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fd57-137">`Do...Loop` Yapısına göre daha fazla esneklik sağlar [sırada... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md) döngü sona karar olanak sağladığından, `condition` olmaktan çıkar `True` veya ne zaman ilk duruma `True`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="3fd57-138">Ayrıca, test etmek sağlar `condition` başlangıç veya bitiş döngünün.</span><span class="sxs-lookup"><span data-stu-id="3fd57-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="3fd57-139">Çıkış yapın</span><span class="sxs-lookup"><span data-stu-id="3fd57-139">Exit Do</span></span>  
 <span data-ttu-id="3fd57-140">[Çıkış yapın](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi, çıkmak için alternatif bir yol sağlayabilir bir `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="3fd57-141">`Exit Do` Denetim takip eden deyime hemen aktarır `Loop` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3fd57-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="3fd57-142">`Exit Do` Bazı koşullar örnekte değerlendirildikten sonra sık kullanılan bir `If...Then...Else` yapısı.</span><span class="sxs-lookup"><span data-stu-id="3fd57-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="3fd57-143">Gereksiz veya hatalı bir değer veya bir sonlandırma isteği gibi yineleme devam etmek mümkün kılan bir koşul algılama bir döngüden çıkma isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fd57-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="3fd57-144">Bir kullanımını `Exit Do` neden olabilecek bir koşulu sınamak için bir *sonsuz bir döngüye*, bir büyük veya hatta sonsuz sayıda çalıştırabileceğiniz bir döngü olduğu.</span><span class="sxs-lookup"><span data-stu-id="3fd57-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="3fd57-145">Kullanabileceğiniz `Exit Do` döngüden çıkma.</span><span class="sxs-lookup"><span data-stu-id="3fd57-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="3fd57-146">Herhangi bir sayıda içerebilir `Exit Do` deyimlerinde herhangi bir yerde bir `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="3fd57-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="3fd57-147">Kullanıldığında içinde iç içe geçmiş `Do` döngüleri `Exit Do` denetimi iç döngü dışında ve iç içe geçme daha yüksek düzeydeki içine aktarır.</span><span class="sxs-lookup"><span data-stu-id="3fd57-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fd57-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fd57-148">Example</span></span>  
 <span data-ttu-id="3fd57-149">Aşağıdaki örnekte, Döngüdeki deyimler kadar çalışmaya devam `index` değişkendir 10'dan büyük.</span><span class="sxs-lookup"><span data-stu-id="3fd57-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="3fd57-150">`Until` Yan tümcesi ise döngü sonunda.</span><span class="sxs-lookup"><span data-stu-id="3fd57-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="3fd57-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fd57-151">Example</span></span>  
 <span data-ttu-id="3fd57-152">Aşağıdaki örnekte bir `While` yan tümcesi yerine bir `Until` yan tümcesi ve `condition` sonunda yerine döngüsünün başında test edilir.</span><span class="sxs-lookup"><span data-stu-id="3fd57-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="3fd57-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fd57-153">Example</span></span>  
 <span data-ttu-id="3fd57-154">Aşağıdaki örnekte, `condition` döngü durdurur, `index` değişkendir 100'den büyük.</span><span class="sxs-lookup"><span data-stu-id="3fd57-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="3fd57-155">`If` Döngü deyimi ancak neden `Exit Do` döngüyü dizin değişkeni 10'dan büyük olduğunda durdurmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="3fd57-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="3fd57-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fd57-156">Example</span></span>  
 <span data-ttu-id="3fd57-157">Aşağıdaki örnek, bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="3fd57-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="3fd57-158"><xref:System.IO.File.OpenText%2A> Yöntemi dosyayı açar ve döndüren bir <xref:System.IO.StreamReader> , bir karakter okur.</span><span class="sxs-lookup"><span data-stu-id="3fd57-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="3fd57-159">İçinde `Do...Loop` koşulu <xref:System.IO.StreamReader.Peek%2A> yöntemi `StreamReader` herhangi bir ek karakter olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3fd57-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3fd57-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fd57-160">See also</span></span>
- [<span data-ttu-id="3fd57-161">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="3fd57-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="3fd57-162">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="3fd57-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3fd57-163">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3fd57-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="3fd57-164">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="3fd57-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="3fd57-165">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="3fd57-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="3fd57-166">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="3fd57-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)

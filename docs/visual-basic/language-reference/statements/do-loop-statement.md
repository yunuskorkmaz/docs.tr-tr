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
ms.openlocfilehash: eff5239e07ca27f40ece5af68f46c491be91cf09
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583437"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="bdf4d-102">Do...Loop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdf4d-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="bdf4d-103">Bir `Boolean` koşulu `True` veya koşul `True` hale gelinceye kadar bir deyim bloğunu yineler.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdf4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdf4d-104">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="bdf4d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="bdf4d-105">Parts</span></span>  
  
|<span data-ttu-id="bdf4d-106">Terim</span><span class="sxs-lookup"><span data-stu-id="bdf4d-106">Term</span></span>|<span data-ttu-id="bdf4d-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="bdf4d-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="bdf4d-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-108">Required.</span></span> <span data-ttu-id="bdf4d-109">@No__t_0 döngüsünün tanımını başlatır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="bdf4d-110">@No__t_0 kullanılmadığı müddetçe gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-110">Required unless `Until` is used.</span></span> <span data-ttu-id="bdf4d-111">@No__t_0 `False` kadar döngüyü tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="bdf4d-112">@No__t_0 kullanılmadığı müddetçe gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-112">Required unless `While` is used.</span></span> <span data-ttu-id="bdf4d-113">@No__t_0 `True` kadar döngüyü tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="bdf4d-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-114">Optional.</span></span> <span data-ttu-id="bdf4d-115">`Boolean` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-115">`Boolean` expression.</span></span> <span data-ttu-id="bdf4d-116">@No__t_0 `Nothing`, Visual Basic `False` olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="bdf4d-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-117">Optional.</span></span> <span data-ttu-id="bdf4d-118">@No__t_0, veya Until olarak yinelenen bir veya daha fazla deyim `True`.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="bdf4d-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-119">Optional.</span></span> <span data-ttu-id="bdf4d-120">Denetimi `Do` döngüsünün bir sonraki yinelemesine aktarır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="bdf4d-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-121">Optional.</span></span> <span data-ttu-id="bdf4d-122">@No__t_0 döngüsünün dışına denetimini aktarır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="bdf4d-123">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-123">Required.</span></span> <span data-ttu-id="bdf4d-124">@No__t_0 döngüsünün tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdf4d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bdf4d-125">Remarks</span></span>  
 <span data-ttu-id="bdf4d-126">Bir deyim kümesini sınırsız sayıda tekrarlamak istediğinizde, bir koşul karşılanana kadar `Do...Loop` yapısını kullanın.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="bdf4d-127">Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="bdf4d-128">Yalnızca `condition` belirtmek için `While` ya da `Until` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="bdf4d-129">@No__t_0 döngünün başlangıcında veya sonunda yalnızca bir kez test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="bdf4d-130">Döngünün başlangıcında `condition` test ederseniz (`Do` bildiriminde), döngü bir kez çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="bdf4d-131">Döngünün sonunda test ederseniz (`Loop` bildiriminde), döngü her zaman en az bir kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="bdf4d-132">Koşul genellikle iki değerin karşılaştırılmasının sonucunu verir, ancak [Boolean veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md) değeri (`True` veya `False`) değerlendirilen herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="bdf4d-133">Bu, `Boolean` dönüştürülen sayısal türler gibi diğer veri türlerinin değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="bdf4d-134">Bir döngüyü diğerinin içine yerleştirerek `Do` döngüleri iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="bdf4d-135">Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="bdf4d-136">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="bdf4d-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdf4d-137">@No__t_0 yapısı, çok daha fazla esneklik sağlar... [ End while Ifadesinin](../../../visual-basic/language-reference/statements/while-end-while-statement.md) `condition` `True` durdurulduğunda veya ilk `True` hale geldiği zaman döngünün sonlandırılmayacağına karar vermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="bdf4d-138">Ayrıca, döngünün başlangıcında veya sonunda `condition` test etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="bdf4d-139">Çık</span><span class="sxs-lookup"><span data-stu-id="bdf4d-139">Exit Do</span></span>  
 <span data-ttu-id="bdf4d-140">[Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri `Do…Loop` çıkmak için alternatif bir yol sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="bdf4d-141">`Exit Do` denetimi, `Loop` bildirisini izleyen deyime hemen aktarır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="bdf4d-142">`Exit Do`, örneğin bir `If...Then...Else` yapısında bir koşul hesaplandıktan sonra kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="bdf4d-143">Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="bdf4d-144">@No__t_0 kullanımı, sonsuz bir *döngüye*neden olabilecek, büyük veya hatta sonsuz bir sayı çalışabilen bir döngü olan bir koşulu test etmekle yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="bdf4d-145">Döngüyü atlamak için `Exit Do` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="bdf4d-146">Herhangi bir sayıda `Exit Do` deyimini `Do…Loop` herhangi bir yere ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="bdf4d-147">İç içe geçmiş `Do` döngüleri içinde kullanıldığında, `Exit Do` denetimi en içteki döngüden ve sonraki daha yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdf4d-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdf4d-148">Example</span></span>  
 <span data-ttu-id="bdf4d-149">Aşağıdaki örnekte, döngü içindeki deyimler `index` değişkeni 10 ' dan büyük olana kadar çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="bdf4d-150">@No__t_0 yan tümcesi döngünün sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="bdf4d-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdf4d-151">Example</span></span>  
 <span data-ttu-id="bdf4d-152">Aşağıdaki örnek, bir `Until` yan tümcesi yerine bir `While` yan tümcesi kullanır ve `condition` son yerine döngünün başlangıcında test edilir.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="bdf4d-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdf4d-153">Example</span></span>  
 <span data-ttu-id="bdf4d-154">Aşağıdaki örnekte, `index` değişkeni 100 ' den büyük olduğunda `condition` döngüyü sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="bdf4d-155">Ancak, döngüdeki `If` ifade, dizin değişkeni 10 ' dan büyük olduğunda `Exit Do` deyimin döngüyü durdurmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="bdf4d-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdf4d-156">Example</span></span>  
 <span data-ttu-id="bdf4d-157">Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="bdf4d-158">@No__t_0 yöntemi dosyayı açar ve karakterleri okuyan bir <xref:System.IO.StreamReader> döndürür.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="bdf4d-159">@No__t_0 koşulunda, `StreamReader` <xref:System.IO.StreamReader.Peek%2A> yöntemi herhangi bir ek karakter olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="bdf4d-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdf4d-160">See also</span></span>

- [<span data-ttu-id="bdf4d-161">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="bdf4d-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="bdf4d-162">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="bdf4d-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="bdf4d-163">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="bdf4d-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="bdf4d-164">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="bdf4d-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="bdf4d-165">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="bdf4d-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="bdf4d-166">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="bdf4d-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)

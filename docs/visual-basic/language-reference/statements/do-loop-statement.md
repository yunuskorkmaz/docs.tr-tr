---
description: 'Hakkında daha fazla bilgi edinin: do... Loop ekstresi (Visual Basic)'
title: Do...Loop Deyimi
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
ms.openlocfilehash: d170074c44d1692517f6b51abd4a6b3d005941c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795189"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="c4eda-103">Do...Loop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4eda-103">Do...Loop Statement (Visual Basic)</span></span>

<span data-ttu-id="c4eda-104">Bir `Boolean` koşul olduğunda `True` veya koşul haline gelene kadar bir deyim bloğunu yineler `True` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-104">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4eda-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4eda-105">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="c4eda-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c4eda-106">Parts</span></span>  
  
|<span data-ttu-id="c4eda-107">Süre</span><span class="sxs-lookup"><span data-stu-id="c4eda-107">Term</span></span>|<span data-ttu-id="c4eda-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="c4eda-108">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="c4eda-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c4eda-109">Required.</span></span> <span data-ttu-id="c4eda-110">Döngünün tanımını başlatır `Do` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-110">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="c4eda-111">`Until`Kullanılmadıysa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c4eda-111">Required unless `Until` is used.</span></span> <span data-ttu-id="c4eda-112">Loop olana kadar tekrarlayın `condition` `False` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-112">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="c4eda-113">`While`Kullanılmadıysa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c4eda-113">Required unless `While` is used.</span></span> <span data-ttu-id="c4eda-114">Loop olana kadar tekrarlayın `condition` `True` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-114">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="c4eda-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c4eda-115">Optional.</span></span> <span data-ttu-id="c4eda-116">`Boolean` ifadesini.</span><span class="sxs-lookup"><span data-stu-id="c4eda-116">`Boolean` expression.</span></span> <span data-ttu-id="c4eda-117">İse `condition` `Nothing` , Visual Basic olduğu gibi davranır `False` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-117">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="c4eda-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c4eda-118">Optional.</span></span> <span data-ttu-id="c4eda-119">, Veya Until gibi yinelenen bir veya daha fazla deyim `condition` `True` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-119">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="c4eda-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c4eda-120">Optional.</span></span> <span data-ttu-id="c4eda-121">Denetimi döngünün bir sonraki yinelemesine aktarır `Do` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-121">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="c4eda-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c4eda-122">Optional.</span></span> <span data-ttu-id="c4eda-123">Denetimi döngünün dışına aktarır `Do` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-123">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="c4eda-124">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c4eda-124">Required.</span></span> <span data-ttu-id="c4eda-125">Döngünün tanımını sonlandırır `Do` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-125">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4eda-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4eda-126">Remarks</span></span>  

 <span data-ttu-id="c4eda-127">Bir `Do...Loop` deyim kümesini sınırsız sayıda yinelemek istediğinizde, bir koşul karşılanana kadar bir yapı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4eda-127">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="c4eda-128">Deyimlerini bir dizi defa yinelemek istiyorsanız, [için... Sonraki Ifade](for-next-statement.md) genellikle daha iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="c4eda-128">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="c4eda-129">`While`Ya da `Until` öğesini belirtmek için veya `condition` ikisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4eda-129">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="c4eda-130">`condition`Döngünün başlangıcında veya sonunda yalnızca bir kez test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4eda-130">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="c4eda-131">Döngünün başlangıcında test ederseniz `condition` ( `Do` bildiriminde), döngü bir kez çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c4eda-131">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="c4eda-132">Döngünün sonunda test ederseniz ( `Loop` bildiriminde), döngü her zaman en az bir kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="c4eda-132">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="c4eda-133">Koşul genellikle iki değerin karşılaştırılmasının sonucunu verir, ancak [Boolean veri türü](../data-types/boolean-data-type.md) değeri (veya) olarak değerlendirilen herhangi bir ifade olabilir `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-133">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="c4eda-134">Buna dönüştürülmüş sayısal türler gibi diğer veri türlerinin değerleri de dahildir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-134">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="c4eda-135">Bir `Do` döngüyü diğerinin içine yerleştirerek döngüleri iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4eda-135">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="c4eda-136">Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4eda-136">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="c4eda-137">Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="c4eda-137">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4eda-138">`Do...Loop`Yapı, çok daha fazla esneklik sağlar [... End while Ifadesinin sonu](while-end-while-statement.md) , ne zaman `condition` `True` veya ilk kez geldiğini sonlandırırken döngüyü sonlandırmaya karar vermenize olanak sağlar `True` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-138">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="c4eda-139">Ayrıca döngünün başlangıcında veya sonunda test etmenizi sağlar `condition` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-139">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="c4eda-140">Çık</span><span class="sxs-lookup"><span data-stu-id="c4eda-140">Exit Do</span></span>  

 <span data-ttu-id="c4eda-141">[Exit Do](exit-statement.md) deyimleri, bir çıkışı için alternatif bir yol sağlayabilir `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-141">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="c4eda-142">`Exit Do` denetimi, ifadesiyle takip eden deyime hemen aktarır `Loop` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-142">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="c4eda-143">`Exit Do` Genellikle, örneğin bir yapıda, bazı koşullar hesaplandıktan sonra kullanılır `If...Then...Else` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-143">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="c4eda-144">Hatalı bir değer veya sonlandırma isteği gibi yineleme işleminin devam etmesi için gereksiz veya imkansız hale getiren bir koşul tespit ederseniz bir döngüden çıkmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4eda-144">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="c4eda-145">Tek kullanımı, sonsuz bir `Exit Do` *döngüye* neden olabilecek bir durum için test etmek, büyük veya hatta sonsuz bir sayı çalışabilen bir döngüdür.</span><span class="sxs-lookup"><span data-stu-id="c4eda-145">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="c4eda-146">`Exit Do`Döngüyü atlamak için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4eda-146">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="c4eda-147">Herhangi `Exit Do` bir yerde herhangi bir sayıda deyim ekleyebilirsiniz `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-147">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="c4eda-148">İç içe döngüler içinde kullanıldığında `Do` , `Exit Do` denetimi en içteki döngünün dışına ve sonraki yüksek iç içe geçme düzeyine aktarır.</span><span class="sxs-lookup"><span data-stu-id="c4eda-148">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4eda-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4eda-149">Example</span></span>  

 <span data-ttu-id="c4eda-150">Aşağıdaki örnekte, döngü içindeki deyimler, değişken 10 ' dan büyük olana kadar çalışmaya devam eder `index` .</span><span class="sxs-lookup"><span data-stu-id="c4eda-150">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="c4eda-151">`Until`Yan tümce döngünün sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="c4eda-151">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="c4eda-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4eda-152">Example</span></span>  

 <span data-ttu-id="c4eda-153">Aşağıdaki örnek `While` , bir yan tümce yerine bir yan tümce kullanır `Until` ve `condition` son yerine döngüsünün başlangıcında test edilir.</span><span class="sxs-lookup"><span data-stu-id="c4eda-153">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="c4eda-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4eda-154">Example</span></span>  

 <span data-ttu-id="c4eda-155">Aşağıdaki örnekte, `condition` `index` değişken 100 ' den büyükse döngüyü sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c4eda-155">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="c4eda-156">`If`Ancak, döngüdeki ifade, `Exit Do` Dizin değişkeni 10 ' dan büyük olduğunda deyimin döngüyü durdurmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c4eda-156">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="c4eda-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4eda-157">Example</span></span>  

 <span data-ttu-id="c4eda-158">Aşağıdaki örnek bir metin dosyasındaki tüm satırları okur.</span><span class="sxs-lookup"><span data-stu-id="c4eda-158">The following example reads all lines in a text file.</span></span> <span data-ttu-id="c4eda-159"><xref:System.IO.File.OpenText%2A>Yöntemi dosyayı açar ve karakterleri okuyan bir döndürür <xref:System.IO.StreamReader> .</span><span class="sxs-lookup"><span data-stu-id="c4eda-159">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="c4eda-160">Koşulunda, `Do...Loop` <xref:System.IO.StreamReader.Peek%2A> öğesinin yöntemi `StreamReader` ek karakter olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c4eda-160">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="c4eda-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4eda-161">See also</span></span>

- [<span data-ttu-id="c4eda-162">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="c4eda-162">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="c4eda-163">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="c4eda-163">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="c4eda-164">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c4eda-164">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="c4eda-165">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="c4eda-165">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="c4eda-166">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="c4eda-166">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="c4eda-167">While...End While Deyimi</span><span class="sxs-lookup"><span data-stu-id="c4eda-167">While...End While Statement</span></span>](while-end-while-statement.md)

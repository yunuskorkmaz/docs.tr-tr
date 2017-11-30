---
title: "Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16365b64e5430be61c113ac7601154df260e4ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="28e3b-102">Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28e3b-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="28e3b-103">A *lambda ifadesi* bir işlevi veya bir adı yok alt yordam.</span><span class="sxs-lookup"><span data-stu-id="28e3b-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="28e3b-104">Lambda ifadesi bir temsilci türü geçerli olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="28e3b-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="28e3b-105">Tek satırlı lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="28e3b-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="28e3b-106">Burada bir temsilci türü kullanılabilirdi, herhangi bir durumda anahtar sözcüğünü yazmanız `Function`, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="28e3b-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="28e3b-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="28e3b-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="28e3b-108">Parantez içindeki hemen sonra `Function`, işlev parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="28e3b-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="28e3b-109">Adından sonra belirtmeyin fark `Function`.</span><span class="sxs-lookup"><span data-stu-id="28e3b-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="28e3b-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="28e3b-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="28e3b-111">Parametre listesi işlev gövdesi olarak tek bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="28e3b-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="28e3b-112">İçin ifadeyi hesaplar işlev tarafından döndürülen değer değerdir.</span><span class="sxs-lookup"><span data-stu-id="28e3b-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="28e3b-113">Kullanmadığınız bir `As` yan tümcesini dönüş türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="28e3b-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     <span data-ttu-id="28e3b-114">Lambda ifadesi bir tamsayı bağımsız değişken geçirme çağrısı.</span><span class="sxs-lookup"><span data-stu-id="28e3b-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  <span data-ttu-id="28e3b-115">Alternatif olarak, aşağıdaki örnekte aynı sonucu elde edilir:</span><span class="sxs-lookup"><span data-stu-id="28e3b-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="28e3b-116">Tek satırlı lambda ifadesi alt yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="28e3b-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="28e3b-117">Burada bir temsilci türü kullanılabilirdi, herhangi bir durumda anahtar sözcüğünü yazmanız `Sub`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="28e3b-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="28e3b-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="28e3b-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="28e3b-119">Parantez içindeki hemen sonra `Sub`, alt yordam parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="28e3b-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="28e3b-120">Adından sonra belirtmeyin fark `Sub`.</span><span class="sxs-lookup"><span data-stu-id="28e3b-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="28e3b-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="28e3b-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="28e3b-122">Parametre listesi alt yordama gövdesi olarak tek bir deyimde yazın.</span><span class="sxs-lookup"><span data-stu-id="28e3b-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     <span data-ttu-id="28e3b-123">Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrısı.</span><span class="sxs-lookup"><span data-stu-id="28e3b-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="28e3b-124">Çok satırlı lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="28e3b-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="28e3b-125">Burada bir temsilci türü kullanılabilirdi, herhangi bir durumda anahtar sözcüğünü yazmanız `Function`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="28e3b-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="28e3b-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="28e3b-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="28e3b-127">Parantez içindeki hemen sonra `Function`, işlev parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="28e3b-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="28e3b-128">Adından sonra belirtmeyin fark `Function`.</span><span class="sxs-lookup"><span data-stu-id="28e3b-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="28e3b-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="28e3b-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="28e3b-130">ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="28e3b-130">Press ENTER.</span></span> <span data-ttu-id="28e3b-131">`End Function` Deyimi otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="28e3b-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="28e3b-132">İşlev gövdesi içinde bir ifade oluşturun ve değerini döndürmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28e3b-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="28e3b-133">Kullanmadığınız bir `As` yan tümcesini dönüş türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="28e3b-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     <span data-ttu-id="28e3b-134">Lambda ifadesi bir tamsayı bağımsız değişken geçirme çağrısı.</span><span class="sxs-lookup"><span data-stu-id="28e3b-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="28e3b-135">Çok satırlı lambda ifadesi alt yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="28e3b-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="28e3b-136">Burada bir temsilci türü kullanılabilirdi, herhangi bir durumda anahtar sözcüğünü yazmanız `Sub`, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="28e3b-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="28e3b-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="28e3b-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="28e3b-138">Parantez içindeki hemen sonra `Sub`, alt yordam parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="28e3b-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="28e3b-139">Adından sonra belirtmeyin fark `Sub`.</span><span class="sxs-lookup"><span data-stu-id="28e3b-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="28e3b-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="28e3b-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="28e3b-141">ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="28e3b-141">Press ENTER.</span></span> <span data-ttu-id="28e3b-142">`End Sub` Deyimi otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="28e3b-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="28e3b-143">İşlev gövdesi içinde alt yordam çağrıldığında yürütmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28e3b-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     <span data-ttu-id="28e3b-144">Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrısı.</span><span class="sxs-lookup"><span data-stu-id="28e3b-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a><span data-ttu-id="28e3b-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="28e3b-145">Example</span></span>  
 <span data-ttu-id="28e3b-146">Lambda ifadeleri yaygın kullanımı için bağımsız değişken türü olan bir parametre olarak geçirilebilir işlevi tanımlamaktır `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="28e3b-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="28e3b-147">Aşağıdaki örnekte, <xref:System.Diagnostics.Process.GetProcesses%2A> yöntemi yerel bilgisayarda çalışan işlemlerin bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="28e3b-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="28e3b-148"><xref:System.Linq.Enumerable.Where%2A> Yönteminden <xref:System.Linq.Enumerable> sınıfı gerektiren bir `Boolean` temsilci bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="28e3b-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="28e3b-149">Örnekte lambda ifadesi bu amaç için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28e3b-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="28e3b-150">Döndürdüğü `True` her işlem için yalnızca bir iş parçacığı sahip ve bu seçili `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="28e3b-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 <span data-ttu-id="28e3b-151">Önceki örnekte yazıldığı aşağıdaki kodu eşdeğerdir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="28e3b-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="28e3b-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28e3b-152">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 [<span data-ttu-id="28e3b-153">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="28e3b-153">Lambda Expressions</span></span>](./lambda-expressions.md)  
 [<span data-ttu-id="28e3b-154">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="28e3b-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="28e3b-155">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="28e3b-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="28e3b-156">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="28e3b-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="28e3b-157">Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirme</span><span class="sxs-lookup"><span data-stu-id="28e3b-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="28e3b-158">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="28e3b-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="28e3b-159">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="28e3b-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

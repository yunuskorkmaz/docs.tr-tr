---
title: 'Nasıl yapılır: Bir Lambda ifadesi (Visual Basic) oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 35df64848c0506a1c0a97bd8cd34f158f9febcd7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970174"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="3d4d5-102">Nasıl yapılır: Bir Lambda ifadesi (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d4d5-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="3d4d5-103">A *lambda ifadesi* bir işlev veya bir ada sahip bir alt yordam.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="3d4d5-104">Bir lambda ifadesi, bir temsilci türü geçerli olduğu her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="3d4d5-105">Tek satırlı lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3d4d5-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="3d4d5-106">Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Function`, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="3d4d5-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="3d4d5-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="3d4d5-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="3d4d5-108">Parantez içinde hemen sonra `Function`, işlev parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="3d4d5-109">Sonra adı belirtmeyin fark `Function`.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="3d4d5-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="3d4d5-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="3d4d5-111">Parametre listesi işlev gövdesi olarak tek bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="3d4d5-112">İfadeyi değerlendiren işlevi tarafından döndürülen değer değerdir.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="3d4d5-113">Kullanmadığınız bir `As` dönüş türü belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="3d4d5-114">Lambda ifadesi tamsayı bağımsız değişken geçirme çağrı.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4.  <span data-ttu-id="3d4d5-115">Alternatif olarak, aşağıdaki örnekte aynı sonucu elde edilir:</span><span class="sxs-lookup"><span data-stu-id="3d4d5-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="3d4d5-116">Tek satırlı lambda ifadesi alt yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3d4d5-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="3d4d5-117">Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Sub`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="3d4d5-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="3d4d5-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="3d4d5-119">Parantez içinde hemen sonra `Sub`, alt yordam parametreleri yazın.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="3d4d5-120">Sonra adı belirtmeyin fark `Sub`.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="3d4d5-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="3d4d5-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="3d4d5-122">Parametre listesi tek deyimde alt yordam gövdesi olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="3d4d5-123">Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrı.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="3d4d5-124">Çok satırlı lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3d4d5-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="3d4d5-125">Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Function`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="3d4d5-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="3d4d5-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="3d4d5-127">Parantez içinde hemen sonra `Function`, işlev parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="3d4d5-128">Sonra adı belirtmeyin fark `Function`.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="3d4d5-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="3d4d5-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="3d4d5-130">Press ENTER.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-130">Press ENTER.</span></span> <span data-ttu-id="3d4d5-131">`End Function` Deyimi otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="3d4d5-132">İşlev gövdesi içinde bir ifade oluşturun ve değeri döndürmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="3d4d5-133">Kullanmadığınız bir `As` dönüş türü belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="3d4d5-134">Lambda ifadesi tamsayı bağımsız değişken geçirme çağrı.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="3d4d5-135">Çok satırlı lambda ifadesi alt yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3d4d5-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="3d4d5-136">Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Sub`, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="3d4d5-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="3d4d5-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="3d4d5-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="3d4d5-138">Parantez içinde hemen sonra `Sub`, alt yordam parametreleri yazın.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="3d4d5-139">Sonra adı belirtmeyin fark `Sub`.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="3d4d5-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="3d4d5-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="3d4d5-141">Press ENTER.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-141">Press ENTER.</span></span> <span data-ttu-id="3d4d5-142">`End Sub` Deyimi otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="3d4d5-143">İşlev gövdesi içinde alt yordam çağrıldığında yürütmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="3d4d5-144">Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrı.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="3d4d5-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d4d5-145">Example</span></span>  
 <span data-ttu-id="3d4d5-146">Lambda ifadeleri yaygın kullanımı bir işlev için bağımsız değişken türü olan bir parametre olarak geçirilebilir tanımlamaktır `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="3d4d5-147">Aşağıdaki örnekte, <xref:System.Diagnostics.Process.GetProcesses%2A> yöntem, yerel bilgisayarda çalışan işlemlerin bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="3d4d5-148"><xref:System.Linq.Enumerable.Where%2A> Yönteminden <xref:System.Linq.Enumerable> sınıfı gerektirir bir `Boolean` temsilci bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="3d4d5-149">Bu örnek, lambda ifadesi bu amaç için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="3d4d5-150">Döndürür `True` her işlem için yalnızca bir iş parçacığı olan ve bu seçili `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="3d4d5-151">Önceki örnekte, yazıldığı aşağıdaki koda eşdeğerdir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="3d4d5-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="3d4d5-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d4d5-152">See also</span></span>
- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="3d4d5-153">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="3d4d5-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="3d4d5-154">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="3d4d5-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="3d4d5-155">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="3d4d5-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="3d4d5-156">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="3d4d5-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="3d4d5-157">Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin</span><span class="sxs-lookup"><span data-stu-id="3d4d5-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="3d4d5-158">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="3d4d5-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="3d4d5-159">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="3d4d5-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

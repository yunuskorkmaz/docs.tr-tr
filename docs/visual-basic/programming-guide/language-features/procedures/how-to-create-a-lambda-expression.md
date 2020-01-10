---
title: 'Nasıl yapılır: Lambda İfadesi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 1c65841e4c124252cfa41bcd4d0c305a426687ee
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632356"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="902cb-102">Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="902cb-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="902cb-103">*Lambda ifadesi* , adı olmayan bir işlev veya alt yordam.</span><span class="sxs-lookup"><span data-stu-id="902cb-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="902cb-104">Bir lambda ifadesi, bir temsilci türünün geçerli olduğu her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="902cb-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="902cb-105">Tek satırlık lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="902cb-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="902cb-106">Temsilci türünün kullanılabileceği herhangi bir durumda, aşağıdaki örnekte olduğu gibi `Function`anahtar sözcüğünü yazın:</span><span class="sxs-lookup"><span data-stu-id="902cb-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="902cb-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="902cb-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="902cb-108">Parantez içinde, `Function`doğrudan sonra, işlevin parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="902cb-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="902cb-109">`Function`sonra bir ad belirtmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="902cb-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="902cb-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="902cb-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="902cb-111">Parametre listesini izleyerek işlevin gövdesi olarak tek bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="902cb-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="902cb-112">İfadenin değerlendirme değeri, işlev tarafından döndürülen değerdir.</span><span class="sxs-lookup"><span data-stu-id="902cb-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="902cb-113">Dönüş türünü belirtmek için bir `As` yan tümcesi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="902cb-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="902cb-114">Bir tamsayı bağımsız değişkeni geçirerek lambda ifadesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="902cb-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="902cb-115">Alternatif olarak, aynı sonuç aşağıdaki örnek tarafından gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="902cb-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="902cb-116">Tek satırlık lambda ifadesi alt yordamı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="902cb-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="902cb-117">Temsilci türünün kullanılabileceği herhangi bir durumda, aşağıdaki örnekte gösterildiği gibi `Sub`anahtar sözcüğünü yazın.</span><span class="sxs-lookup"><span data-stu-id="902cb-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="902cb-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="902cb-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="902cb-119">Parantez içinde, `Sub`doğrudan sonrasında, alt yordamın parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="902cb-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="902cb-120">`Sub`sonra bir ad belirtmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="902cb-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="902cb-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="902cb-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="902cb-122">Parametre listesini takip eden alt yordamın gövdesi olarak tek bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="902cb-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="902cb-123">Bir dize bağımsız değişkenine geçirerek lambda ifadesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="902cb-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="902cb-124">Çok satırlı lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="902cb-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="902cb-125">Temsilci türünün kullanılabileceği herhangi bir durumda, aşağıdaki örnekte gösterildiği gibi `Function`anahtar sözcüğünü yazın.</span><span class="sxs-lookup"><span data-stu-id="902cb-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="902cb-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="902cb-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="902cb-127">Parantez içinde, `Function`doğrudan sonra, işlevin parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="902cb-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="902cb-128">`Function`sonra bir ad belirtmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="902cb-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="902cb-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="902cb-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="902cb-130">ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="902cb-130">Press ENTER.</span></span> <span data-ttu-id="902cb-131">`End Function` deyimleri otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="902cb-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="902cb-132">İşlevin gövdesinde, bir ifade oluşturmak ve değeri döndürmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="902cb-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="902cb-133">Dönüş türünü belirtmek için bir `As` yan tümcesi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="902cb-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="902cb-134">Bir tamsayı bağımsız değişkeni geçirerek lambda ifadesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="902cb-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="902cb-135">Çok satırlı lambda ifadesi alt yordamı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="902cb-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="902cb-136">Temsilci türünün kullanılabileceği herhangi bir durumda, aşağıdaki örnekte gösterildiği gibi `Sub`anahtar sözcüğünü yazın:</span><span class="sxs-lookup"><span data-stu-id="902cb-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="902cb-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="902cb-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="902cb-138">Parantez içinde, `Sub`doğrudan sonrasında, alt yordamın parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="902cb-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="902cb-139">`Sub`sonra bir ad belirtmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="902cb-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="902cb-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="902cb-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="902cb-141">ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="902cb-141">Press ENTER.</span></span> <span data-ttu-id="902cb-142">`End Sub` deyimleri otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="902cb-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="902cb-143">İşlevin gövdesinde, alt yordam çağrıldığında yürütülecek aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="902cb-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="902cb-144">Bir dize bağımsız değişkenine geçirerek lambda ifadesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="902cb-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="902cb-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="902cb-145">Example</span></span>  
 <span data-ttu-id="902cb-146">Lambda ifadelerinin yaygın kullanımı, türü `Delegate`olan bir parametre için bağımsız değişken olarak geçirilebilecek bir işlev tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="902cb-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="902cb-147">Aşağıdaki örnekte <xref:System.Diagnostics.Process.GetProcesses%2A> yöntemi, yerel bilgisayarda çalışan işlemlerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="902cb-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="902cb-148"><xref:System.Linq.Enumerable> sınıfındaki <xref:System.Linq.Enumerable.Where%2A> yöntemi bağımsız değişkeni olarak bir `Boolean` temsilcisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="902cb-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="902cb-149">Örnekteki lambda ifadesi bu amaçla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="902cb-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="902cb-150">Yalnızca bir iş parçacığına sahip olan her işlem için `True` döndürür ve bunlar `filteredList`seçilir.</span><span class="sxs-lookup"><span data-stu-id="902cb-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="902cb-151">Önceki örnek, dil ile tümleşik sorgu (LINQ) sözdiziminde yazılan aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="902cb-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="902cb-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="902cb-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="902cb-153">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="902cb-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="902cb-154">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="902cb-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="902cb-155">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="902cb-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="902cb-156">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="902cb-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="902cb-157">Nasıl yapılır: yordamları Visual Basic başka bir yordama geçirme</span><span class="sxs-lookup"><span data-stu-id="902cb-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="902cb-158">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="902cb-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="902cb-159">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="902cb-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

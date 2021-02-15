---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: lambda Ifadesi oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Lambda İfadesi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 386d40c1e2021c9b02b2f785300c4e978b4da87d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472572"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="bf278-103">Nasıl yapılır: Lambda İfadesi Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf278-103">How to: Create a Lambda Expression (Visual Basic)</span></span>

<span data-ttu-id="bf278-104">*Lambda ifadesi* , adı olmayan bir işlev veya alt yordam.</span><span class="sxs-lookup"><span data-stu-id="bf278-104">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="bf278-105">Bir lambda ifadesi, bir temsilci türünün geçerli olduğu her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf278-105">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="bf278-106">Tek satırlık lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bf278-106">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="bf278-107">Temsilci türünün kullanılabileceği herhangi bir durumda, `Function` Aşağıdaki örnekte olduğu gibi anahtar sözcüğünü yazın:</span><span class="sxs-lookup"><span data-stu-id="bf278-107">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="bf278-108">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="bf278-108">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="bf278-109">Parantez içinde doğrudan sonra, `Function` işlevin parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="bf278-109">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="bf278-110">Sonrasında bir ad belirtmediğine dikkat edin `Function` .</span><span class="sxs-lookup"><span data-stu-id="bf278-110">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="bf278-111">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="bf278-111">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="bf278-112">Parametre listesini izleyerek işlevin gövdesi olarak tek bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="bf278-112">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="bf278-113">İfadenin değerlendirme değeri, işlev tarafından döndürülen değerdir.</span><span class="sxs-lookup"><span data-stu-id="bf278-113">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="bf278-114">`As`Dönüş türünü belirtmek için bir yan tümce kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bf278-114">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="bf278-115">Bir tamsayı bağımsız değişkeni geçirerek lambda ifadesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf278-115">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="bf278-116">Alternatif olarak, aynı sonuç aşağıdaki örnek tarafından gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="bf278-116">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="bf278-117">Tek satırlık lambda ifadesi alt yordamı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bf278-117">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="bf278-118">Temsilci türünün kullanılabileceği herhangi bir durumda, `Sub` Aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü yazın.</span><span class="sxs-lookup"><span data-stu-id="bf278-118">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="bf278-119">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="bf278-119">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="bf278-120">Parantez içinde doğrudan sonrasında `Sub` , alt yordamın parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="bf278-120">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="bf278-121">Sonrasında bir ad belirtmediğine dikkat edin `Sub` .</span><span class="sxs-lookup"><span data-stu-id="bf278-121">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="bf278-122">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="bf278-122">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="bf278-123">Parametre listesini takip eden alt yordamın gövdesi olarak tek bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="bf278-123">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="bf278-124">Bir dize bağımsız değişkenine geçirerek lambda ifadesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf278-124">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="bf278-125">Çok satırlı lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bf278-125">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="bf278-126">Temsilci türünün kullanılabileceği herhangi bir durumda, `Function` Aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü yazın.</span><span class="sxs-lookup"><span data-stu-id="bf278-126">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="bf278-127">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="bf278-127">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="bf278-128">Parantez içinde doğrudan sonra, `Function` işlevin parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="bf278-128">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="bf278-129">Sonrasında bir ad belirtmediğine dikkat edin `Function` .</span><span class="sxs-lookup"><span data-stu-id="bf278-129">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="bf278-130">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="bf278-130">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="bf278-131">ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bf278-131">Press ENTER.</span></span> <span data-ttu-id="bf278-132">`End Function`Ekstre otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="bf278-132">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="bf278-133">İşlevin gövdesinde, bir ifade oluşturmak ve değeri döndürmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bf278-133">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="bf278-134">`As`Dönüş türünü belirtmek için bir yan tümce kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bf278-134">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="bf278-135">Bir tamsayı bağımsız değişkeni geçirerek lambda ifadesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf278-135">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="bf278-136">Çok satırlı lambda ifadesi alt yordamı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bf278-136">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="bf278-137">Temsilci türünün kullanılabileceği herhangi bir durumda, `Sub` Aşağıdaki örnekte gösterildiği gibi anahtar sözcüğünü yazın:</span><span class="sxs-lookup"><span data-stu-id="bf278-137">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="bf278-138">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="bf278-138">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="bf278-139">Parantez içinde doğrudan sonrasında `Sub` , alt yordamın parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="bf278-139">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="bf278-140">Sonrasında bir ad belirtmediğine dikkat edin `Sub` .</span><span class="sxs-lookup"><span data-stu-id="bf278-140">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="bf278-141">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="bf278-141">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="bf278-142">ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bf278-142">Press ENTER.</span></span> <span data-ttu-id="bf278-143">`End Sub`Ekstre otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="bf278-143">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="bf278-144">İşlevin gövdesinde, alt yordam çağrıldığında yürütülecek aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bf278-144">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="bf278-145">Bir dize bağımsız değişkenine geçirerek lambda ifadesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf278-145">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="bf278-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf278-146">Example</span></span>  

 <span data-ttu-id="bf278-147">Lambda ifadelerinin yaygın kullanımı, türü olan bir parametre için bağımsız değişken olarak geçirilebilecek bir işlev tanımlamaktır `Delegate` .</span><span class="sxs-lookup"><span data-stu-id="bf278-147">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="bf278-148">Aşağıdaki örnekte, <xref:System.Diagnostics.Process.GetProcesses%2A> yöntemi yerel bilgisayarda çalışan işlemlerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf278-148">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="bf278-149"><xref:System.Linq.Enumerable.Where%2A>Sınıfından yöntemi, <xref:System.Linq.Enumerable> `Boolean` bağımsız değişkeni olarak bir temsilci gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bf278-149">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="bf278-150">Örnekteki lambda ifadesi bu amaçla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf278-150">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="bf278-151">`True`Yalnızca bir iş parçacığına sahip olan ve ' de seçili olan her işlem için döndürür `filteredList` .</span><span class="sxs-lookup"><span data-stu-id="bf278-151">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="bf278-152">Önceki örnek, Language-Integrated Query (LINQ) sözdiziminde yazılan aşağıdaki koda eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="bf278-152">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="bf278-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf278-153">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="bf278-154">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="bf278-154">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="bf278-155">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf278-155">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="bf278-156">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf278-156">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="bf278-157">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="bf278-157">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="bf278-158">Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme</span><span class="sxs-lookup"><span data-stu-id="bf278-158">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="bf278-159">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf278-159">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="bf278-160">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="bf278-160">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)

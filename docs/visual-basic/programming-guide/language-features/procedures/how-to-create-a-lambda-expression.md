---
title: 'Nasıl yapılır: Bir Lambda ifadesi (Visual Basic) oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: fc2b7ed2004b842116d051b393f00506428def61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344552"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="e6958-102">Nasıl yapılır: Bir Lambda ifadesi (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6958-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="e6958-103">A *lambda ifadesi* bir işlev veya bir ada sahip bir alt yordam.</span><span class="sxs-lookup"><span data-stu-id="e6958-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="e6958-104">Bir lambda ifadesi, bir temsilci türü geçerli olduğu her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6958-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="e6958-105">Tek satırlı lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e6958-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="e6958-106">Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Function`, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="e6958-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     `Dim add1 =`   `Function`  
  
2. <span data-ttu-id="e6958-107">Parantez içinde hemen sonra `Function`, işlev parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="e6958-107">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="e6958-108">Sonra adı belirtmeyin fark `Function`.</span><span class="sxs-lookup"><span data-stu-id="e6958-108">Notice that you do not specify a name after `Function`.</span></span>  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. <span data-ttu-id="e6958-109">Parametre listesi işlev gövdesi olarak tek bir ifade yazın.</span><span class="sxs-lookup"><span data-stu-id="e6958-109">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="e6958-110">İfadeyi değerlendiren işlevi tarafından döndürülen değer değerdir.</span><span class="sxs-lookup"><span data-stu-id="e6958-110">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="e6958-111">Kullanmadığınız bir `As` dönüş türü belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e6958-111">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="e6958-112">Lambda ifadesi tamsayı bağımsız değişken geçirme çağrı.</span><span class="sxs-lookup"><span data-stu-id="e6958-112">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="e6958-113">Alternatif olarak, aşağıdaki örnekte aynı sonucu elde edilir:</span><span class="sxs-lookup"><span data-stu-id="e6958-113">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="e6958-114">Tek satırlı lambda ifadesi alt yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e6958-114">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="e6958-115">Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Sub`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e6958-115">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     `Dim add1 =`   `Sub`  
  
2. <span data-ttu-id="e6958-116">Parantez içinde hemen sonra `Sub`, alt yordam parametreleri yazın.</span><span class="sxs-lookup"><span data-stu-id="e6958-116">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="e6958-117">Sonra adı belirtmeyin fark `Sub`.</span><span class="sxs-lookup"><span data-stu-id="e6958-117">Notice that you do not specify a name after `Sub`.</span></span>  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. <span data-ttu-id="e6958-118">Parametre listesi tek deyimde alt yordam gövdesi olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="e6958-118">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="e6958-119">Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrı.</span><span class="sxs-lookup"><span data-stu-id="e6958-119">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="e6958-120">Çok satırlı lambda ifadesi işlevi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e6958-120">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="e6958-121">Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Function`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e6958-121">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     `Dim add1 =`   `Function`  
  
2. <span data-ttu-id="e6958-122">Parantez içinde hemen sonra `Function`, işlev parametrelerini yazın.</span><span class="sxs-lookup"><span data-stu-id="e6958-122">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="e6958-123">Sonra adı belirtmeyin fark `Function`.</span><span class="sxs-lookup"><span data-stu-id="e6958-123">Notice that you do not specify a name after `Function`.</span></span>  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. <span data-ttu-id="e6958-124">Press ENTER.</span><span class="sxs-lookup"><span data-stu-id="e6958-124">Press ENTER.</span></span> <span data-ttu-id="e6958-125">`End Function` Deyimi otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="e6958-125">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="e6958-126">İşlev gövdesi içinde bir ifade oluşturun ve değeri döndürmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6958-126">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="e6958-127">Kullanmadığınız bir `As` dönüş türü belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e6958-127">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="e6958-128">Lambda ifadesi tamsayı bağımsız değişken geçirme çağrı.</span><span class="sxs-lookup"><span data-stu-id="e6958-128">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="e6958-129">Çok satırlı lambda ifadesi alt yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e6958-129">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="e6958-130">Burada bir temsilci türü kullanılabilir herhangi bir durumda anahtar sözcüğü yazın `Sub`, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="e6958-130">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     `Dim add1 =`   `Sub`  
  
2. <span data-ttu-id="e6958-131">Parantez içinde hemen sonra `Sub`, alt yordam parametreleri yazın.</span><span class="sxs-lookup"><span data-stu-id="e6958-131">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="e6958-132">Sonra adı belirtmeyin fark `Sub`.</span><span class="sxs-lookup"><span data-stu-id="e6958-132">Notice that you do not specify a name after `Sub`.</span></span>  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. <span data-ttu-id="e6958-133">Press ENTER.</span><span class="sxs-lookup"><span data-stu-id="e6958-133">Press ENTER.</span></span> <span data-ttu-id="e6958-134">`End Sub` Deyimi otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="e6958-134">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="e6958-135">İşlev gövdesi içinde alt yordam çağrıldığında yürütmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6958-135">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="e6958-136">Lambda ifadesi bir dize bağımsız değişkeni geçirme çağrı.</span><span class="sxs-lookup"><span data-stu-id="e6958-136">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="e6958-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6958-137">Example</span></span>  
 <span data-ttu-id="e6958-138">Lambda ifadeleri yaygın kullanımı bir işlev için bağımsız değişken türü olan bir parametre olarak geçirilebilir tanımlamaktır `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="e6958-138">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="e6958-139">Aşağıdaki örnekte, <xref:System.Diagnostics.Process.GetProcesses%2A> yöntem, yerel bilgisayarda çalışan işlemlerin bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e6958-139">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="e6958-140"><xref:System.Linq.Enumerable.Where%2A> Yönteminden <xref:System.Linq.Enumerable> sınıfı gerektirir bir `Boolean` temsilci bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="e6958-140">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="e6958-141">Bu örnek, lambda ifadesi bu amaç için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6958-141">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="e6958-142">Döndürür `True` her işlem için yalnızca bir iş parçacığı olan ve bu seçili `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="e6958-142">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="e6958-143">Önceki örnekte, yazıldığı aşağıdaki koda eşdeğerdir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="e6958-143">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e6958-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6958-144">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="e6958-145">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="e6958-145">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="e6958-146">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="e6958-146">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="e6958-147">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="e6958-147">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="e6958-148">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e6958-148">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="e6958-149">Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin</span><span class="sxs-lookup"><span data-stu-id="e6958-149">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="e6958-150">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="e6958-150">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="e6958-151">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="e6958-151">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

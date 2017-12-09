---
title: "Lambda İfadeleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69ac88d295420277e99058d0f80a5ae1c2ce2e39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="5d2c5-102">Lambda İfadeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d2c5-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="5d2c5-103">A *lambda ifadesi* bir işlevi veya alt yordama bir temsilci geçerli olduğu yerlerde, kullanılabilecek bir ad olmadan.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="5d2c5-104">Lambda ifadeleri işlevleri veya alt yordamlar olabilir ve tek satırlı veya çok satırlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="5d2c5-105">Değerleri bir lambda ifadesi geçerli kapsamdan geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d2c5-106">`RemoveHandler` Açıklamadır bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="5d2c5-107">Temsilci parametresi için bir lambda ifadesinde geçiremezsiniz `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="5d2c5-108">Lambda ifadeleri kullanarak oluşturduğunuz `Function` veya `Sub` anahtar sözcüğü, standart işlev veya alt yordama oluşturmak gibi.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="5d2c5-109">Ancak, lambda ifadeleri bir deyimde dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="5d2c5-110">Aşağıdaki örnek, bağımsız değişkeni artırır ve değer döndüren bir lambda ifadesi ' dir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="5d2c5-111">Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi işlevi için gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 <span data-ttu-id="5d2c5-112">Aşağıdaki örnek bir değer konsola bir lambda ifadesi ' dir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="5d2c5-113">Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi alt yordam için gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 <span data-ttu-id="5d2c5-114">Önceki örneklerde bir değişken adı lambda ifadeleri atandığını dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="5d2c5-115">Değişkene başvurduğunuzda lambda ifadesi çağırır.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="5d2c5-116">Bildirme ve aşağıdaki örnekte gösterildiği gibi bir lambda ifadesi aynı anda çağırma.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 <span data-ttu-id="5d2c5-117">Lambda ifadesi bir işlev çağrısı değeri olarak döndürülebilecek (örnekte gösterildiği gibi [bağlamı](#context) bu konunun ilerleyen bölümlerinde), veya bir bağımsız değişken bir temsilci türü alan parametresi aşağıda gösterildiği gibi geçirildi örnek.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="5d2c5-118">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d2c5-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="5d2c5-119">Lambda ifadesi sözdizimi, standart işlev veya alt yordama benzer.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="5d2c5-120">Farkları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5d2c5-120">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="5d2c5-121">Lambda ifadesi bir adı yok.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-121">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="5d2c5-122">Lambda ifadeleri olamaz değiştiriciler, gibi `Overloads` veya `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="5d2c5-123">Tek satırlı lambda işlevleri kullanmayın bir `As` dönüş türü atamak yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="5d2c5-124">Bunun yerine, türü lambda ifadesi gövdesi değerlendiren değerinden algılanır.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="5d2c5-125">Örneğin, lambda ifadesi gövdesi ise `cust.City = "London"`, kendi dönüş türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="5d2c5-126">Çok satırlı lambda işlevlerde ya da bir dönüş türü kullanarak belirleyebileceğiniz bir `As` yan tümcesi veya çıkarın `As` yan tümcesi dönüş türü çıkarımı yapılan böylece.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="5d2c5-127">Zaman `As` yan tümcesi için çok satırlı lambda işlevi atlanırsa, dönüş türü tüm baskın türü çıkarımı yapılan `Return` çok satırlı lambda işlevi deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="5d2c5-128">*Baskın türü* tüm diğer türleri için genişletebilirsiniz benzersiz bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="5d2c5-129">Bu benzersiz türü belirlenemiyorsa baskın dizisindeki tüm diğer türleri için daraltabilirsiniz benzersiz türü türüdür.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="5d2c5-130">Bu benzersiz türlerinden hiçbiri belirlenebilir baskın türü varsa, `Object`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="5d2c5-131">Bu durumda, `Option Strict` ayarlanır `On`, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="5d2c5-132">Örneğin, ifadeler için sağlanan `Return` deyimi türü değerleri içeren `Integer`, `Long`, ve `Double`, sonuç dizisi türünde `Double`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="5d2c5-133">Her ikisi de `Integer` ve `Long` için genişletmek `Double` ve yalnızca `Double`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="5d2c5-134">Bu nedenle, `Double` baskın türüdür.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="5d2c5-135">Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="5d2c5-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="5d2c5-136">Tek satırlı işlevinin gövdesini bir deyim bir değer döndüren bir ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="5d2c5-137">Var olan hiçbir `Return` tek satırlı işlevler için deyimi.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="5d2c5-138">Tek satırlı işlevi tarafından döndürülen değeri işlevinin gövdesini ifadesinde değeridir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="5d2c5-139">Tek satırlı alt yordama gövdesi tek satırlı deyim olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="5d2c5-140">Tek satırlı işlevler ve alt yordamlar içermeyen bir `End Function` veya `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="5d2c5-141">Kullanarak bir lambda ifadesi parametresinin veri türü belirtebilirsiniz `As` anahtar sözcüğü ya da parametresinin veri türü sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="5d2c5-142">Veri türleri veya tüm olayla gerekir ya da tüm parametreleri belirledikten gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="5d2c5-143">`Optional`ve `Paramarray` parametreleri izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="5d2c5-144">Genel Parametreler izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="5d2c5-145">Zaman Uyumsuz Lambdalar</span><span class="sxs-lookup"><span data-stu-id="5d2c5-145">Async Lambdas</span></span>  
 <span data-ttu-id="5d2c5-146">Lambda ifadeleri ve kullanarak zaman uyumsuz işleme dahil deyimleri kolayca oluşturabilirsiniz [zaman uyumsuz](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="5d2c5-147">Örneğin, aşağıdaki Windows Forms örnek çağırır ve bir zaman uyumsuz yöntem bekler bir olay işleyiciyi içeriyor `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="5d2c5-148">Bir zaman uyumsuz lambda kullanarak aynı olay işleyicisi ekleyebilirsiniz bir [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5d2c5-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="5d2c5-149">Bu işleyici eklemek için Ekle bir `Async` lambda parametre listesi, aşağıdaki örnekte gösterildiği gibi önce değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="5d2c5-150">Oluşturma ve zaman uyumsuz yöntemler kullanma hakkında daha fazla bilgi için bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d2c5-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <a name="context"></a><span data-ttu-id="5d2c5-151">Bağlam</span><span class="sxs-lookup"><span data-stu-id="5d2c5-151">Context</span></span>  
 <span data-ttu-id="5d2c5-152">Lambda ifadesi ile bağlamı içinde tanımlanan kapsamıyla paylaşır.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="5d2c5-153">İçeren kapsamı içinde yazılmış herhangi bir kod aynı erişim haklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="5d2c5-154">Üye değişkenleri, işlevleri ve alt öğeler, erişim dahildir `Me`, parametreleri ve içeren kapsamdaki yerel değişkenleri ve.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="5d2c5-155">Yerel değişkenleri ve parametreleri içeren kapsamında erişim, kapsamı ömür genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="5d2c5-156">Lambda ifadesi olarak başvuran bir temsilci çöp toplama kullanılamaz olduğu sürece, özgün ortam değişkenlerine erişim korunur.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="5d2c5-157">Aşağıdaki örnekte, değişken `target` için yerel olan `makeTheGame`, yönteminde lambda ifadesi `playTheGame` tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="5d2c5-158">Döndürülen lambda ifadesi atanan Not `takeAGuess` içinde `Main`, hala yerel değişken erişimi `target`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 <span data-ttu-id="5d2c5-159">Aşağıdaki örnek, çeşitli iç içe geçmiş lambda ifadesi erişim haklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="5d2c5-160">Ne zaman döndürülen lambda ifadesi yürütüldüğünde gelen `Main` olarak `aDel`, bu öğeler erişen:</span><span class="sxs-lookup"><span data-stu-id="5d2c5-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="5d2c5-161">İçinde tanımlandığı sınıfının bir alanı:`aField`</span><span class="sxs-lookup"><span data-stu-id="5d2c5-161">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="5d2c5-162">İçinde tanımlandığı sınıfın özelliği:`aProp`</span><span class="sxs-lookup"><span data-stu-id="5d2c5-162">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="5d2c5-163">Yönteminin bir parametresi `functionWithNestedLambda`, tanımlandığı içinde:`level1`</span><span class="sxs-lookup"><span data-stu-id="5d2c5-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="5d2c5-164">Yerel bir değişken `functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="5d2c5-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="5d2c5-165">Yer alan lambda ifadesi parametresinin:`level2`</span><span class="sxs-lookup"><span data-stu-id="5d2c5-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="5d2c5-166">Bir temsilci türüne dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5d2c5-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="5d2c5-167">Lambda ifadesi bir uyumlu temsilci türü örtük olarak dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="5d2c5-168">Uyumluluk için genel gereksinimler hakkında daha fazla bilgi için bkz: [gevşek temsilci dönüşümü](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="5d2c5-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="5d2c5-169">Örneğin, aşağıdaki kod örneğinde örtük olarak dönüştürür bir lambda ifadesi gösterilir `Func(Of Integer, Boolean)` veya eşleşen bir temsilci imzası.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 <span data-ttu-id="5d2c5-170">Aşağıdaki kod örneğinde örtük olarak dönüştürür bir lambda ifadesi gösterilir `Sub(Of Double, String, Double)` veya eşleşen bir temsilci imzası.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 <span data-ttu-id="5d2c5-171">Lambda ifadeleri temsilcileri atayın ya da bunları yordamları bağımsız değişken olarak geçirmek parametre adları belirtin ama temsilciden alınması türleri izin vererek kendi veri türleri atlayın.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5d2c5-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5d2c5-172">Examples</span></span>  
  
-   <span data-ttu-id="5d2c5-173">Aşağıdaki örnek döndüren bir lambda ifadesi tanımlar `True` boş değer atanabilir bağımsız değişkeni atanan bir değeri varsa ve `False` değerini ise `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   <span data-ttu-id="5d2c5-174">Aşağıdaki örnek, bir dizi son öğenin dizinini döndürür bir lambda ifadesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5d2c5-175">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d2c5-175">See Also</span></span>  
 [<span data-ttu-id="5d2c5-176">Yordamları</span><span class="sxs-lookup"><span data-stu-id="5d2c5-176">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5d2c5-177">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="5d2c5-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="5d2c5-178">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="5d2c5-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="5d2c5-179">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="5d2c5-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5d2c5-180">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="5d2c5-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="5d2c5-181">Boş değer atanabilen değer türleri</span><span class="sxs-lookup"><span data-stu-id="5d2c5-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="5d2c5-182">Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirme</span><span class="sxs-lookup"><span data-stu-id="5d2c5-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="5d2c5-183">Nasıl yapılır: Lambda ifadesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d2c5-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)  
 [<span data-ttu-id="5d2c5-184">Gevşek temsilci dönüşümü</span><span class="sxs-lookup"><span data-stu-id="5d2c5-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)

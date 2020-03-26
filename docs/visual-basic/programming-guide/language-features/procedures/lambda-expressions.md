---
title: Lambda İfadeleri
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249675"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="25763-102">Lambda İfadeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25763-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="25763-103">*Lambda ifadesi,* temsilcinin geçerli olduğu her yerde kullanılabilecek bir ad olmayan bir işlev veya alt yordamdır.</span><span class="sxs-lookup"><span data-stu-id="25763-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="25763-104">Lambda ifadeleri işlevler veya alt yordamlar olabilir ve tek satırlı veya çok satırlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="25763-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="25763-105">Değerleri geçerli kapsamdan lambda ifadesine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25763-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="25763-106">İfade `RemoveHandler` bir istisnadır.</span><span class="sxs-lookup"><span data-stu-id="25763-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="25763-107">`RemoveHandler`'nin temsilci parametresi için lambda ifadesini geçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="25763-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="25763-108">Standart bir işlev veya `Function` `Sub` alt yordam oluşturduğunuz gibi, lambda ifadelerini de standart bir işlev veya alt yordam oluşturduğunuz gibi, anahtar kelimeyi kullanarak lambda ifadeleri oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="25763-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="25763-109">Ancak, lambda ifadeler bir açıklamada yer alıyor.</span><span class="sxs-lookup"><span data-stu-id="25763-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="25763-110">Aşağıdaki örnek, bağımsız değişkenini artan ve değeri döndüren bir lambda ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="25763-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="25763-111">Örnek, bir işlev için hem tek satırlı hem de çok satırlı lambda ifade sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25763-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="25763-112">Aşağıdaki örnek, konsola bir değer yazan bir lambda ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="25763-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="25763-113">Örnek, bir alt yordam için hem tek satırlı hem de çok satırlı lambda ifade sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25763-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="25763-114">Önceki örneklerde lambda ifadelerinin değişken bir ada atandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="25763-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="25763-115">Değişkene her başvuruyaptığınızda, lambda ifadesini çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="25763-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="25763-116">Ayrıca, aşağıdaki örnekte gösterildiği gibi, aynı anda bir lambda ifadesini beyan edebilir ve çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25763-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="25763-117">Lambda ifadesi işlev çağrısının değeri olarak döndürülebilir (bu konunun ilerleyen bölümünde [Bağlam](#context) bölümünde gösterildiği gibi) veya aşağıdaki örnekte gösterildiği gibi, temsilci türünü alan bir parametreye bağımsız değişken olarak geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="25763-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="25763-118">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25763-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="25763-119">Lambda ifadesinin sözdizimi standart bir işlevin veya alt yordamınkine benzer.</span><span class="sxs-lookup"><span data-stu-id="25763-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="25763-120">Farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="25763-120">The differences are as follows:</span></span>

- <span data-ttu-id="25763-121">Lambda ifadesinin bir adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="25763-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="25763-122">Lambda ifadeleri gibi `Overloads` değiştiriciler olamaz, `Overrides`ya da .</span><span class="sxs-lookup"><span data-stu-id="25763-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="25763-123">Tek satırlı lambda işlevleri, `As` dönüş türünü belirlemek için bir yan tümce kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="25763-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="25763-124">Bunun yerine, tür lambda ifadesinin gövdesinin değerlendirdığı değerden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="25763-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="25763-125">Örneğin, lambda ifadesinin gövdesi `cust.City = "London"`ise, dönüş türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="25763-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="25763-126">Çok satırlı lambda işlevlerinde, bir yan tümce `As` kullanarak bir iade `As` türü belirtebilir veya iade türünün çıkarılaması için yan tümceyi atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25763-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="25763-127">Çok `As` satırlı lambda işlevi için yan tümce atlandığında, dönüş türü çok satırlı lambda işlevindeki tüm `Return` ifadelerden baskın tür olarak çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="25763-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="25763-128">*Baskın türü,* diğer tüm türlerin genişletebileceği benzersiz bir türdür.</span><span class="sxs-lookup"><span data-stu-id="25763-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="25763-129">Bu benzersiz tür belirlenemiyorsa, baskın tür dizideki tüm diğer türlerin daraltabileceği benzersiz türüdür.</span><span class="sxs-lookup"><span data-stu-id="25763-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="25763-130">Bu benzersiz türlerden hiçbiri belirlenemezse, `Object`baskın tür .</span><span class="sxs-lookup"><span data-stu-id="25763-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="25763-131">Bu durumda, `Option Strict` olarak ayarlanırsa, `On`bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="25763-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="25763-132">Örneğin, `Return` deyime verilen ifadeler , `Integer`, , `Long`ve `Double`, ortaya çıkan dizi değerleri `Double`içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="25763-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="25763-133">Hem `Integer` `Long` genişletmek `Double` ve sadece `Double`.</span><span class="sxs-lookup"><span data-stu-id="25763-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="25763-134">Bu `Double` nedenle, baskın türüdür.</span><span class="sxs-lookup"><span data-stu-id="25763-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="25763-135">Daha fazla bilgi için [Dönüşümleri Genişletme ve Daraltma'ya](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="25763-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="25763-136">Tek satırlı bir işlevin gövdesi, bir ifade değil, bir değer döndüren bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25763-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="25763-137">Tek satırlı işlevler için ifade yok. `Return`</span><span class="sxs-lookup"><span data-stu-id="25763-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="25763-138">Tek satırlı işlev tarafından döndürülen değer, işlevin gövdesindeki ifadenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="25763-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="25763-139">Tek satırlı bir alt yordamın gövdesi tek satırlı ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25763-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="25763-140">Tek satırlı işlevler ve alt `End Function` yordamlar bir veya `End Sub` deyim içermez.</span><span class="sxs-lookup"><span data-stu-id="25763-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="25763-141">Bir lambda ifade parametresinin veri türünü `As` anahtar sözcüğü kullanarak belirtebilirsiniz veya parametrenin veri türü çıkarılabilir.</span><span class="sxs-lookup"><span data-stu-id="25763-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="25763-142">Tüm parametrelerin belirtilen veri türleri olmalı veya tüm bunlar çıkarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25763-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="25763-143">`Optional`ve `Paramarray` parametrelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="25763-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="25763-144">Genel parametrelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="25763-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="25763-145">Zaman Uyumsuz Lambdalar</span><span class="sxs-lookup"><span data-stu-id="25763-145">Async Lambdas</span></span>

<span data-ttu-id="25763-146">[Async](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar kelimelerini kullanarak asynchronous işlemeiçeren lambda ifadeleri ve deyimleri kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25763-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="25763-147">Örneğin, aşağıdaki Windows Forms örneği çağıran ve bir async yöntemi ni `ExampleMethodAsync`bekleyen bir olay işleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="25763-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="25763-148">[AddHandler Deyimi'nde](../../../../visual-basic/language-reference/statements/addhandler-statement.md)bir async lambda kullanarak aynı olay işleyicisi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25763-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="25763-149">Bu işleyiciyi eklemek `Async` için, aşağıdaki örnekte görüldüğü gibi lambda parametre listesinden önce bir değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="25763-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

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

<span data-ttu-id="25763-150">Async yöntemlerinin nasıl oluşturulup kullanılacağı hakkında daha fazla bilgi için [Async ve Await ile Asynchronous Programming'e](../../../../visual-basic/programming-guide/concepts/async/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="25763-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="25763-151">Bağlam</span><span class="sxs-lookup"><span data-stu-id="25763-151">Context</span></span>

<span data-ttu-id="25763-152">Bir lambda ifadesi, bağlamını tanımlandığı kapsamla paylaşır.</span><span class="sxs-lookup"><span data-stu-id="25763-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="25763-153">Bu kapsamda yazılmış herhangi bir kod olarak aynı erişim haklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="25763-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="25763-154">Bu, üye değişkenlere, işlevlere ve `Me`alt lara, parametrelere ve yerel değişkenlere erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="25763-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="25763-155">İçerdeki kapsamdaki yerel değişkenlere ve parametrelere erişim, bu kapsamın ömrünün ötesine uzanabilir.</span><span class="sxs-lookup"><span data-stu-id="25763-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="25763-156">Çöp toplama için lambda ifadesine atıfta bulunan bir temsilci kullanılamadığı sürece, özgün ortamdaki değişkenlere erişim korunur.</span><span class="sxs-lookup"><span data-stu-id="25763-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="25763-157">Aşağıdaki örnekte, `target` değişken , `makeTheGame`lambda ifade `playTheGame` tanımlanan yöntem için yereldir.</span><span class="sxs-lookup"><span data-stu-id="25763-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="25763-158">Döndürülen lambda ifadesinin, `takeAGuess` yerel `Main`değişkene `target`hala erişebilen bir ifadeolduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="25763-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="25763-159">Aşağıdaki örnek, iç içe lambda ifadesinin geniş erişim haklarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="25763-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="25763-160">Döndürülen lambda ifadesi `Main` şu `aDel`şekilde yürütüldüğünde, şu unsurlara erişir:</span><span class="sxs-lookup"><span data-stu-id="25763-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="25763-161">Tanımlandığı sınıfın bir alanı:`aField`</span><span class="sxs-lookup"><span data-stu-id="25763-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="25763-162">Tanımlandığı sınıfın özelliği:`aProp`</span><span class="sxs-lookup"><span data-stu-id="25763-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="25763-163">Yöntemin bir `functionWithNestedLambda`parametresi , hangi tanımlanır:`level1`</span><span class="sxs-lookup"><span data-stu-id="25763-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="25763-164">Yerel bir `functionWithNestedLambda`değişken:`localVar`</span><span class="sxs-lookup"><span data-stu-id="25763-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="25763-165">İç içe olduğu lambda ifadesinin bir parametresi:`level2`</span><span class="sxs-lookup"><span data-stu-id="25763-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="25763-166">Temsilci Türüne Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="25763-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="25763-167">Lambda ifadesi örtülü olarak uyumlu bir temsilci türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="25763-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="25763-168">Uyumluluk için genel gereksinimler hakkında bilgi için [bkz.](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="25763-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="25763-169">Örneğin, aşağıdaki kod örneği, örtülü olarak veya eşleşen `Func(Of Integer, Boolean)` bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25763-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="25763-170">Aşağıdaki kod örneği, örtülü olarak veya eşleşen `Sub(Of Double, String, Double)` bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25763-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="25763-171">Lambda ifadelerini temsilcilere atadığınızda veya bunları yordamlara bağımsız değişken olarak aktardığınızda, parametre adlarını belirtebilirsiniz, ancak veri türlerini atlayarak türlerin inden alınmasına izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25763-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="25763-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="25763-172">Examples</span></span>

- <span data-ttu-id="25763-173">Aşağıdaki örnekte, nullable değer `True` türü bağımsız değişkeninin atanmış bir değeri `False` varsa ve `Nothing`değeri .</span><span class="sxs-lookup"><span data-stu-id="25763-173">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="25763-174">Aşağıdaki örnek, bir dizideki son öğenin dizinini döndüren bir lambda ifadesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25763-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="25763-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25763-175">See also</span></span>

- [<span data-ttu-id="25763-176">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="25763-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="25763-177">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="25763-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="25763-178">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="25763-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="25763-179">Fonksiyon Bildirimi</span><span class="sxs-lookup"><span data-stu-id="25763-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="25763-180">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="25763-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="25763-181">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="25763-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="25763-182">Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme</span><span class="sxs-lookup"><span data-stu-id="25763-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="25763-183">Nasıl yapılır: Lambda İfadesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="25763-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="25763-184">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="25763-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)

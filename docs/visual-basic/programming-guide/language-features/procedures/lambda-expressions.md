---
description: 'Hakkında daha fazla bilgi edinin: lambda Ifadeleri (Visual Basic)'
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
ms.openlocfilehash: adac7f0d0dbbff575837f691d70c7752eebb39f1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480095"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="0aa25-103">Lambda İfadeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0aa25-103">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="0aa25-104">*Lambda ifadesi* , bir temsilcinin geçerli olduğu her yerde kullanılabilecek bir ada sahip olmayan bir işlev veya alt yordam 'dir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-104">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="0aa25-105">Lambda ifadeleri işlevler veya alt yordamlar olabilir ve tek satırlık veya çok satırlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-105">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="0aa25-106">Geçerli kapsamdan bir lambda ifadesine değer geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-106">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="0aa25-107">`RemoveHandler`İfade bir özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="0aa25-107">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="0aa25-108">Temsilci parametresi için içinde bir lambda ifadesi geçirilemez `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-108">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="0aa25-109">`Function` `Sub` Bir standart işlev veya alt yordam oluştururken olduğu gibi, veya anahtar sözcüğünü kullanarak lambda ifadeleri oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-109">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="0aa25-110">Ancak, lambda ifadeleri bir ifadeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-110">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="0aa25-111">Aşağıdaki örnek, bağımsız değişkenini artıran ve değeri döndüren bir lambda ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-111">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="0aa25-112">Örnek, bir işlev için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-112">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="0aa25-113">Aşağıdaki örnek, konsoluna bir değer yazan bir lambda ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-113">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="0aa25-114">Örnek, bir altyordam için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-114">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="0aa25-115">Önceki örneklerde lambda ifadelerinin bir değişken adına atandığını fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-115">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="0aa25-116">Değişkenine başvurduğunuzda, lambda ifadesini çağırılır.</span><span class="sxs-lookup"><span data-stu-id="0aa25-116">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="0aa25-117">Ayrıca, aşağıdaki örnekte gösterildiği gibi bir lambda ifadesini aynı anda bildirebilir ve çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-117">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="0aa25-118">Bir lambda ifadesi, bir işlev çağrısının değeri olarak döndürülebilir (Bu konunun ilerleyen bölümlerinde yer alan [bağlam](#context) bölümünde gösterildiği gibi) veya aşağıdaki örnekte gösterildiği gibi bir temsilci türü alan parametreye bağımsız değişken olarak geçirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-118">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="0aa25-119">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0aa25-119">Lambda Expression Syntax</span></span>

<span data-ttu-id="0aa25-120">Bir lambda ifadesinin sözdizimi, standart bir işlev veya alt yordamın sözdizimine benzer.</span><span class="sxs-lookup"><span data-stu-id="0aa25-120">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="0aa25-121">Farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0aa25-121">The differences are as follows:</span></span>

- <span data-ttu-id="0aa25-122">Lambda ifadesinin adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="0aa25-122">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="0aa25-123">Lambda ifadelerinin veya gibi değiştiriciler olamaz `Overloads` `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-123">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="0aa25-124">Tek satırlık Lambda işlevleri `As` , dönüş türünü belirlemek için bir yan tümce kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-124">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="0aa25-125">Bunun yerine, tür lambda ifadesinin gövdesinin değerlendirilen değerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="0aa25-125">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="0aa25-126">Örneğin, lambda ifadesinin gövdesi ise, `cust.City = "London"` dönüş türü olur `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-126">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="0aa25-127">Çok satırlı lambda işlevlerinde, bir yan tümce kullanarak bir dönüş türü belirtebilir `As` veya `As` dönüş türünün çıkarsanabilmesi için yan tümceyi atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-127">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="0aa25-128">`As`Bir çok satırlı Lambda işlevi için yan tümce atlandığında, dönüş türü, `Return` çok satırlı lambda işlevindeki tüm deyimlerden baskın tür olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="0aa25-128">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="0aa25-129">*Baskın tür* , diğer tüm türlerin genişletip benzersiz bir türdür.</span><span class="sxs-lookup"><span data-stu-id="0aa25-129">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="0aa25-130">Bu benzersiz tür belirlenemiyorsa, baskın tür, dizideki diğer tüm türlerin daraltabileceği benzersiz türdür.</span><span class="sxs-lookup"><span data-stu-id="0aa25-130">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="0aa25-131">Bu benzersiz türlerden hiçbiri belirlenemiyorsa, baskın tür olur `Object` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-131">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="0aa25-132">Bu durumda, `Option Strict` olarak ayarlandıysa `On` , bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="0aa25-132">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="0aa25-133">Örneğin, deyimi için sağlanan ifadeler `Return` , ve türünde değerler içeriyorsa, sonuç olarak `Integer` `Long` `Double` elde edilen dizi türüdür `Double` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-133">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="0aa25-134">Her ikisi ve `Integer` `Long` `Double` yalnızca ve ' a kadar `Double` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-134">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="0aa25-135">Bu nedenle, `Double` baskın türdür.</span><span class="sxs-lookup"><span data-stu-id="0aa25-135">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="0aa25-136">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="0aa25-136">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="0aa25-137">Tek satırlık bir işlevin gövdesi bir deyim değil, bir değer döndüren bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0aa25-137">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="0aa25-138">`Return`Tek satır işlevleri için bir ifade yoktur.</span><span class="sxs-lookup"><span data-stu-id="0aa25-138">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="0aa25-139">Tek satır işlevi tarafından döndürülen değer, işlevin gövdesinde ifadenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-139">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="0aa25-140">Tek satırlık alt yordamın gövdesi tek satırlık bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0aa25-140">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="0aa25-141">Tek satırlı işlevler ve alt yordamlar bir `End Function` veya `End Sub` ifadesini içermez.</span><span class="sxs-lookup"><span data-stu-id="0aa25-141">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="0aa25-142">Anahtar sözcüğünü kullanarak bir lambda ifadesi parametresinin veri türünü belirtebilir `As` veya parametresinin veri türü çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="0aa25-142">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="0aa25-143">Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0aa25-143">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="0aa25-144">`Optional` ve `Paramarray` parametrelerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="0aa25-144">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="0aa25-145">Genel parametrelere izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="0aa25-145">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="0aa25-146">Zaman Uyumsuz Lambdalar</span><span class="sxs-lookup"><span data-stu-id="0aa25-146">Async Lambdas</span></span>

<span data-ttu-id="0aa25-147">[Async](../../../language-reference/modifiers/async.md) ve [Await işleci](../../../language-reference/operators/await-operator.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-147">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../language-reference/modifiers/async.md) and [Await Operator](../../../language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="0aa25-148">Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi çağıran ve bekleden bir olay işleyicisi içerir `ExampleMethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-148">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="0aa25-149">Bir [AddHandler ifadesinde](../../../language-reference/statements/addhandler-statement.md)zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-149">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="0aa25-150">Bu işleyiciyi eklemek için `Async` Aşağıdaki örnekte gösterildiği gibi Lambda parametre listesinden önce bir değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0aa25-150">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

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

<span data-ttu-id="0aa25-151">Zaman uyumsuz yöntemlerin nasıl oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="0aa25-151">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="0aa25-152">Bağlam</span><span class="sxs-lookup"><span data-stu-id="0aa25-152">Context</span></span>

<span data-ttu-id="0aa25-153">Lambda ifadesi bağlamını kapsam içinde paylaşır.</span><span class="sxs-lookup"><span data-stu-id="0aa25-153">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="0aa25-154">Bu, kapsayan kapsamda yazılan kod ile aynı erişim haklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-154">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="0aa25-155">Bu, üye değişkenlerine, işlevlere ve alt öğeleri, `Me` ve parametreleri ve kapsayan kapsamdaki yerel değişkenlere erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-155">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="0aa25-156">Yerel değişkenlere ve kapsayan kapsamdaki parametrelere erişim, bu kapsamın yaşam süresinden daha fazla uzatabilirler.</span><span class="sxs-lookup"><span data-stu-id="0aa25-156">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="0aa25-157">Lambda ifadesine başvuran bir temsilci çöp toplama için kullanılabilir olmadığından, özgün ortamdaki değişkenlere erişim korunur.</span><span class="sxs-lookup"><span data-stu-id="0aa25-157">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="0aa25-158">Aşağıdaki örnekte, değişkeni `target` yereldir `makeTheGame` , lambda ifadesinin `playTheGame` tanımlandığı yöntem.</span><span class="sxs-lookup"><span data-stu-id="0aa25-158">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="0aa25-159">İçinde öğesine atanan döndürülen lambda ifadesinin `takeAGuess` `Main` yerel değişkene hala erişimi olduğunu unutmayın `target` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-159">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="0aa25-160">Aşağıdaki örnek, iç içe lambda ifadesinin çok çeşitli erişim haklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-160">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="0aa25-161">Döndürülen lambda ifadesi sürümünden yürütüldüğünde `Main` `aDel` , şu öğelere erişir:</span><span class="sxs-lookup"><span data-stu-id="0aa25-161">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="0aa25-162">İçinde tanımlandığı sınıfın alanı: `aField`</span><span class="sxs-lookup"><span data-stu-id="0aa25-162">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="0aa25-163">İçinde tanımlandığı sınıfın bir özelliği: `aProp`</span><span class="sxs-lookup"><span data-stu-id="0aa25-163">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="0aa25-164">Tanımlı yöntemin parametresi `functionWithNestedLambda` : `level1`</span><span class="sxs-lookup"><span data-stu-id="0aa25-164">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="0aa25-165">Yerel değişkeni `functionWithNestedLambda` : `localVar`</span><span class="sxs-lookup"><span data-stu-id="0aa25-165">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="0aa25-166">İçinde iç içe yerleştirilmiş olan lambda ifadesinin parametresi: `level2`</span><span class="sxs-lookup"><span data-stu-id="0aa25-166">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="0aa25-167">Temsilci türüne dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0aa25-167">Converting to a Delegate Type</span></span>

<span data-ttu-id="0aa25-168">Lambda ifadesi örtük olarak uyumlu bir temsilci türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-168">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="0aa25-169">Uyumluluk için genel gereksinimler hakkında daha fazla bilgi için bkz. [gevşek temsilci dönüştürme](../delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="0aa25-169">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="0aa25-170">Örneğin, aşağıdaki kod örneği dolaylı olarak `Func(Of Integer, Boolean)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-170">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="0aa25-171">Aşağıdaki kod örneği, örtülü olarak `Sub(Of Double, String, Double)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0aa25-171">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="0aa25-172">Temsilcilere lambda ifadeleri atadığınızda veya bunları yordamlara bağımsız değişkenler olarak geçirdiğinizde, parametre adlarını belirtebilir, ancak veri türlerini atlayabilirsiniz, böylece türlerin temsilciden alınmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-172">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="0aa25-173">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0aa25-173">Examples</span></span>

- <span data-ttu-id="0aa25-174">Aşağıdaki örnek, `True` null yapılabilir değer türü bağımsız değişkenine atanan bir değer varsa ve değeri ise döndüren bir lambda ifadesini tanımlar `False` `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="0aa25-174">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="0aa25-175">Aşağıdaki örnek, bir dizideki son öğenin dizinini döndüren bir lambda ifadesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0aa25-175">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="0aa25-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0aa25-176">See also</span></span>

- [<span data-ttu-id="0aa25-177">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0aa25-177">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0aa25-178">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="0aa25-178">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="0aa25-179">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="0aa25-179">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="0aa25-180">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="0aa25-180">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="0aa25-181">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="0aa25-181">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="0aa25-182">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="0aa25-182">Nullable Value Types</span></span>](../data-types/nullable-value-types.md)
- [<span data-ttu-id="0aa25-183">Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme</span><span class="sxs-lookup"><span data-stu-id="0aa25-183">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="0aa25-184">Nasıl yapılır: Lambda İfadesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0aa25-184">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="0aa25-185">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0aa25-185">Relaxed Delegate Conversion</span></span>](../delegates/relaxed-delegate-conversion.md)

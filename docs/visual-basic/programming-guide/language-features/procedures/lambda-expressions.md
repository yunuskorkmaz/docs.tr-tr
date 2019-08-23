---
title: Lambda İfadeleri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: e688beac18e782367bf39ddec8339df2b2735225
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928900"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="fa3c7-102">Lambda İfadeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa3c7-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="fa3c7-103">*Lambda ifadesi* , bir temsilcinin geçerli olduğu her yerde kullanılabilecek bir ada sahip olmayan bir işlev veya alt yordam 'dir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="fa3c7-104">Lambda ifadeleri işlevler veya alt yordamlar olabilir ve tek satırlık veya çok satırlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="fa3c7-105">Geçerli kapsamdan bir lambda ifadesine değer geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa3c7-106">`RemoveHandler` İfade bir özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="fa3c7-107">Temsilci parametresi `RemoveHandler`için içinde bir lambda ifadesi geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="fa3c7-108">Bir standart işlev veya alt yordam oluştururken `Function` olduğu `Sub` gibi, veya anahtar sözcüğünü kullanarak lambda ifadeleri oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="fa3c7-109">Ancak, lambda ifadeleri bir ifadeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="fa3c7-110">Aşağıdaki örnek, bağımsız değişkenini artıran ve değeri döndüren bir lambda ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="fa3c7-111">Örnek, bir işlev için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 <span data-ttu-id="fa3c7-112">Aşağıdaki örnek, konsoluna bir değer yazan bir lambda ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="fa3c7-113">Örnek, bir altyordam için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 <span data-ttu-id="fa3c7-114">Önceki örneklerde lambda ifadelerinin bir değişken adına atandığını fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="fa3c7-115">Değişkenine başvurduğunuzda, lambda ifadesini çağırılır.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="fa3c7-116">Ayrıca, aşağıdaki örnekte gösterildiği gibi bir lambda ifadesini aynı anda bildirebilir ve çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 <span data-ttu-id="fa3c7-117">Bir lambda ifadesi, bir işlev çağrısının değeri olarak döndürülebilir (Bu konunun ilerleyen bölümlerinde yer alan [bağlam](#context) bölümünde gösterildiği gibi) veya aşağıdaki örnekte gösterildiği gibi bir temsilci türü alan parametreye bağımsız değişken olarak geçirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="fa3c7-118">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa3c7-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="fa3c7-119">Bir lambda ifadesinin sözdizimi, standart bir işlev veya alt yordamın sözdizimine benzer.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="fa3c7-120">Farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fa3c7-120">The differences are as follows:</span></span>  
  
- <span data-ttu-id="fa3c7-121">Lambda ifadesinin adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-121">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="fa3c7-122">Lambda ifadelerinin `Overloads` veya `Overrides`gibi değiştiriciler olamaz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="fa3c7-123">Tek satırlık Lambda işlevleri, dönüş türünü belirlemek için `As` bir yan tümce kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="fa3c7-124">Bunun yerine, tür lambda ifadesinin gövdesinin değerlendirilen değerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="fa3c7-125">Örneğin, lambda ifadesinin gövdesi ise `cust.City = "London"`, dönüş türü olur. `Boolean`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="fa3c7-126">Çok satırlı lambda işlevlerinde, bir `As` yan tümce kullanarak bir dönüş türü belirtebilir veya dönüş türünün çıkarsanabilmesi için `As` yan tümceyi atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="fa3c7-127">Bir çok satırlı Lambda işlevi için `Return` yantümceatlandığında,dönüştürü,çoksatırlılambdaişlevindekitümdeyimlerdenbaskıntürolarakalgılanır.`As`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="fa3c7-128">*Baskın tür* , diğer tüm türlerin genişletip benzersiz bir türdür.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="fa3c7-129">Bu benzersiz tür belirlenemiyorsa, baskın tür, dizideki diğer tüm türlerin daraltabileceği benzersiz türdür.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="fa3c7-130">Bu benzersiz türlerden hiçbiri belirlenemiyorsa, baskın tür olur `Object`.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="fa3c7-131">Bu durumda `Option Strict` , olarak `On`ayarlandıysa, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="fa3c7-132">Örneğin `Return` , deyimi için sağlanan ifadeler, `Long`ve `Double`türünde `Integer`değerler içeriyorsa, sonuç olarak elde edilen dizi türüdür `Double`.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="fa3c7-133">Her ikisi `Integer` ve `Double` yalnızca ve`Double`'akadar. `Long`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="fa3c7-134">Bu nedenle `Double` , baskın türdür.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="fa3c7-135">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="fa3c7-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
- <span data-ttu-id="fa3c7-136">Tek satırlık bir işlevin gövdesi bir deyim değil, bir değer döndüren bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="fa3c7-137">Tek satır işlevleri için bir ifadeyoktur.`Return`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="fa3c7-138">Tek satır işlevi tarafından döndürülen değer, işlevin gövdesinde ifadenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
- <span data-ttu-id="fa3c7-139">Tek satırlık alt yordamın gövdesi tek satırlık bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
- <span data-ttu-id="fa3c7-140">Tek satırlı işlevler ve alt yordamlar bir `End Function` veya `End Sub` ifadesini içermez.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="fa3c7-141">`As` Anahtar sözcüğünü kullanarak bir lambda ifadesi parametresinin veri türünü belirtebilir veya parametresinin veri türü çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="fa3c7-142">Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="fa3c7-143">`Optional`ve `Paramarray` parametrelerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
- <span data-ttu-id="fa3c7-144">Genel parametrelere izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="fa3c7-145">Zaman Uyumsuz Lambdalar</span><span class="sxs-lookup"><span data-stu-id="fa3c7-145">Async Lambdas</span></span>  
 <span data-ttu-id="fa3c7-146">[Async](../../../../visual-basic/language-reference/modifiers/async.md) ve [Await işleci](../../../../visual-basic/language-reference/operators/await-operator.md) anahtar sözcüklerini kullanarak zaman uyumsuz işleme içeren lambda ifadeleri ve deyimlerini kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="fa3c7-147">Örneğin, aşağıdaki Windows Forms örnek, zaman uyumsuz bir yöntemi `ExampleMethodAsync`çağıran ve bekleden bir olay işleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="fa3c7-148">Bir [AddHandler ifadesinde](../../../../visual-basic/language-reference/statements/addhandler-statement.md)zaman uyumsuz lambda kullanarak aynı olay işleyicisini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="fa3c7-149">Bu işleyiciyi eklemek için aşağıdaki örnekte gösterildiği `Async` gibi Lambda parametre listesinden önce bir değiştirici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="fa3c7-150">Zaman uyumsuz yöntemlerin nasıl oluşturulacağı ve kullanılacağı hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="fa3c7-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="context"></a><span data-ttu-id="fa3c7-151">Bağlam</span><span class="sxs-lookup"><span data-stu-id="fa3c7-151">Context</span></span>  
 <span data-ttu-id="fa3c7-152">Lambda ifadesi bağlamını kapsam içinde paylaşır.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="fa3c7-153">Bu, kapsayan kapsamda yazılan kod ile aynı erişim haklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="fa3c7-154">Bu, üye değişkenlerine, işlevlere ve alt öğeleri `Me`, ve parametreleri ve kapsayan kapsamdaki yerel değişkenlere erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="fa3c7-155">Yerel değişkenlere ve kapsayan kapsamdaki parametrelere erişim, bu kapsamın yaşam süresinden daha fazla uzatabilirler.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="fa3c7-156">Lambda ifadesine başvuran bir temsilci çöp toplama için kullanılabilir olmadığından, özgün ortamdaki değişkenlere erişim korunur.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="fa3c7-157">Aşağıdaki örnekte, değişkeni `target` `makeTheGame`yereldir, lambda ifadesinin `playTheGame` tanımlandığı yöntem.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="fa3c7-158">`target`İçinde `takeAGuess` öğesineatanandöndürülenlambdaifadesininyereldeğişkenehalaerişimiolduğunuunutmayın.`Main`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 <span data-ttu-id="fa3c7-159">Aşağıdaki örnek, iç içe lambda ifadesinin çok çeşitli erişim haklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="fa3c7-160">Döndürülen lambda ifadesi sürümünden `Main` `aDel`yürütüldüğünde, şu öğelere erişir:</span><span class="sxs-lookup"><span data-stu-id="fa3c7-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
- <span data-ttu-id="fa3c7-161">İçinde tanımlandığı sınıfın alanı:`aField`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-161">A field of the class in which it is defined: `aField`</span></span>  
  
- <span data-ttu-id="fa3c7-162">İçinde tanımlandığı sınıfın bir özelliği:`aProp`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-162">A property of the class in which it is defined: `aProp`</span></span>  
  
- <span data-ttu-id="fa3c7-163">Tanımlı yöntemin `functionWithNestedLambda`parametresi:`level1`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
- <span data-ttu-id="fa3c7-164">Yerel değişkeni `functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
- <span data-ttu-id="fa3c7-165">İçinde iç içe yerleştirilmiş olan lambda ifadesinin parametresi:`level2`</span><span class="sxs-lookup"><span data-stu-id="fa3c7-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="fa3c7-166">Temsilci türüne dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fa3c7-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="fa3c7-167">Lambda ifadesi örtük olarak uyumlu bir temsilci türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="fa3c7-168">Uyumluluk için genel gereksinimler hakkında daha fazla bilgi için bkz. [gevşek temsilci dönüştürme](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="fa3c7-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="fa3c7-169">Örneğin, aşağıdaki kod örneği dolaylı olarak `Func(Of Integer, Boolean)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 <span data-ttu-id="fa3c7-170">Aşağıdaki kod örneği, örtülü olarak `Sub(Of Double, String, Double)` veya eşleşen bir temsilci imzasına dönüştüren bir lambda ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 <span data-ttu-id="fa3c7-171">Temsilcilere lambda ifadeleri atadığınızda veya bunları yordamlara bağımsız değişkenler olarak geçirdiğinizde, parametre adlarını belirtebilir, ancak veri türlerini atlayabilirsiniz, böylece türlerin temsilciden alınmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fa3c7-172">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fa3c7-172">Examples</span></span>  
  
- <span data-ttu-id="fa3c7-173">Aşağıdaki örnek, null atanabilir bağımsız değişkeni atanan bir `True` değere sahipse ve `False` değeri ise `Nothing`, döndüren bir lambda ifadesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
- <span data-ttu-id="fa3c7-174">Aşağıdaki örnek, bir dizideki son öğenin dizinini döndüren bir lambda ifadesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="fa3c7-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa3c7-175">See also</span></span>

- [<span data-ttu-id="fa3c7-176">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="fa3c7-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fa3c7-177">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="fa3c7-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="fa3c7-178">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="fa3c7-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="fa3c7-179">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="fa3c7-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="fa3c7-180">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="fa3c7-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="fa3c7-181">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="fa3c7-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="fa3c7-182">Nasıl yapılır: Yordamları Visual Basic başka bir yordama geçirin</span><span class="sxs-lookup"><span data-stu-id="fa3c7-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="fa3c7-183">Nasıl yapılır: Lambda Ifadesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa3c7-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="fa3c7-184">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fa3c7-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)

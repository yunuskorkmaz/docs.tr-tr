---
title: Alt yordamlar
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 9ca1d302a0bc8e989e0b2dddf8cce68e89211d57
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163819"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="97c06-102">Alt yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97c06-102">Sub procedures (Visual Basic)</span></span>

<span data-ttu-id="97c06-103">`Sub` yordam, `Sub` ve `End Sub` deyimlerinin içine alınmış Visual Basic deyimlerinin bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="97c06-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="97c06-104">`Sub` yordamı bir görevi gerçekleştirir ve ardından çağıran koda denetim döndürür, ancak çağıran koda bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="97c06-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>

<span data-ttu-id="97c06-105">Yordam her çağrıldığında, `Sub` deyiminden sonra ilk yürütülebilir deyimden başlayıp ilk `End Sub`, `Exit Sub`veya `Return` ifadesiyle biten deyimleri yürütülür.</span><span class="sxs-lookup"><span data-stu-id="97c06-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>

<span data-ttu-id="97c06-106">Modüller, sınıflar ve yapılar için bir `Sub` yordamı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c06-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="97c06-107">Varsayılan olarak `Public`, bu, sizin tanımladığınız modüle, sınıfa veya yapıya erişimi olan uygulamanızdaki herhangi bir yerden çağırabilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="97c06-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="97c06-108">Terim *yöntemi* , tanımlama modülünün, sınıfın veya yapının dışından erişilen bir `Sub` veya `Function` yordamını açıklar.</span><span class="sxs-lookup"><span data-stu-id="97c06-108">The term *method* describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="97c06-109">Daha fazla bilgi için bkz. [yordamlar](./index.md).</span><span class="sxs-lookup"><span data-stu-id="97c06-109">For more information, see [Procedures](./index.md).</span></span>

<span data-ttu-id="97c06-110">`Sub` yordam, çağıran kod tarafından buna geçirilen sabitler, değişkenler veya ifadeler gibi bağımsız değişkenler alabilir.</span><span class="sxs-lookup"><span data-stu-id="97c06-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="97c06-111">Bildirim söz dizimi</span><span class="sxs-lookup"><span data-stu-id="97c06-111">Declaration syntax</span></span>

<span data-ttu-id="97c06-112">`Sub` yordamı bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97c06-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

<span data-ttu-id="97c06-113">`modifiers`, erişim düzeyini ve aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme hakkında bilgileri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="97c06-113">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="97c06-114">Daha fazla bilgi için bkz. [Sub deyimidir](../../../language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="97c06-114">For more information, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="97c06-115">Parametre bildirimi</span><span class="sxs-lookup"><span data-stu-id="97c06-115">Parameter declaration</span></span>

<span data-ttu-id="97c06-116">Her yordam parametresini, parametre adını ve veri türünü belirterek bir değişkeni nasıl bildirdiğinizin benzer şekilde bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c06-116">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="97c06-117">Ayrıca, geçen mekanizmayı ve parametrenin isteğe bağlı veya bir parametre dizisi olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c06-117">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>

<span data-ttu-id="97c06-118">Parametre listesindeki her bir parametre için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97c06-118">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

<span data-ttu-id="97c06-119">Parametre isteğe bağlı ise, bildiriminin bir parçası olarak bir varsayılan değer de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="97c06-119">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="97c06-120">Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97c06-120">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a><span data-ttu-id="97c06-121">Yerel değişkenler olarak parametreler</span><span class="sxs-lookup"><span data-stu-id="97c06-121">Parameters as local variables</span></span>

<span data-ttu-id="97c06-122">Denetim yordama geçtiğinde, her bir parametre yerel bir değişken olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="97c06-122">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="97c06-123">Bu, yaşam süresinin prosedürünyle aynı olduğu ve kapsamı tüm yordam olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="97c06-123">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="97c06-124">Çağırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97c06-124">Calling syntax</span></span>

<span data-ttu-id="97c06-125">Tek başına çağırma ifadesiyle bir `Sub` yordamını açık olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c06-125">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="97c06-126">Bir ifadede adını kullanarak çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="97c06-126">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="97c06-127">İsteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız gerekir ve bağımsız değişken listesini parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="97c06-127">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="97c06-128">Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c06-128">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="97c06-129">`Call` anahtar sözcüğünün kullanımı isteğe bağlıdır, ancak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="97c06-129">The use of the `Call` keyword is optional but not recommended.</span></span>

<span data-ttu-id="97c06-130">`Sub` yordam çağrısı için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97c06-130">The syntax for a call to a `Sub` procedure is as follows:</span></span>

```vb
[Call] SubName[(argumentlist)]
```

<span data-ttu-id="97c06-131">Bir `Sub` yöntemi, kendisini tanımlayan sınıfın dışından çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c06-131">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="97c06-132">İlk olarak, sınıfının bir örneğini oluşturmak veya sınıfının bir örneğini döndüren bir yöntemi çağırmak için `New` anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="97c06-132">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="97c06-133">Daha fazla bilgi için bkz. [New Operator](../../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="97c06-133">For more information, see [New Operator](../../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="97c06-134">Ardından, örnek nesnesinde `Sub` yöntemini çağırmak için aşağıdaki sözdizimini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="97c06-134">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="97c06-135">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="97c06-135">Illustration of declaration and call</span></span>

<span data-ttu-id="97c06-136">Aşağıdaki `Sub` yordam, bilgisayar işlecine uygulamanın hangi görevi gerçekleştirmesini söyler ve ayrıca bir zaman damgası görüntüler.</span><span class="sxs-lookup"><span data-stu-id="97c06-136">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="97c06-137">Her görevin başlangıcında bu kodu çoğaltmak yerine, uygulama yalnızca çeşitli konumlardan `tellOperator` çağırır.</span><span class="sxs-lookup"><span data-stu-id="97c06-137">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="97c06-138">Her çağrı, başlatılmakta olan görevi tanımlayan `task` bağımsız değişkeninde bir dize geçirir.</span><span class="sxs-lookup"><span data-stu-id="97c06-138">Each call passes a string in the `task` argument that identifies the task being started.</span></span>

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

<span data-ttu-id="97c06-139">Aşağıdaki örnek `tellOperator`tipik bir çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97c06-139">The following example shows a typical call to `tellOperator`.</span></span>

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="97c06-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97c06-140">See also</span></span>

- [<span data-ttu-id="97c06-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="97c06-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="97c06-142">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="97c06-142">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="97c06-143">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="97c06-143">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="97c06-144">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="97c06-144">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="97c06-145">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="97c06-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="97c06-146">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="97c06-146">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="97c06-147">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="97c06-147">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="97c06-148">Nasıl yapılır: Visual Basic bir olay Işleyicisini çağırma</span><span class="sxs-lookup"><span data-stu-id="97c06-148">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)

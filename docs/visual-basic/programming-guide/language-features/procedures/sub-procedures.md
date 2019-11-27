---
title: Alt Yordamlar
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
ms.openlocfilehash: 7848dc07d6462622685cdbea92202585f4d5d2c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352530"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="ca91b-102">Alt Yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca91b-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="ca91b-103">`Sub` yordam, `Sub` ve `End Sub` deyimlerinin içine alınmış Visual Basic deyimlerinin bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="ca91b-104">`Sub` yordamı bir görevi gerçekleştirir ve ardından çağıran koda denetim döndürür, ancak çağıran koda bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="ca91b-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="ca91b-105">Yordam her çağrıldığında, `Sub` deyiminden sonra ilk yürütülebilir deyimden başlayıp ilk `End Sub`, `Exit Sub`veya `Return` ifadesiyle biten deyimleri yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ca91b-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="ca91b-106">Modüller, sınıflar ve yapılar için bir `Sub` yordamı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca91b-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="ca91b-107">Varsayılan olarak `Public`, bu, sizin tanımladığınız modüle, sınıfa veya yapıya erişimi olan uygulamanızdaki herhangi bir yerden çağırabilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="ca91b-108">*Yöntemi*, tanımlama modülünün, sınıfın veya yapının dışından erişilen bir `Sub` veya `Function` yordamını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca91b-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="ca91b-109">Daha fazla bilgi için bkz. [yordamlar](./index.md).</span><span class="sxs-lookup"><span data-stu-id="ca91b-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="ca91b-110">`Sub` yordam, çağıran kod tarafından buna geçirilen sabitler, değişkenler veya ifadeler gibi bağımsız değişkenler alabilir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="ca91b-111">Bildirim Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="ca91b-111">Declaration Syntax</span></span>  
 <span data-ttu-id="ca91b-112">`Sub` yordamı bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ca91b-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="ca91b-113">`[` *değiştiriciler* `] Sub`*subname* `[(` *parameterlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="ca91b-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="ca91b-114">`modifiers`, erişim düzeyini ve aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme hakkında bilgileri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="ca91b-115">Daha fazla bilgi için bkz. [Sub deyimidir](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ca91b-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="ca91b-116">Parametre bildirimi</span><span class="sxs-lookup"><span data-stu-id="ca91b-116">Parameter Declaration</span></span>  
 <span data-ttu-id="ca91b-117">Her yordam parametresini, parametre adını ve veri türünü belirterek bir değişkeni nasıl bildirdiğinizin benzer şekilde bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca91b-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="ca91b-118">Ayrıca, geçen mekanizmayı ve parametrenin isteğe bağlı veya bir parametre dizisi olduğunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca91b-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="ca91b-119">Parametre listesindeki her bir parametre için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ca91b-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="ca91b-120">`[Optional] [ByVal | ByRef] [ParamArray]`*parametername*`As`*DataType*</span><span class="sxs-lookup"><span data-stu-id="ca91b-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="ca91b-121">Parametre isteğe bağlı ise, bildiriminin bir parçası olarak bir varsayılan değer de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="ca91b-122">Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ca91b-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="ca91b-123">`Optional [ByVal | ByRef]`*parametername*`As`*DataType*`=`*DefaultValue*</span><span class="sxs-lookup"><span data-stu-id="ca91b-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="ca91b-124">Yerel değişkenler olarak parametreler</span><span class="sxs-lookup"><span data-stu-id="ca91b-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="ca91b-125">Denetim yordama geçtiğinde, her bir parametre yerel bir değişken olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="ca91b-126">Bu, yaşam süresinin prosedürünyle aynı olduğu ve kapsamı tüm yordam olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="ca91b-127">Çağırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca91b-127">Calling Syntax</span></span>  
 <span data-ttu-id="ca91b-128">Tek başına çağırma ifadesiyle bir `Sub` yordamını açık olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca91b-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="ca91b-129">Bir ifadede adını kullanarak çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="ca91b-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="ca91b-130">İsteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız gerekir ve bağımsız değişken listesini parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="ca91b-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="ca91b-131">Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca91b-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="ca91b-132">`Call` anahtar sözcüğünün kullanımı isteğe bağlıdır, ancak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ca91b-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="ca91b-133">`Sub` yordam çağrısı için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ca91b-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="ca91b-134">`[Call]`*subname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="ca91b-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="ca91b-135">Bir `Sub` yöntemi, kendisini tanımlayan sınıfın dışından çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca91b-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="ca91b-136">İlk olarak, sınıfının bir örneğini oluşturmak veya sınıfının bir örneğini döndüren bir yöntemi çağırmak için `New` anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="ca91b-137">Daha fazla bilgi için bkz. [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ca91b-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="ca91b-138">Ardından, örnek nesnesinde `Sub` yöntemini çağırmak için aşağıdaki sözdizimini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ca91b-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="ca91b-139">*Nesne*. *methodname*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="ca91b-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="ca91b-140">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="ca91b-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="ca91b-141">Aşağıdaki `Sub` yordam, bilgisayar işlecine uygulamanın hangi görevi gerçekleştirmesini söyler ve ayrıca bir zaman damgası görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ca91b-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="ca91b-142">Her görevin başlangıcında bu kodu çoğaltmak yerine, uygulama yalnızca çeşitli konumlardan `tellOperator` çağırır.</span><span class="sxs-lookup"><span data-stu-id="ca91b-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="ca91b-143">Her çağrı, başlatılmakta olan görevi tanımlayan `task` bağımsız değişkeninde bir dize geçirir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ca91b-144">Aşağıdaki örnek `tellOperator`tipik bir çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca91b-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ca91b-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca91b-145">See also</span></span>

- [<span data-ttu-id="ca91b-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ca91b-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ca91b-147">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="ca91b-147">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="ca91b-148">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="ca91b-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="ca91b-149">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="ca91b-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="ca91b-150">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ca91b-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ca91b-151">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="ca91b-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ca91b-152">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="ca91b-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="ca91b-153">Nasıl yapılır: Visual Basic bir olay Işleyicisini çağırma</span><span class="sxs-lookup"><span data-stu-id="ca91b-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)

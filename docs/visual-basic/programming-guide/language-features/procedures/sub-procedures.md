---
title: Alt Yordamlar (Visual Basic)
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
ms.openlocfilehash: b70594e002bbf08f0890586e78df901ccb26c7ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843116"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="46c98-102">Alt Yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46c98-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="46c98-103">A `Sub` yordamdır kapsadığı Visual Basic deyimleri bir dizi `Sub` ve `End Sub` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="46c98-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="46c98-104">`Sub` Yordamı bir görevi gerçekleştirir ve çağıran koda denetim döndürür, ancak çağrıldığı koda bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="46c98-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="46c98-105">Yordam çağrıldığında, her zaman kendi deyimleri, sonra yürütülebilir ilk deyimi'ile başlayan yürütülür `Sub` deyimi ve ilk görmektesiniz `End Sub`, `Exit Sub`, veya `Return` deyimiyle karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="46c98-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="46c98-106">Tanımlayabileceğiniz bir `Sub` modülleri, sınıfları ve yapıları yordamda.</span><span class="sxs-lookup"><span data-stu-id="46c98-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="46c98-107">Varsayılan olarak, olduğu `Public`, anlamına yerden çağırabilirsiniz uygulamanızdaki modül, sınıf veya yapının, tanımlandığı da erişebilir.</span><span class="sxs-lookup"><span data-stu-id="46c98-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="46c98-108">Terim *yöntemi*, açıklayan bir `Sub` veya `Function` kendi tanımlama dışından erişilen gelen yordamı modül, sınıf veya yapı.</span><span class="sxs-lookup"><span data-stu-id="46c98-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="46c98-109">Daha fazla bilgi için [yordamları](./index.md).</span><span class="sxs-lookup"><span data-stu-id="46c98-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="46c98-110">A `Sub` yordamı, sabitleri, değişkenleri veya kendisine çağıran kod tarafından geçirilen ifadeler gibi bir bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="46c98-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="46c98-111">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46c98-111">Declaration Syntax</span></span>  
 <span data-ttu-id="46c98-112">Bildirmek için söz dizimi bir `Sub` yordam şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="46c98-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="46c98-113">`[` *değiştiriciler* `] Sub` *subname* `[(` *parameterlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="46c98-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="46c98-114">`modifiers` Erişim düzeyi ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve gölgeleme hakkında bilgileri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46c98-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="46c98-115">Daha fazla bilgi için [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="46c98-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="46c98-116">Parametre bildirimi</span><span class="sxs-lookup"><span data-stu-id="46c98-116">Parameter Declaration</span></span>  
 <span data-ttu-id="46c98-117">Size nasıl parametre adı ile veri türünü belirten bir değişken bildirmek için benzer şekilde, her yordam parametresinin bildirin.</span><span class="sxs-lookup"><span data-stu-id="46c98-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="46c98-118">Geçirme mekanizması belirtebilirsiniz ve parametrenin isteğe bağlı olduğundan veya bir parametre dizisi.</span><span class="sxs-lookup"><span data-stu-id="46c98-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="46c98-119">Parametre listesindeki her parametre için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="46c98-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="46c98-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*veri türü*</span><span class="sxs-lookup"><span data-stu-id="46c98-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="46c98-121">Parametre isteğe bağlıysa, varsayılan değer bildiriminin bir parçası olarak da belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46c98-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="46c98-122">Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="46c98-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="46c98-123">`Optional [ByVal | ByRef]`  *parametername*`As`*datatype*`=`*defaultvalue*</span><span class="sxs-lookup"><span data-stu-id="46c98-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="46c98-124">Yerel değişkenleri olarak Parametreler</span><span class="sxs-lookup"><span data-stu-id="46c98-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="46c98-125">Her bir parametre, yordama denetimi başarılı olduğunda, yerel bir değişken olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="46c98-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="46c98-126">Bu, yaşam süresi yordamın aynıdır ve kapsamı bütün bir yordamdır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="46c98-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="46c98-127">Arama söz dizimi</span><span class="sxs-lookup"><span data-stu-id="46c98-127">Calling Syntax</span></span>  
 <span data-ttu-id="46c98-128">Çağırdığınızda bir `Sub` açıkça tek başına bir deyim çağırma yordamı.</span><span class="sxs-lookup"><span data-stu-id="46c98-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="46c98-129">Adı bir ifade kullanarak çağrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="46c98-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="46c98-130">İsteğe bağlı olmayan tüm bağımsız değişkenler için değerler sağlaması gerekir ve bağımsız değişken listesi parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="46c98-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="46c98-131">Hiçbir bağımsız değişken sağlanmadıysa, parantezler isteğe bağlı olarak atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46c98-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="46c98-132">Kullanımını `Call` anahtar sözcüğü isteğe bağlıdır, ancak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="46c98-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="46c98-133">Bir çağrı sözdizimi bir `Sub` yordam şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="46c98-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="46c98-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="46c98-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="46c98-135">Çağırabilirsiniz bir `Sub` yöntemi tanımlayan bir sınıf dışında.</span><span class="sxs-lookup"><span data-stu-id="46c98-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="46c98-136">İlk olarak kullanmak zorunda `New` sınıfının bir örneğini oluşturmak veya, bir yöntem çağırmak için anahtar sözcüğü bir sınıf örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="46c98-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="46c98-137">Daha fazla bilgi için [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="46c98-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="46c98-138">Ardından çağırmak için aşağıdaki söz dizimini kullanabilirsiniz `Sub` örneği nesnesi üzerinde yöntemi:</span><span class="sxs-lookup"><span data-stu-id="46c98-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="46c98-139">*Nesne*. *MethodName*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="46c98-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="46c98-140">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="46c98-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="46c98-141">Aşağıdaki `Sub` yordamı uygulamasıdır gerçekleştirmek üzere hangi görev bilgisayar işleci bildirir ve ayrıca bir zaman damgasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46c98-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="46c98-142">Bu kod, her görevin başlangıcında çoğaltmak yerine uygulama yalnızca çağırır `tellOperator` çeşitli konumlardan.</span><span class="sxs-lookup"><span data-stu-id="46c98-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="46c98-143">Her çağrı bir dizede geçirir `task` Başlatılmakta olan görevi tanımlayan bir bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="46c98-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="46c98-144">Aşağıdaki örnek, tipik bir çağrı gösterir `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="46c98-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="46c98-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46c98-145">See also</span></span>

- [<span data-ttu-id="46c98-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="46c98-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="46c98-147">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="46c98-147">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="46c98-148">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="46c98-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="46c98-149">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="46c98-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="46c98-150">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="46c98-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="46c98-151">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="46c98-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="46c98-152">Nasıl yapılır: Bir değer döndürmeyen bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="46c98-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="46c98-153">Nasıl yapılır: Visual Basic olay işleyicisi çağırma</span><span class="sxs-lookup"><span data-stu-id="46c98-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)

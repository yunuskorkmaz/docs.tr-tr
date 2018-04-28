---
title: Alt Yordamlar (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7258d57d2677042a2020097893a4f7a0adb35508
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="fb7e4-102">Alt Yordamlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb7e4-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="fb7e4-103">A `Sub` yordamdır bir dizi kapsadığı Visual Basic deyimi `Sub` ve `End Sub` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="fb7e4-104">`Sub` Yordamı bir görevi gerçekleştirir ve çağrıyı yapan kod denetim verir, ancak çağıran kodu için bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="fb7e4-105">Yordam çağrıldığında, her zaman kendi deyimleri, sonra ilk yürütülebilir ifadesiyle başlayan yürütülür `Sub` deyimi ve ilk ile bitiş `End Sub`, `Exit Sub`, veya `Return` deyimiyle karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="fb7e4-106">Tanımlayabileceğiniz bir `Sub` modülleri, sınıfları ve yapıları yordamda.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="fb7e4-107">Varsayılan olarak, olmasından `Public`, anlamına gelir, herhangi bir yerden çağırabilir modülü, sınıf veya yapı içinde tanımlanan bu erişimi, uygulamanızda.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="fb7e4-108">Terim *yöntemi*, açıklayan bir `Sub` veya `Function` kendi tanımlama dışında erişilen gelen yordamı modülü, sınıf veya yapı.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="fb7e4-109">Daha fazla bilgi için bkz: [yordamları](./index.md).</span><span class="sxs-lookup"><span data-stu-id="fb7e4-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="fb7e4-110">A `Sub` yordamı sabitleri, değişkenleri veya kendisine çağrıyı yapan kod tarafından geçirilen ifadeler gibi bağımsız değişkenleri alabilir.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="fb7e4-111">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb7e4-111">Declaration Syntax</span></span>  
 <span data-ttu-id="fb7e4-112">Bildirme sözdizimi bir `Sub` yordam aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fb7e4-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="fb7e4-113">`[` *değiştiriciler* `] Sub` *subname* `[(` *parametreListesi*  `)]`</span><span class="sxs-lookup"><span data-stu-id="fb7e4-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="fb7e4-114">`modifiers` Erişim düzeyini ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve gölgeleme hakkında bilgileri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="fb7e4-115">Daha fazla bilgi için bkz: [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb7e4-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="fb7e4-116">Parametre bildirimi</span><span class="sxs-lookup"><span data-stu-id="fb7e4-116">Parameter Declaration</span></span>  
 <span data-ttu-id="fb7e4-117">Benzer şekilde nasıl parametre adını ve veri türünü belirten bir değişken bildirmek için her yordam parametresini bildirin.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="fb7e4-118">Geçirme mekanizması da belirtebilirsiniz ve parametre isteğe bağlı olup ya da bir parametre dizisi.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="fb7e4-119">Parametre listesindeki her parametre için söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fb7e4-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="fb7e4-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*veri türü* </span><span class="sxs-lookup"><span data-stu-id="fb7e4-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="fb7e4-121">Parametre isteğe bağlı ise, varsayılan değer bildiriminden bir parçası olarak sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="fb7e4-122">Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fb7e4-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="fb7e4-123">`Optional [ByVal | ByRef]`  *parametername*`As`*datatype*`=`*defaultvalue* </span><span class="sxs-lookup"><span data-stu-id="fb7e4-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="fb7e4-124">Yerel değişkenleri olarak Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb7e4-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="fb7e4-125">Denetim yordama geçtiğinde, her bir parametreyi yerel değişken olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="fb7e4-126">Bu yaşam yordamın aynıdır ve tüm yordamı kapsamı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="fb7e4-127">Arama sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb7e4-127">Calling Syntax</span></span>  
 <span data-ttu-id="fb7e4-128">Çağırmayı bir `Sub` açıkça ifadesiyle bir tek başına arama yordamı.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="fb7e4-129">Bir ifadeyi adını kullanarak çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="fb7e4-130">İsteğe bağlı olmayan tüm bağımsız değişkenler için değerler sağlayın ve bağımsız değişken listesi parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="fb7e4-131">Bağımsız değişkenler sağlandıysa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="fb7e4-132">Kullanımını `Call` anahtar sözcüğü isteğe bağlıdır, ancak önerilmez.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="fb7e4-133">Çağrı sözdizimi bir `Sub` yordam aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fb7e4-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="fb7e4-134">`[Call]`  *subname* `[(` *bağımsızdeğişkenListesi* `)]`</span><span class="sxs-lookup"><span data-stu-id="fb7e4-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="fb7e4-135">Arayabileceğiniz bir `Sub` yönteminden tanımladığı sınıfı dışında.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="fb7e4-136">İlk olarak, kullanmak zorunda `New` sınıfının bir örneğini oluşturmak veya bir yöntem çağrısı için anahtar sözcüğü sınıfının bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="fb7e4-137">Daha fazla bilgi için bkz: [yeni işleç](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="fb7e4-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="fb7e4-138">Ardından, çağırmak için aşağıdaki söz dizimini kullanabilirsiniz `Sub` örneği nesnesi üzerinde yöntemi:</span><span class="sxs-lookup"><span data-stu-id="fb7e4-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="fb7e4-139">*Nesne*. *MethodName*`[(`*bağımsızdeğişkenListesi*`)]`</span><span class="sxs-lookup"><span data-stu-id="fb7e4-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="fb7e4-140">Bildirim ve çağrı çizimi</span><span class="sxs-lookup"><span data-stu-id="fb7e4-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="fb7e4-141">Aşağıdaki `Sub` yordamı uygulamasıdır gerçekleştirmek üzere hangi görev bilgisayar işleci bildirir ve ayrıca bir zaman damgasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="fb7e4-142">Bu kodu her görev başlangıcında çoğaltmak yerine uygulama yalnızca çağırır `tellOperator` çeşitli konumlardan.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="fb7e4-143">Bir dizede her çağrı geçirir `task` başlatılmakta görevi tanımlar bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 <span data-ttu-id="fb7e4-144">Aşağıdaki örnek tipik bir çağrı gösterilmektedir `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fb7e4-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb7e4-145">See Also</span></span>  
 [<span data-ttu-id="fb7e4-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="fb7e4-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="fb7e4-147">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="fb7e4-147">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="fb7e4-148">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="fb7e4-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="fb7e4-149">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="fb7e4-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="fb7e4-150">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="fb7e4-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="fb7e4-151">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="fb7e4-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="fb7e4-152">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="fb7e4-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [<span data-ttu-id="fb7e4-153">Nasıl yapılır: Visual Basic'te bir olay işleyicisi çağırma</span><span class="sxs-lookup"><span data-stu-id="fb7e4-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)

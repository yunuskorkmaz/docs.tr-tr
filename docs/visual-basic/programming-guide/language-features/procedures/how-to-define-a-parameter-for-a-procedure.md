---
title: 'Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb4bac9208c03fd18e1904f58b247824d2c215da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="51c1f-102">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51c1f-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="51c1f-103">A *parametresi* onu çağırdığında yordamı için bir değer geçirmek için çağıran kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="51c1f-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="51c1f-104">Bir yordam için her parametre adı ve veri türünü belirten bir değişken bildirin aynı şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="51c1f-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="51c1f-105">Ayrıca geçirme mekanizması belirtin ve parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="51c1f-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="51c1f-106">Daha fazla bilgi için bkz: [parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="51c1f-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="51c1f-107">Bir yordam parametresini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="51c1f-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="51c1f-108">Yordam bildiriminde yordam parametre listesi, diğer parametreler virgül ile ayırarak parametre adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="51c1f-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="51c1f-109">Parametresinin veri türü karar verin.</span><span class="sxs-lookup"><span data-stu-id="51c1f-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="51c1f-110">Parametre adı ile izleyin bir `As` veri türünü belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="51c1f-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="51c1f-111">Parametresi için istediğiniz geçirme mekanizması karar verin.</span><span class="sxs-lookup"><span data-stu-id="51c1f-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="51c1f-112">Normalde, yordamı çağıran kodu değeriyle değiştirebilmesi istediğiniz sürece değer ile bir parametre geçirin.</span><span class="sxs-lookup"><span data-stu-id="51c1f-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="51c1f-113">Parametre adından [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) geçirme düzeneğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="51c1f-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="51c1f-114">Daha fazla bilgi için bkz: [farklar arasında geçirme bir bağımsız değişken değer ve başvuru tarafından](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="51c1f-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="51c1f-115">Parametre isteğe bağlıysa geçirme mekanizmasıyla önünde [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) ve parametre veri türü eşittir işareti ile izleyin (`=`) ve varsayılan bir değer.</span><span class="sxs-lookup"><span data-stu-id="51c1f-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="51c1f-116">Aşağıdaki örnek, bir özeti tanımlar. bir `Sub` yordamı üç parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="51c1f-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="51c1f-117">İlk iki gereklidir ve üçüncü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="51c1f-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="51c1f-118">Parametre bildirimleri parametre listesinde virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="51c1f-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     <span data-ttu-id="51c1f-119">İlk parametre kabul eden bir `customer` nesnesi ve `updateCustomer` geçirilen değişken doğrudan güncelleştirebilirsiniz `c` bağımsız değişkeni geçtiğinden [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="51c1f-119">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="51c1f-120">Geçirilen olduğundan yordamın son iki bağımsız değişken değerlerini değiştiremezsiniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="51c1f-120">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="51c1f-121">Çağrıyı yapan kod için bir değer sağlamaz, `level` parametresi, Visual Basic ayarlar, 0 varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="51c1f-121">If the calling code does not supply a value for the `level` parameter, Visual Basic sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="51c1f-122">Tür denetleme geçiş yaparsanız ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `Off`, `As` yan tümcesi olduğunda isteğe bağlı bir parametre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="51c1f-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="51c1f-123">Ancak, herhangi bir parametre kullanıyorsa, bir `As` yan tümcesi, bunların tümünün gerekir kullanır.</span><span class="sxs-lookup"><span data-stu-id="51c1f-123">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="51c1f-124">Anahtar denetimi türü ise `On`, `As` her parametre tanımı yan tümcesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="51c1f-124">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="51c1f-125">Veri türleri için tüm programlama öğeleri belirtme olarak bilinir *güçlü yazarak*.</span><span class="sxs-lookup"><span data-stu-id="51c1f-125">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="51c1f-126">Ayarladığınızda `Option Strict On`, Visual Basic güçlü yazmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="51c1f-126">When you set `Option Strict On`, Visual Basic enforces strong typing.</span></span> <span data-ttu-id="51c1f-127">Bu, aşağıdaki nedenlerle önerilir:</span><span class="sxs-lookup"><span data-stu-id="51c1f-127">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="51c1f-128">Değişkenleri ve parametreleri için IntelliSense desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="51c1f-128">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="51c1f-129">Bu, kodunuzda yazarken özelliklerini ve diğer üyeleri görmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="51c1f-129">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="51c1f-130">Tür denetleme gerçekleştirmek derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="51c1f-130">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="51c1f-131">Bu, çalışma zamanında taşma gibi hatalar nedeniyle başarısız olabilir deyimleri catch yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="51c1f-131">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="51c1f-132">Ayrıca bunları desteklemeyen nesnelerde yöntem çağrıları yakalar.</span><span class="sxs-lookup"><span data-stu-id="51c1f-132">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="51c1f-133">Kodunuzu daha hızlı yürütülmesini sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="51c1f-133">It results in faster execution of your code.</span></span> <span data-ttu-id="51c1f-134">Bunun bir nedeni olan bir programlama öğesi için bir veri türü belirtmezseniz, Visual Basic derleyici onu atayacağını `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="51c1f-134">One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type.</span></span> <span data-ttu-id="51c1f-135">Derlenmiş kodunuzu arasında ileri ve geri dönüştürmeniz gerekebilir `Object` ve performansını düşürür diğer veri türleri.</span><span class="sxs-lookup"><span data-stu-id="51c1f-135">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c1f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51c1f-136">See also</span></span>

 [<span data-ttu-id="51c1f-137">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="51c1f-137">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="51c1f-138">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="51c1f-138">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="51c1f-139">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="51c1f-139">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="51c1f-140">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="51c1f-140">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="51c1f-141">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="51c1f-141">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="51c1f-142">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="51c1f-142">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="51c1f-143">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="51c1f-143">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="51c1f-144">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="51c1f-144">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="51c1f-145">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51c1f-145">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  

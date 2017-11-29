---
title: "Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c909cfe1b45a42aae91948917f310474575f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="9d438-102">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d438-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="9d438-103">A *parametresi* onu çağırdığında yordamı için bir değer geçirmek için çağıran kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d438-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="9d438-104">Bir yordam için her parametre adı ve veri türünü belirten bir değişken bildirin aynı şekilde bildirin.</span><span class="sxs-lookup"><span data-stu-id="9d438-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="9d438-105">Ayrıca geçirme mekanizması belirtin ve parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d438-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="9d438-106">Daha fazla bilgi için bkz: [parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="9d438-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="9d438-107">Bir yordam parametresini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="9d438-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="9d438-108">Yordam bildiriminde yordam parametre listesi, diğer parametreler virgül ile ayırarak parametre adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9d438-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="9d438-109">Parametresinin veri türü karar verin.</span><span class="sxs-lookup"><span data-stu-id="9d438-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="9d438-110">Parametre adı ile izleyin bir `As` veri türünü belirtmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9d438-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="9d438-111">Parametresi için istediğiniz geçirme mekanizması karar verin.</span><span class="sxs-lookup"><span data-stu-id="9d438-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="9d438-112">Normalde, yordamı çağıran kodu değeriyle değiştirebilmesi istediğiniz sürece değer ile bir parametre geçirin.</span><span class="sxs-lookup"><span data-stu-id="9d438-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="9d438-113">Parametre adından [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) geçirme düzeneğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="9d438-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="9d438-114">Daha fazla bilgi için bkz: [farklar arasında geçirme bir bağımsız değişken değer ve başvuru tarafından](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9d438-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="9d438-115">Parametre isteğe bağlıysa geçirme mekanizmasıyla önünde [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) ve parametre veri türü eşittir işareti ile izleyin (`=`) ve varsayılan bir değer.</span><span class="sxs-lookup"><span data-stu-id="9d438-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="9d438-116">Aşağıdaki örnek, bir özeti tanımlar. bir `Sub` yordamı üç parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="9d438-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="9d438-117">İlk iki gereklidir ve üçüncü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d438-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="9d438-118">Parametre bildirimleri parametre listesinde virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="9d438-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     <span data-ttu-id="9d438-119">İlk parametre kabul eden bir `customer` nesnesi ve `updateCustomer` geçirilen değişken doğrudan güncelleştirebilirsiniz `c` bağımsız değişkeni geçtiğinden [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="9d438-119">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="9d438-120">Geçirilen olduğundan yordamın son iki bağımsız değişken değerlerini değiştiremezsiniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="9d438-120">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="9d438-121">Çağrıyı yapan kod için bir değer sağlamaz, `level` parametresi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 0 varsayılan değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9d438-121">If the calling code does not supply a value for the `level` parameter, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="9d438-122">Tür denetleme geçiş yaparsanız ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `Off`, `As` yan tümcesi olduğunda isteğe bağlı bir parametre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9d438-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="9d438-123">Ancak, herhangi bir parametre kullanıyorsa, bir `As` yan tümcesi, bunların tümünün gerekir kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d438-123">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="9d438-124">Anahtar denetimi türü ise `On`, `As` her parametre tanımı yan tümcesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9d438-124">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="9d438-125">Veri türleri için tüm programlama öğeleri belirtme olarak bilinir *güçlü yazarak*.</span><span class="sxs-lookup"><span data-stu-id="9d438-125">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="9d438-126">Ayarladığınızda `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] güçlü yazmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="9d438-126">When you set `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enforces strong typing.</span></span> <span data-ttu-id="9d438-127">Bu, aşağıdaki nedenlerle önerilir:</span><span class="sxs-lookup"><span data-stu-id="9d438-127">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="9d438-128">Değişkenleri ve parametreleri için IntelliSense desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d438-128">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="9d438-129">Bu, kodunuzda yazarken özelliklerini ve diğer üyeleri görmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d438-129">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="9d438-130">Tür denetleme gerçekleştirmek derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d438-130">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="9d438-131">Bu, çalışma zamanında taşma gibi hatalar nedeniyle başarısız olabilir deyimleri catch yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9d438-131">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="9d438-132">Ayrıca bunları desteklemeyen nesnelerde yöntem çağrıları yakalar.</span><span class="sxs-lookup"><span data-stu-id="9d438-132">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="9d438-133">Kodunuzu daha hızlı yürütülmesini sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="9d438-133">It results in faster execution of your code.</span></span> <span data-ttu-id="9d438-134">Bir Bunun nedeni, bir programlama öğesi için bir veri türü belirtmezseniz, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici atar `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="9d438-134">One reason for this is that if you do not specify a data type for a programming element, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler assigns it the `Object` type.</span></span> <span data-ttu-id="9d438-135">Derlenmiş kodunuzu arasında ileri ve geri dönüştürmeniz gerekebilir `Object` ve performansını düşürür diğer veri türleri.</span><span class="sxs-lookup"><span data-stu-id="9d438-135">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d438-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d438-136">See Also</span></span>  
 [<span data-ttu-id="9d438-137">Yordamları</span><span class="sxs-lookup"><span data-stu-id="9d438-137">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="9d438-138">Alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="9d438-138">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="9d438-139">İşlev yordamları</span><span class="sxs-lookup"><span data-stu-id="9d438-139">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="9d438-140">Nasıl yapılır: bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="9d438-140">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="9d438-141">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="9d438-141">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="9d438-142">Özyinelemeli yordamlar</span><span class="sxs-lookup"><span data-stu-id="9d438-142">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="9d438-143">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="9d438-143">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="9d438-144">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="9d438-144">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="9d438-145">Nesne odaklı programlama</span><span class="sxs-lookup"><span data-stu-id="9d438-145">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)

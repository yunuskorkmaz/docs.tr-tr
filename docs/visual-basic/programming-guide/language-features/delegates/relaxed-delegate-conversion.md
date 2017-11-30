---
title: "Gevşek Temsilci Dönüşümü (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cca3d09b538905714f627c9fa006187b8927383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="14d6b-102">Gevşek Temsilci Dönüşümü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14d6b-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="14d6b-103">Gevşek temsilci dönüşümü içerdikleri ve işlevleri temsilciler veya işleyicileri için kendi imzaları aynı olmadığında bile atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="14d6b-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="14d6b-104">Bu nedenle, temsilciler bağlama zaten için yöntem çağrılarına izin verilen bağlama ile tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="14d6b-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="14d6b-105">Parametreler ve dönüş türü</span><span class="sxs-lookup"><span data-stu-id="14d6b-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="14d6b-106">Aşağıdaki koşulların karşılanması gevşek dönüşüm tam imza eşleştirme yerine gerektirir zaman `Option Strict` ayarlanır `On`:</span><span class="sxs-lookup"><span data-stu-id="14d6b-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="14d6b-107">Genişletme dönüşümü her temsilci parametre veri türünden atanan işlevi karşılık gelen parametrenin veri türü mevcut olmalıdır veya `Sub`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="14d6b-108">Aşağıdaki örnekte, temsilci `Del1` parametresinin, bir `Integer`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="14d6b-109">Parametre `m` atanan lambda ifadeleri var olduğu genişletme dönüştürme bir veri türüne sahip olmalıdır `Integer`, gibi `Long` veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     <span data-ttu-id="14d6b-110">Daraltma dönüşümleri yalnızca izin verilen `Option Strict` ayarlanır `Off`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   <span data-ttu-id="14d6b-111">Genişletme dönüşümü atanan işlevinin dönüş türünden ters yönde mevcut olmalıdır veya `Sub` için temsilci dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="14d6b-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="14d6b-112">Aşağıdaki örneklerde, her atanan lambda ifadesi gövdesi için widens bir veri türü değerlendirilmelidir `Integer` dönüş türü olduğundan `del1` olan `Integer`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 <span data-ttu-id="14d6b-113">Varsa `Option Strict` ayarlanır `Off`, kısıtlama genişletme her iki yönde de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="14d6b-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="14d6b-114">Parametre belirtimleri atlama</span><span class="sxs-lookup"><span data-stu-id="14d6b-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="14d6b-115">Gevşek temsilci atanan yönteminde parametre özellikleri tamamen atlayın izin:</span><span class="sxs-lookup"><span data-stu-id="14d6b-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 <span data-ttu-id="14d6b-116">Edemez bazı parametrelerini belirtin ve diğerleri atlayın olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="14d6b-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 <span data-ttu-id="14d6b-117">Parametrelerini atlayın yeteneği, burada birkaç karmaşık parametreleri dahil bir olay işleyicisi tanımlama gibi bir durumda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="14d6b-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="14d6b-118">Bağımsız değişkenler bazı olay işleyicileri için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="14d6b-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="14d6b-119">Bunun yerine, işleyici üzerinde olayı kaydedilir ve bağımsız değişkenleri göz ardı eder denetim durumunu doğrudan erişir.</span><span class="sxs-lookup"><span data-stu-id="14d6b-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="14d6b-120">Gevşek temsilci, bu tür bildirimleri belirsizlikleri sonuç olduğunda değişkenlerinde atlamak izin verir.</span><span class="sxs-lookup"><span data-stu-id="14d6b-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="14d6b-121">Aşağıdaki örnekte, tam olarak belirtilen yöntem `OnClick` olarak yazılabilir `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="14d6b-122">AddressOf örnekleri</span><span class="sxs-lookup"><span data-stu-id="14d6b-122">AddressOf Examples</span></span>  
 <span data-ttu-id="14d6b-123">Lambda ifadeleri önceki örneklerde tür ilişkileri görmeyi kolaylaştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14d6b-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="14d6b-124">Ancak, aynı relaxations kullanan temsilci atamaları izin verilen `AddressOf`, `Handles`, veya `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="14d6b-125">Aşağıdaki örnekte, işlevleri `f1`, `f2`, `f3`, ve `f4` tüm atanabilir `Del1`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 <span data-ttu-id="14d6b-126">Aşağıdaki örnekte yalnızca olduğunda geçerlidir olan `Option Strict` ayarlanır `Off`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="14d6b-127">Bırakma işlevi döndürür</span><span class="sxs-lookup"><span data-stu-id="14d6b-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="14d6b-128">Gevşek temsilci dönüşümü bir işleve atamanızı sağlar bir `Sub` temsilci, etkili bir şekilde işlevinin dönüş değeri yoksayılıyor.</span><span class="sxs-lookup"><span data-stu-id="14d6b-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="14d6b-129">Ancak, atayamazsınız bir `Sub` için bir işlev temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="14d6b-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="14d6b-130">Aşağıdaki örnekte, işlevin adresini `doubler` atandığı `Sub` temsilci `Del3`.</span><span class="sxs-lookup"><span data-stu-id="14d6b-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="14d6b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14d6b-131">See Also</span></span>  
 [<span data-ttu-id="14d6b-132">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="14d6b-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="14d6b-133">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="14d6b-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="14d6b-134">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="14d6b-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="14d6b-135">Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirme</span><span class="sxs-lookup"><span data-stu-id="14d6b-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="14d6b-136">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="14d6b-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="14d6b-137">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="14d6b-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

---
title: Gevşek Temsilci Dönüşümü (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: 57e863d9781721a997ae49e1a5c9d8f3562a1bd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973292"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="d82a2-102">Gevşek Temsilci Dönüşümü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d82a2-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="d82a2-103">Gevşek temsilci dönüşümü bile bunların imzalarını aynı olmadığında abonelerimizin ve işlevleri temsilci veya işleyicileri için atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d82a2-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="d82a2-104">Bu nedenle, temsilciler bağlama zaten için yöntem çağrılarına izin verilen bağlama ile tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="d82a2-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="d82a2-105">Parametreler ve dönüş türü</span><span class="sxs-lookup"><span data-stu-id="d82a2-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="d82a2-106">Tam imza eşleştirme yerine, aşağıdaki koşulların karşılanması gevşek dönüşüm gerektirir, `Option Strict` ayarlanır `On`:</span><span class="sxs-lookup"><span data-stu-id="d82a2-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="d82a2-107">Bir genişletme dönüşümü her temsilcinin parametre veri türünden atanan işlevin karşılık gelen parametrenin veri türü için mevcut olmalıdır veya `Sub`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="d82a2-108">Aşağıdaki örnekte, temsilci `Del1` bir parametreye sahip bir `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="d82a2-109">Parametre `m` içinde atanan lambda ifadeleri var olan bir genişletme dönüşümü bir veri türüne sahip olmalıdır `Integer`, gibi `Long` veya `Double`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="d82a2-110">Daraltma dönüştürmeleri, yalnızca verilen `Option Strict` ayarlanır `Off`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="d82a2-111">Atanan işlevin dönüş türünden ters yönde genişletme dönüştürmesi olmalıdır veya `Sub` temsilcinin dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="d82a2-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="d82a2-112">Aşağıdaki örneklerde, her atanmış bir lambda ifadesinin gövdesi için widens bir veri türü değerlendirilmelidir `Integer` çünkü dönüş türü `del1` olduğu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="d82a2-113">Varsa `Option Strict` ayarlanır `Off`, kısıtlama genişletme her iki yönde de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d82a2-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="d82a2-114">Atlama parametre özellikleri</span><span class="sxs-lookup"><span data-stu-id="d82a2-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="d82a2-115">Gevşek temsilciler de tamamen atanan yöntemindeki parametre özellikleri atlamak izin ver:</span><span class="sxs-lookup"><span data-stu-id="d82a2-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="d82a2-116">Bazı parametreler belirtin ve diğerleri atlamak olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d82a2-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="d82a2-117">Parametreleri atlarsanız olanağı, burada birkaç karmaşık parametresi söz konusu olan bir olay işleyicisi tanımlama gibi bir durumda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d82a2-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="d82a2-118">Bazı olay işleyicilerine bağımsız değişkenleri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d82a2-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="d82a2-119">Bunun yerine, işleyici üretileceği olayı kaydedilir ve bağımsız değişkenler yoksayar denetim durumunu doğrudan erişir.</span><span class="sxs-lookup"><span data-stu-id="d82a2-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="d82a2-120">Gevşek temsilciler belirsizlikleri sonuç olduğunda bu tür bildirimleri bağımsız atlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d82a2-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="d82a2-121">Aşağıdaki örnekte, tam olarak belirtilen yöntem `OnClick` şeklinde yeniden yazılabilir `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="d82a2-122">AddressOf örnekleri</span><span class="sxs-lookup"><span data-stu-id="d82a2-122">AddressOf Examples</span></span>  
 <span data-ttu-id="d82a2-123">Lambda ifadeleri, önceki örneklerde, tür ilişkilerini görmek kolay hale getirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d82a2-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="d82a2-124">Ancak, aynı relaxations kullanan temsilci atamaları için izin verilen `AddressOf`, `Handles`, veya `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="d82a2-125">Aşağıdaki örnekte, İşlevler `f1`, `f2`, `f3`, ve `f4` tüm atanabilir `Del1`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="d82a2-126">Aşağıdaki örnek yalnızca geçerli olduğunda, `Option Strict` ayarlanır `Off`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="d82a2-127">Bırakma işlevi döndürür</span><span class="sxs-lookup"><span data-stu-id="d82a2-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="d82a2-128">Gevşek temsilci dönüşümü bir işleve atamanızı sağlar bir `Sub` temsilci, etkili bir şekilde işlev dönüş değeri yoksayılıyor.</span><span class="sxs-lookup"><span data-stu-id="d82a2-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="d82a2-129">Ancak, atanamaz bir `Sub` için bir işlev temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="d82a2-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="d82a2-130">Aşağıdaki örnekte, işlevin adresini `doubler` atandığı `Sub` temsilci `Del3`.</span><span class="sxs-lookup"><span data-stu-id="d82a2-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="d82a2-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d82a2-131">See also</span></span>

- [<span data-ttu-id="d82a2-132">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="d82a2-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="d82a2-133">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d82a2-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="d82a2-134">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="d82a2-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="d82a2-135">Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin</span><span class="sxs-lookup"><span data-stu-id="d82a2-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="d82a2-136">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="d82a2-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="d82a2-137">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="d82a2-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

---
title: Gevşek Temsilci Dönüştürme
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: b914d0479f160199744a8f9923c0bebc87321329
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086081"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="63c5d-102">Gevşek Temsilci Dönüşümü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63c5d-102">Relaxed Delegate Conversion (Visual Basic)</span></span>

<span data-ttu-id="63c5d-103">Gevşek temsilci dönüştürme, imzaları özdeş olmasa bile temsilcilere veya işleyicilere alt öğeleri ve işlevleri atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63c5d-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="63c5d-104">Bu nedenle, temsilcilere bağlama, yöntem etkinleştirmeleri için zaten izin verilen bağlama ile tutarlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="63c5d-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="63c5d-105">Parametreler ve dönüş türü</span><span class="sxs-lookup"><span data-stu-id="63c5d-105">Parameters and Return Type</span></span>  

 <span data-ttu-id="63c5d-106">Tam imza eşleşmesi yerine, gevşek dönüştürme aşağıdaki koşulların yerine getirilmesi gerekir `Option Strict` `On` :</span><span class="sxs-lookup"><span data-stu-id="63c5d-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="63c5d-107">Her temsilci parametresinin veri türünden, atanan işlevin veya karşılık gelen parametresinin veri türüne genişleyen bir dönüştürme bulunmalıdır `Sub` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="63c5d-108">Aşağıdaki örnekte, temsilcinin bir `Del1` parametresi vardır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="63c5d-109">`m`Atanan Lambda ifadelerinde parametresi, veya gibi bir üzerinde genişleyen dönüştürme olan bir veri türüne sahip olmalıdır `Integer` `Long` `Double` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="63c5d-110">Daraltma dönüştürmelerine yalnızca `Option Strict` öğesine ayarlandığında izin verilir `Off` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="63c5d-111">Genişleyen bir dönüştürme, atanan işlevin dönüş türünden veya `Sub` temsilcinin dönüş türüne karşı yönde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63c5d-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="63c5d-112">Aşağıdaki örneklerde, atanan her lambda ifadesinin gövdesi, öğesinin dönüş türü olduğu için widens tarafından kullanılan bir veri türü olarak değerlendirilmelidir `Integer` `del1` `Integer` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="63c5d-113">`Option Strict`Olarak ayarlanırsa `Off` , genişletme kısıtlaması her iki yönde de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="63c5d-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="63c5d-114">Parametre belirtimlerini atlama</span><span class="sxs-lookup"><span data-stu-id="63c5d-114">Omitting Parameter Specifications</span></span>  

 <span data-ttu-id="63c5d-115">Gevşek Temsilciler, atanan yöntemdeki parametre belirtimlerini tamamen atlamanızı da sağlar:</span><span class="sxs-lookup"><span data-stu-id="63c5d-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="63c5d-116">Bazı parametreleri belirtemezsiniz ve diğerlerini atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="63c5d-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="63c5d-117">Parametreleri atlama özelliği, çeşitli karmaşık parametrelerin dahil olduğu bir olay işleyicisini tanımlama gibi bir durumda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="63c5d-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="63c5d-118">Bazı olay işleyicilerinin bağımsız değişkenleri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="63c5d-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="63c5d-119">Bunun yerine, işleyici doğrudan olayın kaydedildiği denetimin durumuna erişir ve bağımsız değişkenleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="63c5d-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="63c5d-120">Gevşek Temsilciler, belirsizlikleri sonucu olmadığında bu bildirimlerin bağımsız değişkenlerini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63c5d-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="63c5d-121">Aşağıdaki örnekte, tam olarak belirtilen yöntem olarak yeniden `OnClick` yazılabilir `RelaxedOnClick` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="63c5d-122">AddressOf örnekleri</span><span class="sxs-lookup"><span data-stu-id="63c5d-122">AddressOf Examples</span></span>  

 <span data-ttu-id="63c5d-123">Lambda ifadeleri, tür ilişkilerinin kolayca görmesini sağlamak için önceki örneklerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63c5d-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="63c5d-124">Ancak,, veya kullanan temsilci atamaları için aynı relade izin verilir `AddressOf` `Handles` `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="63c5d-125">Aşağıdaki örnekte,,, `f1` ve işlevleri `f2` `f3` `f4` öğesine atanabilir `Del1` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="63c5d-126">Aşağıdaki örnek yalnızca `Option Strict` öğesine ayarlandığında geçerlidir `Off` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="63c5d-127">Işlev dönüşleri bırakılıyor</span><span class="sxs-lookup"><span data-stu-id="63c5d-127">Dropping Function Returns</span></span>  

 <span data-ttu-id="63c5d-128">Gevşek temsilci dönüştürme, bir temsilciye bir işlevi atamanıza `Sub` ve işlevin dönüş değerini etkin bir şekilde yoksaymanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63c5d-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="63c5d-129">Ancak, bir `Sub` işlev temsilcisine bir atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="63c5d-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="63c5d-130">Aşağıdaki örnekte, işlevin adresi `doubler` `Sub` temsilciye atanır `Del3` .</span><span class="sxs-lookup"><span data-stu-id="63c5d-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="63c5d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63c5d-131">See also</span></span>

- [<span data-ttu-id="63c5d-132">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="63c5d-132">Lambda Expressions</span></span>](../procedures/lambda-expressions.md)
- [<span data-ttu-id="63c5d-133">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="63c5d-133">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="63c5d-134">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="63c5d-134">Delegates</span></span>](index.md)
- [<span data-ttu-id="63c5d-135">Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme</span><span class="sxs-lookup"><span data-stu-id="63c5d-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="63c5d-136">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63c5d-136">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="63c5d-137">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="63c5d-137">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)

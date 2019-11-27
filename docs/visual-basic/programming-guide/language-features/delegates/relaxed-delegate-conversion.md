---
title: Gevşek Temsilci Dönüşümü
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345227"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="20ffd-102">Gevşek Temsilci Dönüşümü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20ffd-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="20ffd-103">Gevşek temsilci dönüştürme, imzaları özdeş olmasa bile temsilcilere veya işleyicilere alt öğeleri ve işlevleri atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="20ffd-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="20ffd-104">Bu nedenle, temsilcilere bağlama, yöntem etkinleştirmeleri için zaten izin verilen bağlama ile tutarlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="20ffd-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="20ffd-105">Parametreler ve dönüş türü</span><span class="sxs-lookup"><span data-stu-id="20ffd-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="20ffd-106">Tam imza eşleşmesi yerine, gevşek dönüştürme, `Option Strict` `On`olarak ayarlandığında aşağıdaki koşulların karşılanmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="20ffd-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="20ffd-107">Her temsilci parametresinin veri türünden, atanan işlevin veya `Sub`karşılık gelen parametresinin veri türüne genişleyen bir dönüştürme bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20ffd-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="20ffd-108">Aşağıdaki örnekte, temsilci `Del1` bir `Integer`parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="20ffd-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="20ffd-109">Atanan Lambda ifadelerinde `m` parametresi, `Long` veya `Double`gibi `Integer`üzerinde genişleyen dönüştürme olan bir veri türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20ffd-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="20ffd-110">Daraltma dönüştürmelerine yalnızca `Option Strict` `Off`olarak ayarlandığında izin verilir.</span><span class="sxs-lookup"><span data-stu-id="20ffd-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="20ffd-111">Genişleyen bir dönüştürme, atanan işlevin dönüş türünden ya da temsilcinin dönüş türüne `Sub` karşı yönde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20ffd-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="20ffd-112">Aşağıdaki örneklerde, `del1` dönüş türü `Integer`olduğundan, her bir atanan lambda ifadesinin gövdesi `Integer` bir veri türü olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="20ffd-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="20ffd-113">`Option Strict` `Off`olarak ayarlanırsa, genişleyen kısıtlama her iki yönde de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="20ffd-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="20ffd-114">Parametre belirtimlerini atlama</span><span class="sxs-lookup"><span data-stu-id="20ffd-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="20ffd-115">Gevşek Temsilciler, atanan yöntemdeki parametre belirtimlerini tamamen atlamanızı da sağlar:</span><span class="sxs-lookup"><span data-stu-id="20ffd-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="20ffd-116">Bazı parametreleri belirtemezsiniz ve diğerlerini atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="20ffd-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="20ffd-117">Parametreleri atlama özelliği, çeşitli karmaşık parametrelerin dahil olduğu bir olay işleyicisini tanımlama gibi bir durumda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="20ffd-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="20ffd-118">Bazı olay işleyicilerinin bağımsız değişkenleri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="20ffd-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="20ffd-119">Bunun yerine, işleyici doğrudan olayın kaydedildiği denetimin durumuna erişir ve bağımsız değişkenleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="20ffd-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="20ffd-120">Gevşek Temsilciler, belirsizlikleri sonucu olmadığında bu bildirimlerin bağımsız değişkenlerini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="20ffd-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="20ffd-121">Aşağıdaki örnekte, tam olarak belirtilen yöntem `OnClick` `RelaxedOnClick`olarak yeniden yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="20ffd-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="20ffd-122">AddressOf örnekleri</span><span class="sxs-lookup"><span data-stu-id="20ffd-122">AddressOf Examples</span></span>  
 <span data-ttu-id="20ffd-123">Lambda ifadeleri, tür ilişkilerinin kolayca görmesini sağlamak için önceki örneklerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20ffd-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="20ffd-124">Ancak, `AddressOf`, `Handles`veya `AddHandler`kullanan temsilci atamaları için aynı relade izin verilir.</span><span class="sxs-lookup"><span data-stu-id="20ffd-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="20ffd-125">Aşağıdaki örnekte, `f1`, `f2`, `f3`ve `f4` işlevleri `Del1`atanabilir.</span><span class="sxs-lookup"><span data-stu-id="20ffd-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="20ffd-126">Aşağıdaki örnek yalnızca `Option Strict` `Off`olarak ayarlandığında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="20ffd-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="20ffd-127">Işlev dönüşleri bırakılıyor</span><span class="sxs-lookup"><span data-stu-id="20ffd-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="20ffd-128">Gevşek temsilci dönüşümü, işlevin dönüş değerini etkin bir şekilde yok sayan bir `Sub` temsilcisine bir işlev atamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="20ffd-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="20ffd-129">Ancak, bir işlev temsilcisine `Sub` atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="20ffd-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="20ffd-130">Aşağıdaki örnekte, `doubler` işlev adresi `Sub` temsilci `Del3`atanır.</span><span class="sxs-lookup"><span data-stu-id="20ffd-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="20ffd-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20ffd-131">See also</span></span>

- [<span data-ttu-id="20ffd-132">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="20ffd-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="20ffd-133">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="20ffd-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="20ffd-134">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="20ffd-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="20ffd-135">Nasıl yapılır: yordamları Visual Basic başka bir yordama geçirme</span><span class="sxs-lookup"><span data-stu-id="20ffd-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="20ffd-136">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="20ffd-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="20ffd-137">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="20ffd-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

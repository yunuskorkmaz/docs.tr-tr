---
description: 'Daha fazla bilgi edinin: gevşek temsilci dönüştürme (Visual Basic)'
title: Gevşek Temsilci Dönüştürme
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: 36917017cd29d2c71f0c04ca9545b7d4e90c644e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428499"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="e4f29-103">Gevşek Temsilci Dönüşümü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4f29-103">Relaxed Delegate Conversion (Visual Basic)</span></span>

<span data-ttu-id="e4f29-104">Gevşek temsilci dönüştürme, imzaları özdeş olmasa bile temsilcilere veya işleyicilere alt öğeleri ve işlevleri atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4f29-104">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="e4f29-105">Bu nedenle, temsilcilere bağlama, yöntem etkinleştirmeleri için zaten izin verilen bağlama ile tutarlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e4f29-105">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="e4f29-106">Parametreler ve dönüş türü</span><span class="sxs-lookup"><span data-stu-id="e4f29-106">Parameters and Return Type</span></span>  

 <span data-ttu-id="e4f29-107">Tam imza eşleşmesi yerine, gevşek dönüştürme aşağıdaki koşulların yerine getirilmesi gerekir `Option Strict` `On` :</span><span class="sxs-lookup"><span data-stu-id="e4f29-107">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="e4f29-108">Her temsilci parametresinin veri türünden, atanan işlevin veya karşılık gelen parametresinin veri türüne genişleyen bir dönüştürme bulunmalıdır `Sub` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-108">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="e4f29-109">Aşağıdaki örnekte, temsilcinin bir `Del1` parametresi vardır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-109">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="e4f29-110">`m`Atanan Lambda ifadelerinde parametresi, veya gibi bir üzerinde genişleyen dönüştürme olan bir veri türüne sahip olmalıdır `Integer` `Long` `Double` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-110">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="e4f29-111">Daraltma dönüştürmelerine yalnızca `Option Strict` öğesine ayarlandığında izin verilir `Off` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-111">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="e4f29-112">Genişleyen bir dönüştürme, atanan işlevin dönüş türünden veya `Sub` temsilcinin dönüş türüne karşı yönde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4f29-112">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="e4f29-113">Aşağıdaki örneklerde, atanan her lambda ifadesinin gövdesi, öğesinin dönüş türü olduğu için widens tarafından kullanılan bir veri türü olarak değerlendirilmelidir `Integer` `del1` `Integer` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-113">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="e4f29-114">`Option Strict`Olarak ayarlanırsa `Off` , genişletme kısıtlaması her iki yönde de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e4f29-114">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="e4f29-115">Parametre belirtimlerini atlama</span><span class="sxs-lookup"><span data-stu-id="e4f29-115">Omitting Parameter Specifications</span></span>  

 <span data-ttu-id="e4f29-116">Gevşek Temsilciler, atanan yöntemdeki parametre belirtimlerini tamamen atlamanızı da sağlar:</span><span class="sxs-lookup"><span data-stu-id="e4f29-116">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="e4f29-117">Bazı parametreleri belirtemezsiniz ve diğerlerini atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e4f29-117">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="e4f29-118">Parametreleri atlama özelliği, çeşitli karmaşık parametrelerin dahil olduğu bir olay işleyicisini tanımlama gibi bir durumda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4f29-118">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="e4f29-119">Bazı olay işleyicilerinin bağımsız değişkenleri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e4f29-119">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="e4f29-120">Bunun yerine, işleyici doğrudan olayın kaydedildiği denetimin durumuna erişir ve bağımsız değişkenleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e4f29-120">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="e4f29-121">Gevşek Temsilciler, belirsizlikleri sonucu olmadığında bu bildirimlerin bağımsız değişkenlerini atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4f29-121">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="e4f29-122">Aşağıdaki örnekte, tam olarak belirtilen yöntem olarak yeniden `OnClick` yazılabilir `RelaxedOnClick` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-122">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="e4f29-123">AddressOf örnekleri</span><span class="sxs-lookup"><span data-stu-id="e4f29-123">AddressOf Examples</span></span>  

 <span data-ttu-id="e4f29-124">Lambda ifadeleri, tür ilişkilerinin kolayca görmesini sağlamak için önceki örneklerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4f29-124">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="e4f29-125">Ancak,, veya kullanan temsilci atamaları için aynı relade izin verilir `AddressOf` `Handles` `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-125">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="e4f29-126">Aşağıdaki örnekte,,, `f1` ve işlevleri `f2` `f3` `f4` öğesine atanabilir `Del1` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-126">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="e4f29-127">Aşağıdaki örnek yalnızca `Option Strict` öğesine ayarlandığında geçerlidir `Off` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-127">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="e4f29-128">Işlev dönüşleri bırakılıyor</span><span class="sxs-lookup"><span data-stu-id="e4f29-128">Dropping Function Returns</span></span>  

 <span data-ttu-id="e4f29-129">Gevşek temsilci dönüştürme, bir temsilciye bir işlevi atamanıza `Sub` ve işlevin dönüş değerini etkin bir şekilde yoksaymanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4f29-129">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="e4f29-130">Ancak, bir `Sub` işlev temsilcisine bir atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e4f29-130">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="e4f29-131">Aşağıdaki örnekte, işlevin adresi `doubler` `Sub` temsilciye atanır `Del3` .</span><span class="sxs-lookup"><span data-stu-id="e4f29-131">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e4f29-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4f29-132">See also</span></span>

- [<span data-ttu-id="e4f29-133">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e4f29-133">Lambda Expressions</span></span>](../procedures/lambda-expressions.md)
- [<span data-ttu-id="e4f29-134">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="e4f29-134">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="e4f29-135">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e4f29-135">Delegates</span></span>](index.md)
- [<span data-ttu-id="e4f29-136">Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme</span><span class="sxs-lookup"><span data-stu-id="e4f29-136">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="e4f29-137">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4f29-137">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="e4f29-138">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="e4f29-138">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)

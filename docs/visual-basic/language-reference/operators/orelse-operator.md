---
title: OrElse İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 02be78c8f2b7529f1fb0e46e9fe610a3c66b0652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860138"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="0f265-102">OrElse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f265-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="0f265-103">Kısa devre kapsamlı mantıksal veya işlecini iki gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0f265-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f265-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f265-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0f265-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0f265-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0f265-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0f265-106">Required.</span></span> <span data-ttu-id="0f265-107">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="0f265-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="0f265-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0f265-108">Required.</span></span> <span data-ttu-id="0f265-109">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="0f265-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="0f265-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0f265-110">Required.</span></span> <span data-ttu-id="0f265-111">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="0f265-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f265-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f265-112">Remarks</span></span>  
 <span data-ttu-id="0f265-113">Bir mantıksal işlemi olduğu söylenir *kısa devre* , derlenmiş kod başka bir ifadenin sonucu bağlı olarak tek bir ifade değerlendirmesi devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="0f265-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="0f265-114">Hesaplanan ilk ifadenin sonucu işlem son sonucunu belirlerse, ikinci ifade değerlendirilemiyor gerek yoktur nihai sonucu değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f265-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="0f265-115">Kısa devre Atlanan ifade karmaşıksa veya yordam çağrılarını içeriyorsa performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0f265-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="0f265-116">Her ikisi de ifadeleri sonucunu verirse `True`, `result` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="0f265-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="0f265-117">Aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0f265-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="0f265-118">Varsa `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="0f265-118">If `expression1` is</span></span>|<span data-ttu-id="0f265-119">Ve `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="0f265-119">And `expression2` is</span></span>|<span data-ttu-id="0f265-120">Değerini `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="0f265-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="0f265-121">(Değerlendirilmedi)</span><span class="sxs-lookup"><span data-stu-id="0f265-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="0f265-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="0f265-122">Data Types</span></span>  
 <span data-ttu-id="0f265-123">`OrElse` İşleci yalnızca tanımlanmış [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0f265-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="0f265-124">Visual Basic, her işlenen gerektiği şekilde dönüştürür `Boolean` ifade değerlendirmeden önce.</span><span class="sxs-lookup"><span data-stu-id="0f265-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="0f265-125">Sonucu bir sayısal tür için atarsanız, Visual Basic ondan dönüştürür `Boolean` o türe şekilde `False` olur `0` ve `True` olur `-1`.</span><span class="sxs-lookup"><span data-stu-id="0f265-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="0f265-126">Daha fazla bilgi için [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions)</span><span class="sxs-lookup"><span data-stu-id="0f265-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions)</span></span>
  
## <a name="overloading"></a><span data-ttu-id="0f265-127">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="0f265-127">Overloading</span></span>  
 <span data-ttu-id="0f265-128">[Veya işleci](../../../visual-basic/language-reference/operators/or-operator.md) ve [IsTrue işleci](../../../visual-basic/language-reference/operators/istrue-operator.md) olabilir *aşırı*, yani bu sınıf türünde bir işlenen sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, veya yapısı.</span><span class="sxs-lookup"><span data-stu-id="0f265-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0f265-129">Aşırı yükleme `Or` ve `IsTrue` işleçleri davranışını etkileyen `OrElse` işleci.</span><span class="sxs-lookup"><span data-stu-id="0f265-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="0f265-130">Kodunuzu kullanıyorsa `OrElse` bir sınıf veya aşırı yapısı `Or` ve `IsTrue`, yeniden tanımlanan davranışlarını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0f265-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="0f265-131">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0f265-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f265-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f265-132">Example</span></span>  
 <span data-ttu-id="0f265-133">Aşağıdaki örnekte `OrElse` mantıksal veya işlecini iki ifadelerini gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="0f265-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="0f265-134">Sonuç bir `Boolean` gösteren bir değer ya da iki ifadenin true olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="0f265-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="0f265-135">İlk ifade yanlışsa `True`, ikinci değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="0f265-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="0f265-136">Yukarıdaki örnekte sonuçlarını üretir `True`, `True`, ve `False` sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="0f265-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="0f265-137">Hesaplamasında `firstCheck`, ilk zaten olduğundan ikinci ifade değerlendirilmez `True`.</span><span class="sxs-lookup"><span data-stu-id="0f265-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="0f265-138">Ancak, ikinci ifade hesaplamasına değerlendirilir `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="0f265-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f265-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f265-139">Example</span></span>  
 <span data-ttu-id="0f265-140">Aşağıdaki örnekte gösterildiği bir `If`... `Then` iki yordam çağrılarını içeren deyimi.</span><span class="sxs-lookup"><span data-stu-id="0f265-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="0f265-141">İlk çağrı döndürürse `True`, ikinci yordam çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="0f265-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="0f265-142">İkinci yordam, kodun bu bölümünü çalıştırıldığında, her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştiriyorsa bu beklenmeyen sonuçlara neden.</span><span class="sxs-lookup"><span data-stu-id="0f265-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="0f265-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f265-143">See also</span></span>

- [<span data-ttu-id="0f265-144">Mantıksal/bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f265-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="0f265-145">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="0f265-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0f265-146">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="0f265-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0f265-147">Or İşleci</span><span class="sxs-lookup"><span data-stu-id="0f265-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="0f265-148">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="0f265-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="0f265-149">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="0f265-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

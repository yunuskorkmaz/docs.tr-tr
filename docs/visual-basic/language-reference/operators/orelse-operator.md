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
ms.openlocfilehash: 1ee3c1a5b6089f44742281eb40e2a7e9cb3e2812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604828"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="d8409-102">OrElse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8409-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="d8409-103">Kapsayıcı mantıksal veya işlecini iki ifadeye kısa devre gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d8409-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8409-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8409-104">Syntax</span></span>  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="d8409-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d8409-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d8409-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d8409-106">Required.</span></span> <span data-ttu-id="d8409-107">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="d8409-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="d8409-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d8409-108">Required.</span></span> <span data-ttu-id="d8409-109">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="d8409-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="d8409-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d8409-110">Required.</span></span> <span data-ttu-id="d8409-111">Tüm `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="d8409-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8409-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8409-112">Remarks</span></span>  
 <span data-ttu-id="d8409-113">Mantıksal bir işlem olarak kabul edilir *kısa devre* derlenmiş kod başka bir ifade sonucuna bağlı olarak bir ifade değerlendirme devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="d8409-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="d8409-114">İlk ifade Hesaplandı sonucunu işleminin son sonucu belirlerse, ikinci ifade değerlendirmek için gerek yoktur nihai sonucu değiştiremediğinizden.</span><span class="sxs-lookup"><span data-stu-id="d8409-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="d8409-115">Kısa devre atlandığında ifade karmaşıksa veya yordam çağrıları içeriyorsa performansı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="d8409-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="d8409-116">İçin veya her ikisi ifadeleri değerlendirin varsa `True`, `result` olan `True`.</span><span class="sxs-lookup"><span data-stu-id="d8409-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="d8409-117">Aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d8409-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="d8409-118">Varsa `expression1` olduğu</span><span class="sxs-lookup"><span data-stu-id="d8409-118">If `expression1` is</span></span>|<span data-ttu-id="d8409-119">Ve `expression2` olduğu</span><span class="sxs-lookup"><span data-stu-id="d8409-119">And `expression2` is</span></span>|<span data-ttu-id="d8409-120">Değeri `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="d8409-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="d8409-121">(Değerlendirilmedi)</span><span class="sxs-lookup"><span data-stu-id="d8409-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="d8409-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d8409-122">Data Types</span></span>  
 <span data-ttu-id="d8409-123">`OrElse` İşleci yalnızca için tanımlanmış [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d8409-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="d8409-124">Visual Basic dönüştürür için gereken her işlenen `Boolean` ve tamamen işlemi gerçekleştirir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d8409-124">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="d8409-125">Sayısal bir tür sonucu atarsanız, Visual Basic ondan dönüştürür `Boolean` bu türü.</span><span class="sxs-lookup"><span data-stu-id="d8409-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="d8409-126">Bu, beklenmeyen davranışları üretebilir.</span><span class="sxs-lookup"><span data-stu-id="d8409-126">This could produce unexpected behavior.</span></span> <span data-ttu-id="d8409-127">Örneğin, `5 OrElse 12` sonuçlanır `–1` için dönüştürüldüğünde `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d8409-127">For example, `5 OrElse 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d8409-128">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d8409-128">Overloading</span></span>  
 <span data-ttu-id="d8409-129">[Veya işleci](../../../visual-basic/language-reference/operators/or-operator.md) ve [IsTrue işleci](../../../visual-basic/language-reference/operators/istrue-operator.md) olabilir *aşırı*, o sınıfın tür işleneni sahip olduğunda bir sınıf veya yapı davranışlarını tanımlayabilirsiniz, anlamına gelir veya yapısı.</span><span class="sxs-lookup"><span data-stu-id="d8409-129">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d8409-130">Aşırı yükleme `Or` ve `IsTrue` işleçleri davranışını etkileyen `OrElse` işleci.</span><span class="sxs-lookup"><span data-stu-id="d8409-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="d8409-131">Kodunuzu kullanıyorsa `OrElse` bir sınıf veya overloads yapısı `Or` ve `IsTrue`, yeniden tanımlanan davranışlarını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d8409-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="d8409-132">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d8409-132">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8409-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8409-133">Example</span></span>  
 <span data-ttu-id="d8409-134">Aşağıdaki örnek kullanır `OrElse` iki ifadeleri mantıksal ayrım yapmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="d8409-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="d8409-135">Sonuç bir `Boolean` temsil eden bir değer ya da iki ifadenin doğru olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="d8409-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="d8409-136">İlk ifade ise `True`, ikinci değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="d8409-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 <span data-ttu-id="d8409-137">Önceki örnekte sonuçlarını üreten `True`, `True`, ve `False` sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="d8409-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="d8409-138">Hesaplanmasına `firstCheck`, ilk zaten olduğundan ikinci ifade değerlendirilmez `True`.</span><span class="sxs-lookup"><span data-stu-id="d8409-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="d8409-139">Ancak, ikinci ifade hesaplaması olarak değerlendirilir `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="d8409-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8409-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8409-140">Example</span></span>  
 <span data-ttu-id="d8409-141">Aşağıdaki örnekte gösterildiği bir `If`... `Then` iki yordam çağrıları içeren deyimi.</span><span class="sxs-lookup"><span data-stu-id="d8409-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="d8409-142">İlk çağrıda döndürürse `True`, ikinci yordam çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="d8409-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="d8409-143">İkinci yordam kodu'nun bu bölümünde çalıştığında, her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştiriyorsa bu beklenmeyen sonuçlara neden.</span><span class="sxs-lookup"><span data-stu-id="d8409-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d8409-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8409-144">See Also</span></span>  
 [<span data-ttu-id="d8409-145">Mantıksal ve bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8409-145">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="d8409-146">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="d8409-146">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d8409-147">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="d8409-147">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d8409-148">Or İşleci</span><span class="sxs-lookup"><span data-stu-id="d8409-148">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)  
 [<span data-ttu-id="d8409-149">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="d8409-149">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="d8409-150">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="d8409-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

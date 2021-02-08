---
description: 'Daha fazla bilgi edinin: Oreli Işleci (Visual Basic)'
title: OrElse İşleci
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
ms.openlocfilehash: 48ccbda1e0cb4f655b28e902b22fbfe0c3e66ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795332"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="edcdf-103">OrElse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edcdf-103">OrElse Operator (Visual Basic)</span></span>

<span data-ttu-id="edcdf-104">İki ifadeye kısa devre uygulayan kapsamlı mantıksal ayırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-104">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edcdf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="edcdf-105">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="edcdf-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="edcdf-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="edcdf-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-107">Required.</span></span> <span data-ttu-id="edcdf-108">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="edcdf-108">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="edcdf-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-109">Required.</span></span> <span data-ttu-id="edcdf-110">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="edcdf-110">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="edcdf-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-111">Required.</span></span> <span data-ttu-id="edcdf-112">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="edcdf-112">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edcdf-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edcdf-113">Remarks</span></span>  

 <span data-ttu-id="edcdf-114">Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-114">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="edcdf-115">Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="edcdf-115">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="edcdf-116">Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-116">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="edcdf-117">Ya da her iki ifade olarak değerlendirilir `True` `result` `True` .</span><span class="sxs-lookup"><span data-stu-id="edcdf-117">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="edcdf-118">Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .</span><span class="sxs-lookup"><span data-stu-id="edcdf-118">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="edcdf-119">İse `expression1`</span><span class="sxs-lookup"><span data-stu-id="edcdf-119">If `expression1` is</span></span>|<span data-ttu-id="edcdf-120">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="edcdf-120">And `expression2` is</span></span>|<span data-ttu-id="edcdf-121">`result`Öğesinin değeri</span><span class="sxs-lookup"><span data-stu-id="edcdf-121">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="edcdf-122">(değerlendirilmedi)</span><span class="sxs-lookup"><span data-stu-id="edcdf-122">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="edcdf-123">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="edcdf-123">Data Types</span></span>  

 <span data-ttu-id="edcdf-124">`OrElse`İşleci yalnızca [Boole veri türü](../data-types/boolean-data-type.md)için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="edcdf-124">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="edcdf-125">Visual Basic `Boolean` , ifadeyi değerlendirmeden önce her işleneni gerektiği şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="edcdf-125">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="edcdf-126">Sonucu sayısal bir türe atarsanız, Visual Basic, ve haline gelen bu türe dönüştürür `Boolean` `False` `0` `True` `-1` .</span><span class="sxs-lookup"><span data-stu-id="edcdf-126">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="edcdf-127">Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="edcdf-127">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="edcdf-128">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="edcdf-128">Overloading</span></span>  

 <span data-ttu-id="edcdf-129">[OR işleci](or-operator.md) ve [IsTrue işleci](istrue-operator.md) *aşırı* yüklenebilir, bu da bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-129">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="edcdf-130">`Or`Ve işleçlerini aşırı yüklemek `IsTrue` işlecin davranışını etkiler `OrElse` .</span><span class="sxs-lookup"><span data-stu-id="edcdf-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="edcdf-131">Kodunuz `OrElse` , ve ' yi aşırı yükleyen bir sınıf veya yapı üzerinde kullanıyorsa `Or` `IsTrue` , yeniden tanımlanmış davranışlarını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="edcdf-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="edcdf-132">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="edcdf-132">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="edcdf-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="edcdf-133">Example</span></span>  

 <span data-ttu-id="edcdf-134">Aşağıdaki örnek, `OrElse` iki ifadeye mantıksal ayırıcı gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="edcdf-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="edcdf-135">Sonuç, `Boolean` iki deyimden birinin doğru olup olmadığını temsil eden bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="edcdf-136">İlk ifade ise, `True` ikincisi değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="edcdf-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="edcdf-137">Yukarıdaki örnek,, ve gibi sonuçları üretir `True` `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="edcdf-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="edcdf-138">Hesaplamasında `firstCheck` ikinci ifade değerlendirilmez çünkü ilki zaten var `True` .</span><span class="sxs-lookup"><span data-stu-id="edcdf-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="edcdf-139">Ancak, ikinci ifade hesaplamasında değerlendirilir `secondCheck` .</span><span class="sxs-lookup"><span data-stu-id="edcdf-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edcdf-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="edcdf-140">Example</span></span>  

 <span data-ttu-id="edcdf-141">Aşağıdaki örnek, `If` `Then` iki yordam çağrısı içeren bir... ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="edcdf-142">İlk çağrı döndürürse `True` ikinci yordam çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="edcdf-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="edcdf-143">Bu, ikinci yordam kodun bu bölümü çalıştırıldığında her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştirdiğinde beklenmedik sonuçlar verebilir.</span><span class="sxs-lookup"><span data-stu-id="edcdf-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="edcdf-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edcdf-144">See also</span></span>

- [<span data-ttu-id="edcdf-145">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edcdf-145">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="edcdf-146">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="edcdf-146">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="edcdf-147">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="edcdf-147">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="edcdf-148">Or İşleci</span><span class="sxs-lookup"><span data-stu-id="edcdf-148">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="edcdf-149">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="edcdf-149">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="edcdf-150">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="edcdf-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

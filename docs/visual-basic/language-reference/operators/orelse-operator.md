---
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
ms.openlocfilehash: edac3eeaef5d0127f10a0d570ca27c8158806ff3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866719"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="f98e8-102">OrElse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f98e8-102">OrElse Operator (Visual Basic)</span></span>

<span data-ttu-id="f98e8-103">İki ifadeye kısa devre uygulayan kapsamlı mantıksal ayırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f98e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f98e8-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="f98e8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f98e8-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="f98e8-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-106">Required.</span></span> <span data-ttu-id="f98e8-107">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="f98e8-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="f98e8-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-108">Required.</span></span> <span data-ttu-id="f98e8-109">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="f98e8-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f98e8-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-110">Required.</span></span> <span data-ttu-id="f98e8-111">Herhangi bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="f98e8-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f98e8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f98e8-112">Remarks</span></span>  

 <span data-ttu-id="f98e8-113">Derlenmiş kod, başka bir ifadenin sonucuna bağlı olarak bir ifadenin değerlendirmesini atlayabiliyorsa, mantıksal bir işlemin *kısa devre dışı* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="f98e8-114">Değerlendirilen ilk ifadenin sonucu işlemin nihai sonucunu belirlerse, nihai sonucu değiştiremediğinden ikinci ifadeyi değerlendirmeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="f98e8-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="f98e8-115">Atlanan ifade karmaşık olduğunda veya yordam çağrıları içeriyorsa, kısa devre dışı hale getirebilirsiniz performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="f98e8-116">Ya da her iki ifade olarak değerlendirilir `True` `result` `True` .</span><span class="sxs-lookup"><span data-stu-id="f98e8-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="f98e8-117">Aşağıdaki tabloda nasıl belirlendiği gösterilmektedir `result` .</span><span class="sxs-lookup"><span data-stu-id="f98e8-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="f98e8-118">İse `expression1`</span><span class="sxs-lookup"><span data-stu-id="f98e8-118">If `expression1` is</span></span>|<span data-ttu-id="f98e8-119">Ve `expression2`</span><span class="sxs-lookup"><span data-stu-id="f98e8-119">And `expression2` is</span></span>|<span data-ttu-id="f98e8-120">`result`Öğesinin değeri</span><span class="sxs-lookup"><span data-stu-id="f98e8-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="f98e8-121">(değerlendirilmedi)</span><span class="sxs-lookup"><span data-stu-id="f98e8-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="f98e8-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f98e8-122">Data Types</span></span>  

 <span data-ttu-id="f98e8-123">`OrElse`İşleci yalnızca [Boole veri türü](../data-types/boolean-data-type.md)için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f98e8-123">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="f98e8-124">Visual Basic `Boolean` , ifadeyi değerlendirmeden önce her işleneni gerektiği şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f98e8-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="f98e8-125">Sonucu sayısal bir türe atarsanız, Visual Basic, ve haline gelen bu türe dönüştürür `Boolean` `False` `0` `True` `-1` .</span><span class="sxs-lookup"><span data-stu-id="f98e8-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="f98e8-126">Daha fazla bilgi için bkz. [Boole tür dönüştürmeleri](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="f98e8-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="f98e8-127">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="f98e8-127">Overloading</span></span>  

 <span data-ttu-id="f98e8-128">[OR işleci](or-operator.md) ve [IsTrue işleci](istrue-operator.md) *aşırı*yüklenebilir, bu da bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışlarını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-128">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f98e8-129">`Or`Ve işleçlerini aşırı yüklemek `IsTrue` işlecin davranışını etkiler `OrElse` .</span><span class="sxs-lookup"><span data-stu-id="f98e8-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="f98e8-130">Kodunuz `OrElse` , ve ' yi aşırı yükleyen bir sınıf veya yapı üzerinde kullanıyorsa `Or` `IsTrue` , yeniden tanımlanmış davranışlarını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f98e8-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="f98e8-131">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f98e8-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f98e8-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="f98e8-132">Example</span></span>  

 <span data-ttu-id="f98e8-133">Aşağıdaki örnek, `OrElse` iki ifadeye mantıksal ayırıcı gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f98e8-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="f98e8-134">Sonuç, `Boolean` iki deyimden birinin doğru olup olmadığını temsil eden bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="f98e8-135">İlk ifade ise, `True` ikincisi değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="f98e8-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="f98e8-136">Yukarıdaki örnek,, ve gibi sonuçları üretir `True` `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="f98e8-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="f98e8-137">Hesaplamasında `firstCheck` ikinci ifade değerlendirilmez çünkü ilki zaten var `True` .</span><span class="sxs-lookup"><span data-stu-id="f98e8-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="f98e8-138">Ancak, ikinci ifade hesaplamasında değerlendirilir `secondCheck` .</span><span class="sxs-lookup"><span data-stu-id="f98e8-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f98e8-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="f98e8-139">Example</span></span>  

 <span data-ttu-id="f98e8-140">Aşağıdaki örnek, `If` `Then` iki yordam çağrısı içeren bir... ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="f98e8-141">İlk çağrı döndürürse `True` ikinci yordam çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="f98e8-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="f98e8-142">Bu, ikinci yordam kodun bu bölümü çalıştırıldığında her zaman gerçekleştirilmesi gereken önemli görevleri gerçekleştirdiğinde beklenmedik sonuçlar verebilir.</span><span class="sxs-lookup"><span data-stu-id="f98e8-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="f98e8-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f98e8-143">See also</span></span>

- [<span data-ttu-id="f98e8-144">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f98e8-144">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="f98e8-145">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="f98e8-145">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f98e8-146">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="f98e8-146">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f98e8-147">Or İşleci</span><span class="sxs-lookup"><span data-stu-id="f98e8-147">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="f98e8-148">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="f98e8-148">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="f98e8-149">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="f98e8-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

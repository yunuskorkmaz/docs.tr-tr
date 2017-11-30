---
title: "Not İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac160aef7b7dc8acb8bf0211b403599692f2373c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="cd2ff-102">Not İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd2ff-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="cd2ff-103">Mantıksal değilleme gerçekleştiren bir `Boolean` ifadesi veya sayısal ifade bit tabanlı değil işlecini.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd2ff-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="cd2ff-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="cd2ff-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="cd2ff-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-106">Required.</span></span> <span data-ttu-id="cd2ff-107">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="cd2ff-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-108">Required.</span></span> <span data-ttu-id="cd2ff-109">Tüm `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd2ff-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd2ff-110">Remarks</span></span>  
 <span data-ttu-id="cd2ff-111">İçin `Boolean` ifadeler, aşağıdaki tabloda gösterilmektedir nasıl `result` belirlenir.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="cd2ff-112">Varsa `expression` olduğu</span><span class="sxs-lookup"><span data-stu-id="cd2ff-112">If `expression` is</span></span>|<span data-ttu-id="cd2ff-113">Değeri `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="cd2ff-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="cd2ff-114">Sayısal ifadeler için `Not` işleci herhangi bir sayısal ifadeye bit değerini tersine çevirir ve karşılık gelen içinde bit ayarlar `result` aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="cd2ff-115">Varsa, bit `expression` olduğu</span><span class="sxs-lookup"><span data-stu-id="cd2ff-115">If bit in `expression` is</span></span>|<span data-ttu-id="cd2ff-116">Bit `result` olduğu</span><span class="sxs-lookup"><span data-stu-id="cd2ff-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="cd2ff-117">1.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-117">1</span></span>|<span data-ttu-id="cd2ff-118">0</span><span class="sxs-lookup"><span data-stu-id="cd2ff-118">0</span></span>|  
|<span data-ttu-id="cd2ff-119">0</span><span class="sxs-lookup"><span data-stu-id="cd2ff-119">0</span></span>|<span data-ttu-id="cd2ff-120">1.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="cd2ff-121">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçleri düşük önceliğe sahip olduğundan, tüm bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmış.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="cd2ff-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="cd2ff-122">Data Types</span></span>  
 <span data-ttu-id="cd2ff-123">Bir Boole değilleme için sonuç veri türünde `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="cd2ff-124">Bit tabanlı değil işlecini için sonuç veri türü aynı değil `expression`.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="cd2ff-125">Ancak, deyim ise `Decimal`, sonuç `Long`.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="cd2ff-126">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="cd2ff-126">Overloading</span></span>  
 <span data-ttu-id="cd2ff-127">`Not` İşleci olabilir *aşırı*, kendi işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="cd2ff-128">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cd2ff-129">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cd2ff-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd2ff-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd2ff-130">Example</span></span>  
 <span data-ttu-id="cd2ff-131">Aşağıdaki örnek kullanır `Not` mantıksal değilleme gerçekleştirileceği işleci bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="cd2ff-132">Sonuç bir `Boolean` ifadesinin değerini tersine gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 <span data-ttu-id="cd2ff-133">Önceki örnekte sonuçlarını üreten `False` ve `True`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd2ff-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd2ff-134">Example</span></span>  
 <span data-ttu-id="cd2ff-135">Aşağıdaki örnek kullanır `Not` mantıksal olumsuzlaştırma sayısal ifadesinin tek tek bit işleci.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="cd2ff-136">Sonuç düzeninde bit oturum bit dahil olmak üzere işleneni düzeninde karşılık gelen bit ters ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 <span data-ttu-id="cd2ff-137">Önceki örnekte –11, –9 ve –7, sonuçları sırasıyla üretir.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2ff-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd2ff-138">See Also</span></span>  
 [<span data-ttu-id="cd2ff-139">Mantıksal ve bit düzeyinde işleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd2ff-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="cd2ff-140">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="cd2ff-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="cd2ff-141">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="cd2ff-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="cd2ff-142">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="cd2ff-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

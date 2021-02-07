---
description: 'Şu konuda daha fazla bilgi edinin: Not Işleci (Visual Basic)'
title: Not İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Not
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
ms.openlocfilehash: 91f3525b52d6f38081b8e5ba208c193f714a4045
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665360"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="40d44-103">Not İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40d44-103">Not Operator (Visual Basic)</span></span>

<span data-ttu-id="40d44-104">Bir ifadede mantıksal Olumsuzlaştırma `Boolean` veya sayısal ifadede bit tabanlı Olumsuzlaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="40d44-104">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40d44-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="40d44-105">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="40d44-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="40d44-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="40d44-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="40d44-107">Required.</span></span> <span data-ttu-id="40d44-108">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="40d44-108">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="40d44-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="40d44-109">Required.</span></span> <span data-ttu-id="40d44-110">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="40d44-110">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40d44-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40d44-111">Remarks</span></span>  

 <span data-ttu-id="40d44-112">`Boolean`İfadeler için aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="40d44-112">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="40d44-113">İse `expression`</span><span class="sxs-lookup"><span data-stu-id="40d44-113">If `expression` is</span></span>|<span data-ttu-id="40d44-114">`result`Öğesinin değeri</span><span class="sxs-lookup"><span data-stu-id="40d44-114">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="40d44-115">Sayısal ifadeler için işleç, `Not` herhangi bir sayısal ifadenin bit değerlerini tersine çevirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40d44-115">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="40d44-116">Eğer bit `expression` ise</span><span class="sxs-lookup"><span data-stu-id="40d44-116">If bit in `expression` is</span></span>|<span data-ttu-id="40d44-117">`result`İçindeki bit</span><span class="sxs-lookup"><span data-stu-id="40d44-117">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="40d44-118">1</span><span class="sxs-lookup"><span data-stu-id="40d44-118">1</span></span>|<span data-ttu-id="40d44-119">0</span><span class="sxs-lookup"><span data-stu-id="40d44-119">0</span></span>|  
|<span data-ttu-id="40d44-120">0</span><span class="sxs-lookup"><span data-stu-id="40d44-120">0</span></span>|<span data-ttu-id="40d44-121">1</span><span class="sxs-lookup"><span data-stu-id="40d44-121">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="40d44-122">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40d44-122">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="40d44-123">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="40d44-123">Data Types</span></span>  

 <span data-ttu-id="40d44-124">Boolean Olumsuzlaştırma için sonucun veri türü olur `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="40d44-124">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="40d44-125">Bit düzeyinde olumsuzlama için sonuç veri türü, ile aynıdır `expression` .</span><span class="sxs-lookup"><span data-stu-id="40d44-125">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="40d44-126">Ancak, ifadesi ise `Decimal` sonuç olur `Long` .</span><span class="sxs-lookup"><span data-stu-id="40d44-126">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="40d44-127">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="40d44-127">Overloading</span></span>  

 <span data-ttu-id="40d44-128">`Not`İşleç *aşırı* yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="40d44-128">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="40d44-129">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="40d44-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="40d44-130">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="40d44-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40d44-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="40d44-131">Example</span></span>  

 <span data-ttu-id="40d44-132">Aşağıdaki örnek, `Not` bir ifadede mantıksal olumsuzlama gerçekleştirmek için işlecini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="40d44-132">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="40d44-133">Sonuç, `Boolean` ifadenin değerinin ters çevrilme değerini temsil eden bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="40d44-133">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="40d44-134">Yukarıdaki örnek `False` sırasıyla ve, sonuçları üretir `True` .</span><span class="sxs-lookup"><span data-stu-id="40d44-134">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40d44-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="40d44-135">Example</span></span>  

 <span data-ttu-id="40d44-136">Aşağıdaki örnek, `Not` bir sayısal ifadenin ayrı bitlerinin mantıksal olumsuzunu gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="40d44-136">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="40d44-137">Sonuç deseninin biti, işaret biti dahil olmak üzere işlenen deseninin karşılık gelen bitin ters olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="40d44-137">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="40d44-138">Yukarıdaki örnek sırasıyla – 11, – 9 ve – 7 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="40d44-138">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d44-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40d44-139">See also</span></span>

- [<span data-ttu-id="40d44-140">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40d44-140">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="40d44-141">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="40d44-141">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="40d44-142">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="40d44-142">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="40d44-143">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="40d44-143">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

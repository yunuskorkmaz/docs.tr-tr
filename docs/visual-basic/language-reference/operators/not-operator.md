---
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
ms.openlocfilehash: 7d0beea16a2ac00be090c6a241f9790a0ba33390
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874798"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="16176-102">Not İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16176-102">Not Operator (Visual Basic)</span></span>

<span data-ttu-id="16176-103">Bir ifadede mantıksal Olumsuzlaştırma `Boolean` veya sayısal ifadede bit tabanlı Olumsuzlaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="16176-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16176-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16176-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="16176-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="16176-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="16176-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="16176-106">Required.</span></span> <span data-ttu-id="16176-107">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="16176-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="16176-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="16176-108">Required.</span></span> <span data-ttu-id="16176-109">Herhangi bir `Boolean` veya sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="16176-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16176-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16176-110">Remarks</span></span>  

 <span data-ttu-id="16176-111">`Boolean`İfadeler için aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="16176-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="16176-112">İse `expression`</span><span class="sxs-lookup"><span data-stu-id="16176-112">If `expression` is</span></span>|<span data-ttu-id="16176-113">`result`Öğesinin değeri</span><span class="sxs-lookup"><span data-stu-id="16176-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="16176-114">Sayısal ifadeler için işleç, `Not` herhangi bir sayısal ifadenin bit değerlerini tersine çevirir ve karşılık gelen biti `result` aşağıdaki tabloya göre ayarlar.</span><span class="sxs-lookup"><span data-stu-id="16176-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="16176-115">Eğer bit `expression` ise</span><span class="sxs-lookup"><span data-stu-id="16176-115">If bit in `expression` is</span></span>|<span data-ttu-id="16176-116">`result`İçindeki bit</span><span class="sxs-lookup"><span data-stu-id="16176-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="16176-117">1</span><span class="sxs-lookup"><span data-stu-id="16176-117">1</span></span>|<span data-ttu-id="16176-118">0</span><span class="sxs-lookup"><span data-stu-id="16176-118">0</span></span>|  
|<span data-ttu-id="16176-119">0</span><span class="sxs-lookup"><span data-stu-id="16176-119">0</span></span>|<span data-ttu-id="16176-120">1</span><span class="sxs-lookup"><span data-stu-id="16176-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="16176-121">Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="16176-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="16176-122">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="16176-122">Data Types</span></span>  

 <span data-ttu-id="16176-123">Boolean Olumsuzlaştırma için sonucun veri türü olur `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="16176-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="16176-124">Bit düzeyinde olumsuzlama için sonuç veri türü, ile aynıdır `expression` .</span><span class="sxs-lookup"><span data-stu-id="16176-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="16176-125">Ancak, ifadesi ise `Decimal` sonuç olur `Long` .</span><span class="sxs-lookup"><span data-stu-id="16176-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="16176-126">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="16176-126">Overloading</span></span>  

 <span data-ttu-id="16176-127">`Not`İşleç *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="16176-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="16176-128">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="16176-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="16176-129">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="16176-129">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16176-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="16176-130">Example</span></span>  

 <span data-ttu-id="16176-131">Aşağıdaki örnek, `Not` bir ifadede mantıksal olumsuzlama gerçekleştirmek için işlecini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="16176-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="16176-132">Sonuç, `Boolean` ifadenin değerinin ters çevrilme değerini temsil eden bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="16176-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="16176-133">Yukarıdaki örnek `False` sırasıyla ve, sonuçları üretir `True` .</span><span class="sxs-lookup"><span data-stu-id="16176-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16176-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="16176-134">Example</span></span>  

 <span data-ttu-id="16176-135">Aşağıdaki örnek, `Not` bir sayısal ifadenin ayrı bitlerinin mantıksal olumsuzunu gerçekleştirmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16176-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="16176-136">Sonuç deseninin biti, işaret biti dahil olmak üzere işlenen deseninin karşılık gelen bitin ters olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="16176-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="16176-137">Yukarıdaki örnek sırasıyla – 11, – 9 ve – 7 sonuçlarını üretir.</span><span class="sxs-lookup"><span data-stu-id="16176-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16176-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16176-138">See also</span></span>

- [<span data-ttu-id="16176-139">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16176-139">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="16176-140">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="16176-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="16176-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="16176-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="16176-142">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="16176-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)

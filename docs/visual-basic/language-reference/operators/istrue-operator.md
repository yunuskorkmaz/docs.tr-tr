---
title: IsTrue İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: cb8ad8cb4a1ec13611edfcc3de7f4b7eb33fc553
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829934"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="14eae-102">IsTrue İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14eae-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="14eae-103">Bir ifade olup olmadığını belirler `True`.</span><span class="sxs-lookup"><span data-stu-id="14eae-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="14eae-104">Çağıramazsınız `IsTrue` açıkça kodunuzu kullanabilirsiniz, ancak Visual Basic derleyici Bu kod oluşturmak için `OrElse` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="14eae-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="14eae-105">Bir sınıf veya yapı tanımlayın ve ardından bu türde bir değişken kullanmak, bir `OrElse` yan tümcesi tanımlamalıdır `IsTrue` Bu sınıf ya da yapı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="14eae-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="14eae-106">Derleyici göz önünde bulundurur `IsTrue` ve `IsFalse` işleçleri bir *çifti eşleşen*.</span><span class="sxs-lookup"><span data-stu-id="14eae-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="14eae-107">Başka bir deyişle, bir tanesi tanımlarsanız, ayrıca diğeri tanımladığınız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14eae-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="14eae-108">IsTrue derleyici kullanımı</span><span class="sxs-lookup"><span data-stu-id="14eae-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="14eae-109">Bir sınıf veya yapı tanımlandığında, bu türde bir değişken kullanabileceğiniz bir `For`, `If`, `Else If`, veya `While` deyimi veya bir `When` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="14eae-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="14eae-110">Bunu yaparsanız, derleyici, türüne dönüştürür bir işleç gerektiriyor. bir `Boolean` koşul sınayabilmeniz değeri.</span><span class="sxs-lookup"><span data-stu-id="14eae-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="14eae-111">Uygun bir işleç şu sırayla arar:</span><span class="sxs-lookup"><span data-stu-id="14eae-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="14eae-112">Genişleyen bir dönüştürme operatörünün sınıfı veya yapısına `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="14eae-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="14eae-113">Genişleyen bir dönüştürme operatörünün sınıfı veya yapısına `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="14eae-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="14eae-114">`IsTrue` İşleci, sınıf ya da yapı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="14eae-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="14eae-115">Bir daraltma dönüşümü için `Boolean?` , değil içeren bir dönüştürme `Boolean` için `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="14eae-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="14eae-116">Bir daraltma dönüşümü işleci sınıfı veya yapısına `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="14eae-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="14eae-117">Herhangi bir dönüştürmeyi tanımlamadıysanız `Boolean` veya `IsTrue` işleci, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="14eae-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14eae-118">`IsTrue` İşleci olabilir *aşırı*, kendi işleneninin türü, sınıfın veya yapının olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="14eae-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="14eae-119">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="14eae-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="14eae-120">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="14eae-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14eae-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="14eae-121">Example</span></span>  
 <span data-ttu-id="14eae-122">Aşağıdaki kod örneği için tanımları içeren bir yapının anahat tanımlar `IsFalse` ve `IsTrue` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="14eae-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="14eae-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14eae-123">See also</span></span>

- [<span data-ttu-id="14eae-124">IsFalse İşleci</span><span class="sxs-lookup"><span data-stu-id="14eae-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="14eae-125">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="14eae-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="14eae-126">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="14eae-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)

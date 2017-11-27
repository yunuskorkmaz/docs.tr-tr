---
title: "IsTrue İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0d261186ce68f06cec95251e815248a189f6da5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="6fc7e-102">IsTrue İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fc7e-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="6fc7e-103">Bir ifade olup olmadığını belirleyen `True`.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="6fc7e-104">Çağıramazsınız `IsTrue` açıkça kodunuzu, ancak Visual Basic derleyici koddan oluşturmak için kullanabilmesi `OrElse` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="6fc7e-105">Bir sınıf veya yapı tanımlayın ve ardından bu tür bir değişken kullanırsanız bir `OrElse` yan tümcesi tanımlamalıdır `IsTrue` sınıf veya yapı.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="6fc7e-106">Derleyici göz önünde bulundurur `IsTrue` ve `IsFalse` işletmenler olarak bir *çifti eşleşen*.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="6fc7e-107">Bu, bunlardan birini tanımlarsanız, ayrıca diğeri tanımlamanız gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="6fc7e-108">IsTrue derleyici kullanımı</span><span class="sxs-lookup"><span data-stu-id="6fc7e-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="6fc7e-109">Bir sınıf veya yapı tanımlandığında, bu tür bir değişkeni kullanabilirsiniz bir `For`, `If`, `Else``If`, veya `While` deyimi, veya bir `When` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else``If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="6fc7e-110">Bunu yaparsanız, derleyici, türe dönüştürür bir işleç gerektiren bir `Boolean` bir koşulu test etmek için değer.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="6fc7e-111">Uygun bir işleç aşağıdaki sırayla arar:</span><span class="sxs-lookup"><span data-stu-id="6fc7e-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="6fc7e-112">Sınıf veya yapı için bir genişletme dönüşüm işleci `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="6fc7e-113">Sınıf veya yapı için bir genişletme dönüşüm işleci `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="6fc7e-114">`IsTrue` Sınıf veya yapı işlecinin.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="6fc7e-115">Daraltma dönüştürmeye `Boolean?` dönüştürme kapsamaz `Boolean` için `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="6fc7e-116">Sınıf veya yapı için daraltma bir dönüşüm işleci `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="6fc7e-117">Herhangi bir dönüştürmeye tanımladıysanız `Boolean` veya bir `IsTrue` işleci, derleyici, bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fc7e-118">`IsTrue` İşleci olabilir *aşırı*, kendi işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="6fc7e-119">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6fc7e-120">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6fc7e-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc7e-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="6fc7e-121">Example</span></span>  
 <span data-ttu-id="6fc7e-122">Aşağıdaki kod örneği için tanımları içeren bir yapı özetini tanımlar `IsFalse` ve `IsTrue` işleçler.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6fc7e-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fc7e-123">See Also</span></span>  
 [<span data-ttu-id="6fc7e-124">IsFalse işleci</span><span class="sxs-lookup"><span data-stu-id="6fc7e-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="6fc7e-125">Nasıl yapılır: bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="6fc7e-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="6fc7e-126">OrElse işleci</span><span class="sxs-lookup"><span data-stu-id="6fc7e-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)

---
title: IsFalse İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: e84b2162eb0763725f05bc52d5c4223d7c430b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600054"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="3c665-102">IsFalse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c665-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="3c665-103">Bir ifade olup olmadığını belirleyen `False`.</span><span class="sxs-lookup"><span data-stu-id="3c665-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="3c665-104">Çağıramazsınız `IsFalse` açıkça kodunuzu, ancak Visual Basic derleyici koddan oluşturmak için kullanabilmesi `AndAlso` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="3c665-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="3c665-105">Bir sınıf veya yapı tanımlayın ve ardından bu tür bir değişken kullanırsanız bir `AndAlso` yan tümcesi tanımlamalıdır `IsFalse` sınıf veya yapı.</span><span class="sxs-lookup"><span data-stu-id="3c665-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="3c665-106">Derleyici göz önünde bulundurur `IsFalse` ve `IsTrue` işletmenler olarak bir *çifti eşleşen*.</span><span class="sxs-lookup"><span data-stu-id="3c665-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="3c665-107">Bu, bunlardan birini tanımlarsanız, ayrıca diğeri tanımlamanız gerektiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3c665-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c665-108">`IsFalse` İşleci olabilir *aşırı*, kendi işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3c665-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="3c665-109">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3c665-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3c665-110">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3c665-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c665-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c665-111">Example</span></span>  
 <span data-ttu-id="3c665-112">Aşağıdaki kod örneği için tanımları içeren bir yapı özetini tanımlar `IsFalse` ve `IsTrue` işleçler.</span><span class="sxs-lookup"><span data-stu-id="3c665-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3c665-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c665-113">See Also</span></span>  
 [<span data-ttu-id="3c665-114">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="3c665-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="3c665-115">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="3c665-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="3c665-116">AndAlso İşleci</span><span class="sxs-lookup"><span data-stu-id="3c665-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)

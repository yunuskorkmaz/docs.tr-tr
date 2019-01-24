---
title: IsFalse İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: ec8d7bcd2f4ca3fb1c74f4edcf6ec8af78fd144d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740443"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="d78d2-102">IsFalse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d78d2-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="d78d2-103">Bir ifade olup olmadığını belirler `False`.</span><span class="sxs-lookup"><span data-stu-id="d78d2-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="d78d2-104">Çağıramazsınız `IsFalse` açıkça kodunuzu kullanabilirsiniz, ancak Visual Basic derleyici Bu kod oluşturmak için `AndAlso` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="d78d2-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="d78d2-105">Bir sınıf veya yapı tanımlayın ve ardından bu türde bir değişken kullanmak, bir `AndAlso` yan tümcesi tanımlamalıdır `IsFalse` Bu sınıf ya da yapı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d78d2-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="d78d2-106">Derleyici göz önünde bulundurur `IsFalse` ve `IsTrue` işleçleri bir *çifti eşleşen*.</span><span class="sxs-lookup"><span data-stu-id="d78d2-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="d78d2-107">Başka bir deyişle, bir tanesi tanımlarsanız, ayrıca diğeri tanımladığınız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d78d2-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d78d2-108">`IsFalse` İşleci olabilir *aşırı*, kendi işleneninin türü, sınıfın veya yapının olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d78d2-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="d78d2-109">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d78d2-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d78d2-110">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d78d2-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d78d2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d78d2-111">Example</span></span>  
 <span data-ttu-id="d78d2-112">Aşağıdaki kod örneği için tanımları içeren bir yapının anahat tanımlar `IsFalse` ve `IsTrue` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="d78d2-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d78d2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d78d2-113">See also</span></span>
- [<span data-ttu-id="d78d2-114">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="d78d2-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="d78d2-115">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="d78d2-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="d78d2-116">AndAlso İşleci</span><span class="sxs-lookup"><span data-stu-id="d78d2-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)

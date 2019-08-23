---
title: IsFalse İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917150"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="9b14d-102">IsFalse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b14d-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="9b14d-103">Bir ifadenin `False`olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9b14d-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="9b14d-104">Kodunuzda açıkça çağrı `IsFalse` yapılamaz, ancak Visual Basic Derleyicisi bunu yan tümcelerden `AndAlso` kod oluşturmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9b14d-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="9b14d-105">Bir sınıf veya yapı tanımlayabilir ve sonra bir `AndAlso` yan tümce içinde bu türden bir değişken kullanırsanız, bu sınıf veya yapıda tanımlamanız `IsFalse` gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b14d-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="9b14d-106">Derleyici, `IsFalse` ve `IsTrue` işleçlerini eşleşen bir *çift*olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="9b14d-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="9b14d-107">Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b14d-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b14d-108">İşleç aşırı yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="9b14d-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="9b14d-109">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9b14d-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9b14d-110">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9b14d-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b14d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b14d-111">Example</span></span>  
 <span data-ttu-id="9b14d-112">Aşağıdaki kod örneği, `IsFalse` ve `IsTrue` işleçleri için tanımlar içeren bir yapının ana hattını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9b14d-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="9b14d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b14d-113">See also</span></span>

- [<span data-ttu-id="9b14d-114">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="9b14d-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="9b14d-115">Nasıl yapılır: Bir Işleç tanımlayın</span><span class="sxs-lookup"><span data-stu-id="9b14d-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="9b14d-116">AndAlso İşleci</span><span class="sxs-lookup"><span data-stu-id="9b14d-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)

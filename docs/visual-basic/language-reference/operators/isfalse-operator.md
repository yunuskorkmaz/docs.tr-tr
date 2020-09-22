---
title: IsFalse İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: bbcdb9bcf645a4e9cb54c657ccd46e04437d207e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873385"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="03226-102">IsFalse İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03226-102">IsFalse Operator (Visual Basic)</span></span>

<span data-ttu-id="03226-103">Bir ifadenin olup olmadığını belirler `False` .</span><span class="sxs-lookup"><span data-stu-id="03226-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="03226-104">`IsFalse`Kodunuzda açıkça çağrı yapılamaz, ancak Visual Basic Derleyicisi bunu yan tümcelerden kod oluşturmak için kullanabilir `AndAlso` .</span><span class="sxs-lookup"><span data-stu-id="03226-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="03226-105">Bir sınıf veya yapı tanımlayabilir ve sonra bir yan tümce içinde bu türden bir değişken kullanırsanız `AndAlso` , `IsFalse` Bu sınıf veya yapıda tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03226-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="03226-106">Derleyici, `IsFalse` ve `IsTrue` işleçlerini *eşleşen bir çift*olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="03226-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="03226-107">Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03226-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03226-108">`IsFalse`İşleç *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="03226-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="03226-109">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="03226-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="03226-110">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="03226-110">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03226-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="03226-111">Example</span></span>  

 <span data-ttu-id="03226-112">Aşağıdaki kod örneği, ve işleçleri için tanımlar içeren bir yapının ana hattını tanımlar `IsFalse` `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="03226-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="03226-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03226-113">See also</span></span>

- [<span data-ttu-id="03226-114">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="03226-114">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="03226-115">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="03226-115">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="03226-116">AndAlso İşleci</span><span class="sxs-lookup"><span data-stu-id="03226-116">AndAlso Operator</span></span>](andalso-operator.md)

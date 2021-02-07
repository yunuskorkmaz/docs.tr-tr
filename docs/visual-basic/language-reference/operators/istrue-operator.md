---
description: 'Daha fazla bilgi edinin: IsTrue Işleci (Visual Basic)'
title: IsTrue İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 50b618c888ce988da5241041fb2f728e0a581c70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665659"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="6f21d-103">IsTrue İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f21d-103">IsTrue Operator (Visual Basic)</span></span>

<span data-ttu-id="6f21d-104">Bir ifadenin olup olmadığını belirler `True` .</span><span class="sxs-lookup"><span data-stu-id="6f21d-104">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="6f21d-105">`IsTrue`Kodunuzda açıkça çağrı yapılamaz, ancak Visual Basic Derleyicisi bunu yan tümcelerden kod oluşturmak için kullanabilir `OrElse` .</span><span class="sxs-lookup"><span data-stu-id="6f21d-105">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="6f21d-106">Bir sınıf veya yapı tanımlayabilir ve sonra bir yan tümce içinde bu türden bir değişken kullanırsanız `OrElse` , `IsTrue` Bu sınıf veya yapıda tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f21d-106">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="6f21d-107">Derleyici, `IsTrue` ve `IsFalse` işleçlerini *eşleşen bir çift* olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6f21d-107">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="6f21d-108">Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f21d-108">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="6f21d-109">Iıstrue derleyicisi kullanımı</span><span class="sxs-lookup"><span data-stu-id="6f21d-109">Compiler Use of IsTrue</span></span>  

 <span data-ttu-id="6f21d-110">Bir sınıf veya yapı tanımladığınızda,,, `For` `If` `Else If` , veya `While` deyimi içinde veya `When` yan tümcesinde bu türde bir değişken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f21d-110">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="6f21d-111">Bunu yaparsanız, derleyici, `Boolean` bir koşulu test edebilmesi için türünüzü bir değere dönüştüren bir operatör gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6f21d-111">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="6f21d-112">Uygun bir işleci aşağıdaki sırayla arar:</span><span class="sxs-lookup"><span data-stu-id="6f21d-112">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="6f21d-113">Sınıfınız veya yapıınızdan ' ye genişleyen bir dönüştürme işleci `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="6f21d-113">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="6f21d-114">Sınıfınız veya yapıınızdan ' ye genişleyen bir dönüştürme işleci `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="6f21d-114">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="6f21d-115">`IsTrue`Sınıfınıza veya yapınıza yönelik operatör.</span><span class="sxs-lookup"><span data-stu-id="6f21d-115">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="6f21d-116">' A `Boolean?` bir dönüştürme içermeyen bir daraltma dönüştürmesi `Boolean` `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="6f21d-116">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="6f21d-117">Sınıfınız veya yapıınızdan ' ye bir daraltma dönüştürme işleci `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="6f21d-117">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="6f21d-118">Ya da işlecine herhangi bir dönüştürme tanımdıysanız `Boolean` `IsTrue` , derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f21d-118">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f21d-119">`IsTrue`İşleç *aşırı* yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6f21d-119">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="6f21d-120">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6f21d-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6f21d-121">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6f21d-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f21d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f21d-122">Example</span></span>  

 <span data-ttu-id="6f21d-123">Aşağıdaki kod örneği, ve işleçleri için tanımlar içeren bir yapının ana hattını tanımlar `IsFalse` `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="6f21d-123">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="6f21d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f21d-124">See also</span></span>

- [<span data-ttu-id="6f21d-125">IsFalse İşleci</span><span class="sxs-lookup"><span data-stu-id="6f21d-125">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="6f21d-126">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="6f21d-126">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="6f21d-127">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="6f21d-127">OrElse Operator</span></span>](orelse-operator.md)

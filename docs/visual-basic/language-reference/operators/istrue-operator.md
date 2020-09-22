---
title: IsTrue İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 2e67a4adabe58ab12d317ae6318c0a2fac29da7d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866940"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="96418-102">IsTrue İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96418-102">IsTrue Operator (Visual Basic)</span></span>

<span data-ttu-id="96418-103">Bir ifadenin olup olmadığını belirler `True` .</span><span class="sxs-lookup"><span data-stu-id="96418-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="96418-104">`IsTrue`Kodunuzda açıkça çağrı yapılamaz, ancak Visual Basic Derleyicisi bunu yan tümcelerden kod oluşturmak için kullanabilir `OrElse` .</span><span class="sxs-lookup"><span data-stu-id="96418-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="96418-105">Bir sınıf veya yapı tanımlayabilir ve sonra bir yan tümce içinde bu türden bir değişken kullanırsanız `OrElse` , `IsTrue` Bu sınıf veya yapıda tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96418-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="96418-106">Derleyici, `IsTrue` ve `IsFalse` işleçlerini *eşleşen bir çift*olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="96418-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="96418-107">Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96418-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="96418-108">Iıstrue derleyicisi kullanımı</span><span class="sxs-lookup"><span data-stu-id="96418-108">Compiler Use of IsTrue</span></span>  

 <span data-ttu-id="96418-109">Bir sınıf veya yapı tanımladığınızda,,, `For` `If` `Else If` , veya `While` deyimi içinde veya `When` yan tümcesinde bu türde bir değişken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96418-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="96418-110">Bunu yaparsanız, derleyici, `Boolean` bir koşulu test edebilmesi için türünüzü bir değere dönüştüren bir operatör gerektirir.</span><span class="sxs-lookup"><span data-stu-id="96418-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="96418-111">Uygun bir işleci aşağıdaki sırayla arar:</span><span class="sxs-lookup"><span data-stu-id="96418-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="96418-112">Sınıfınız veya yapıınızdan ' ye genişleyen bir dönüştürme işleci `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="96418-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="96418-113">Sınıfınız veya yapıınızdan ' ye genişleyen bir dönüştürme işleci `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="96418-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="96418-114">`IsTrue`Sınıfınıza veya yapınıza yönelik operatör.</span><span class="sxs-lookup"><span data-stu-id="96418-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="96418-115">' A `Boolean?` bir dönüştürme içermeyen bir daraltma dönüştürmesi `Boolean` `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="96418-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="96418-116">Sınıfınız veya yapıınızdan ' ye bir daraltma dönüştürme işleci `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="96418-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="96418-117">Ya da işlecine herhangi bir dönüştürme tanımdıysanız `Boolean` `IsTrue` , derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="96418-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96418-118">`IsTrue`İşleç *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="96418-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="96418-119">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="96418-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="96418-120">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="96418-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96418-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="96418-121">Example</span></span>  

 <span data-ttu-id="96418-122">Aşağıdaki kod örneği, ve işleçleri için tanımlar içeren bir yapının ana hattını tanımlar `IsFalse` `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="96418-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="96418-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96418-123">See also</span></span>

- [<span data-ttu-id="96418-124">IsFalse İşleci</span><span class="sxs-lookup"><span data-stu-id="96418-124">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="96418-125">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="96418-125">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="96418-126">OrElse İşleci</span><span class="sxs-lookup"><span data-stu-id="96418-126">OrElse Operator</span></span>](orelse-operator.md)

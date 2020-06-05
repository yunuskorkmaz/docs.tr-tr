---
title: /= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 48ae78630aa66ad804d539f88524c456cf805889
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371251"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="20519-102">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20519-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="20519-103">Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve kayan nokta sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="20519-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20519-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20519-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="20519-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="20519-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="20519-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="20519-106">Required.</span></span> <span data-ttu-id="20519-107">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="20519-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="20519-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="20519-108">Required.</span></span> <span data-ttu-id="20519-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="20519-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20519-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20519-110">Remarks</span></span>  
 <span data-ttu-id="20519-111">İşlecinin sol tarafındaki öğesi `/=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="20519-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="20519-112">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="20519-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="20519-113">`/=`İşleci ilk olarak, değişkenin değerini (işlecin sol tarafında), ifadenin değerine (işlecinin sağ tarafında) böler (işleci).</span><span class="sxs-lookup"><span data-stu-id="20519-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="20519-114">İşleci daha sonra bu işlemin kayan nokta sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="20519-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="20519-115">Bu ifade `Double` , sol taraftaki değişkene veya özelliğe bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="20519-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="20519-116">İse `Option Strict` `On` , `variableorproperty` bir olmalıdır `Double` .</span><span class="sxs-lookup"><span data-stu-id="20519-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="20519-117">`Option Strict`İse, `Off` Visual Basic örtük bir dönüştürme gerçekleştirir ve elde edilen değeri `variableorproperty` çalışma zamanında olası bir hatayla atar.</span><span class="sxs-lookup"><span data-stu-id="20519-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="20519-118">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimdir](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="20519-118">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="20519-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="20519-119">Overloading</span></span>  
 <span data-ttu-id="20519-120">[/İşleci (Visual Basic)](floating-point-division-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="20519-120">The [/ Operator (Visual Basic)](floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="20519-121">İşleci aşırı yüklemek `/` işlecin davranışını etkiler `/=` .</span><span class="sxs-lookup"><span data-stu-id="20519-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="20519-122">Kodunuzun `/=` bir sınıf veya yapı üzerinde kullanması durumunda `/` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="20519-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="20519-123">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="20519-123">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20519-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="20519-124">Example</span></span>  
 <span data-ttu-id="20519-125">Aşağıdaki örnek, `/=` bir `Integer` değişkeni ikinci bir kez bölmek ve bölümü ilk değişkene atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="20519-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="20519-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20519-126">See also</span></span>

- [<span data-ttu-id="20519-127">/İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20519-127">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="20519-128">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="20519-128">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="20519-129">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="20519-129">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="20519-130">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="20519-130">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="20519-131">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="20519-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="20519-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="20519-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="20519-133">Deyimler</span><span class="sxs-lookup"><span data-stu-id="20519-133">Statements</span></span>](../../programming-guide/language-features/statements.md)

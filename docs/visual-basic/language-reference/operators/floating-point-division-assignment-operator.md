---
description: Hakkında daha fazla bilgi edinin:/= Işleci (Visual Basic)
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
ms.openlocfilehash: 3020372be18f554df18fa6dac539ab9d0b2f725e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666036"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="35344-103">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35344-103">/= Operator (Visual Basic)</span></span>

<span data-ttu-id="35344-104">Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve kayan nokta sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="35344-104">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35344-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="35344-105">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="35344-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="35344-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="35344-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="35344-107">Required.</span></span> <span data-ttu-id="35344-108">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="35344-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="35344-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="35344-109">Required.</span></span> <span data-ttu-id="35344-110">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="35344-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35344-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35344-111">Remarks</span></span>  

 <span data-ttu-id="35344-112">İşlecinin sol tarafındaki öğesi `/=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="35344-112">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="35344-113">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="35344-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="35344-114">`/=`İşleci ilk olarak, değişkenin değerini (işlecin sol tarafında), ifadenin değerine (işlecinin sağ tarafında) böler (işleci).</span><span class="sxs-lookup"><span data-stu-id="35344-114">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="35344-115">İşleci daha sonra bu işlemin kayan nokta sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="35344-115">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="35344-116">Bu ifade `Double` , sol taraftaki değişkene veya özelliğe bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="35344-116">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="35344-117">İse `Option Strict` `On` , `variableorproperty` bir olmalıdır `Double` .</span><span class="sxs-lookup"><span data-stu-id="35344-117">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="35344-118">`Option Strict`İse, `Off` Visual Basic örtük bir dönüştürme gerçekleştirir ve elde edilen değeri `variableorproperty` çalışma zamanında olası bir hatayla atar.</span><span class="sxs-lookup"><span data-stu-id="35344-118">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="35344-119">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimdir](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="35344-119">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="35344-120">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="35344-120">Overloading</span></span>  

 <span data-ttu-id="35344-121">[/İşleci (Visual Basic)](floating-point-division-operator.md) *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="35344-121">The [/ Operator (Visual Basic)](floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="35344-122">İşleci aşırı yüklemek `/` işlecin davranışını etkiler `/=` .</span><span class="sxs-lookup"><span data-stu-id="35344-122">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="35344-123">Kodunuzun `/=` bir sınıf veya yapı üzerinde kullanması durumunda `/` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="35344-123">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="35344-124">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="35344-124">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35344-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="35344-125">Example</span></span>  

 <span data-ttu-id="35344-126">Aşağıdaki örnek, `/=` bir `Integer` değişkeni ikinci bir kez bölmek ve bölümü ilk değişkene atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="35344-126">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="35344-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35344-127">See also</span></span>

- [<span data-ttu-id="35344-128">/İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35344-128">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="35344-129">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="35344-129">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="35344-130">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="35344-130">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="35344-131">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="35344-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="35344-132">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="35344-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="35344-133">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="35344-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="35344-134">Deyimler</span><span class="sxs-lookup"><span data-stu-id="35344-134">Statements</span></span>](../../programming-guide/language-features/statements.md)

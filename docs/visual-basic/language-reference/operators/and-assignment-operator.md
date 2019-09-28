---
title: '&amp; = Işleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 82d791e5d66c301442c99d2cc73e3172c3e30f17
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591632"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="8a055-102">&amp; = Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a055-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="8a055-103">Bir `String` ifadesini `String` değişkenine veya özelliğe ekler ve sonucu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="8a055-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a055-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a055-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="8a055-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8a055-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8a055-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8a055-106">Required.</span></span> <span data-ttu-id="8a055-107">Herhangi bir `String` değişkeni veya özelliği.</span><span class="sxs-lookup"><span data-stu-id="8a055-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="8a055-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8a055-108">Required.</span></span> <span data-ttu-id="8a055-109">Herhangi bir `String` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8a055-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a055-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a055-110">Remarks</span></span>  
 <span data-ttu-id="8a055-111">@No__t-0 işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a055-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8a055-112">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="8a055-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="8a055-113">@No__t-0 işleci, solundaki `String` ifadesini `String` değişkenine veya özelliğine ekler ve sonucu sol taraftaki değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="8a055-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8a055-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="8a055-114">Overloading</span></span>  
 <span data-ttu-id="8a055-115">[& işleci](../../../visual-basic/language-reference/operators/concatenation-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8a055-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8a055-116">@No__t aşırı yükleme-0 işleci `&=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="8a055-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="8a055-117">Kodunuz, `&` ' i aşırı yükleyen bir sınıf veya yapıda `&=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8a055-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8a055-118">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8a055-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a055-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a055-119">Example</span></span>  
 <span data-ttu-id="8a055-120">Aşağıdaki örnek, iki `String` değişkenini birleştirmek ve sonucu ilk değişkene atamak için `&=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a055-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8a055-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a055-121">See also</span></span>

- [<span data-ttu-id="8a055-122">& İşleci</span><span class="sxs-lookup"><span data-stu-id="8a055-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="8a055-123">+= İşleci</span><span class="sxs-lookup"><span data-stu-id="8a055-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="8a055-124">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8a055-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8a055-125">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8a055-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="8a055-126">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="8a055-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8a055-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="8a055-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8a055-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="8a055-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)

---
title: '*= İşleci'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: b06ebcb4f4100a0621f52a769543c0fb24fbb4bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401504"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9a683-102">\*= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a683-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="9a683-103">Bir değişkenin veya özelliğin değerini bir ifadenin değeri ile çarpar ve sonucu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="9a683-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a683-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a683-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9a683-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9a683-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9a683-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9a683-106">Required.</span></span> <span data-ttu-id="9a683-107">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="9a683-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="9a683-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9a683-108">Required.</span></span> <span data-ttu-id="9a683-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="9a683-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a683-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a683-110">Remarks</span></span>  
 <span data-ttu-id="9a683-111">İşlecinin sol tarafındaki öğesi `*=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a683-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9a683-112">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="9a683-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="9a683-113">`*=`İşleci ilk olarak, ifadenin değerini (işlecin sağ tarafında) değişkenin veya özelliğin değeri (işlecin sol tarafında) ile çarpar.</span><span class="sxs-lookup"><span data-stu-id="9a683-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="9a683-114">İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="9a683-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9a683-115">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="9a683-115">Overloading</span></span>  
 <span data-ttu-id="9a683-116">[\* İşleci](multiplication-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9a683-116">The [\* Operator](multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9a683-117">İşleci aşırı yüklemek `*` işlecin davranışını etkiler `*=` .</span><span class="sxs-lookup"><span data-stu-id="9a683-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="9a683-118">Kodunuzun `*=` bir sınıf veya yapı üzerinde kullanması durumunda `*` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9a683-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9a683-119">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9a683-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a683-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a683-120">Example</span></span>  
 <span data-ttu-id="9a683-121">Aşağıdaki örnek, `*=` bir `Integer` değişkeni ikinci olarak çarpmak ve sonucu ilk değişkene atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a683-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="9a683-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a683-122">See also</span></span>

- [<span data-ttu-id="9a683-123">\* İşleci</span><span class="sxs-lookup"><span data-stu-id="9a683-123">\* Operator</span></span>](multiplication-operator.md)
- [<span data-ttu-id="9a683-124">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="9a683-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="9a683-125">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="9a683-125">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="9a683-126">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="9a683-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="9a683-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9a683-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="9a683-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="9a683-128">Statements</span></span>](../../programming-guide/language-features/statements.md)

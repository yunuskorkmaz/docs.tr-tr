---
title: '&amp;= İşleci'
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
ms.openlocfilehash: db42f7be7225b866eacf5b73066754e91cd1a0f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371992"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="13a05-102">&amp;= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13a05-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="13a05-103">Bir `String` ifadeyi bir `String` değişkene veya özelliğe ekler ve sonucu değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="13a05-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13a05-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="13a05-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="13a05-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="13a05-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="13a05-106">Required.</span></span> <span data-ttu-id="13a05-107">Herhangi bir `String` değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="13a05-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="13a05-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="13a05-108">Required.</span></span> <span data-ttu-id="13a05-109">Herhangi bir `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="13a05-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13a05-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13a05-110">Remarks</span></span>  
 <span data-ttu-id="13a05-111">İşlecinin sol tarafındaki öğesi `&=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="13a05-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="13a05-112">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="13a05-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="13a05-113">İşleci, sol tarafında bulunan `&=` `String` değişkeni ya da özelliği için sağ taraftaki ifadeyi birleştirir `String` ve sonucu, sol tarafındaki değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="13a05-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="13a05-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="13a05-114">Overloading</span></span>  
 <span data-ttu-id="13a05-115">[& işleci](concatenation-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="13a05-115">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="13a05-116">İşleci aşırı yüklemek `&` işlecin davranışını etkiler `&=` .</span><span class="sxs-lookup"><span data-stu-id="13a05-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="13a05-117">Kodunuzun `&=` bir sınıf veya yapı üzerinde kullanması durumunda `&` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="13a05-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="13a05-118">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="13a05-118">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a05-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="13a05-119">Example</span></span>  
 <span data-ttu-id="13a05-120">Aşağıdaki örnek, `&=` iki `String` değişkeni birleştirmek ve sonucu ilk değişkene atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="13a05-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="13a05-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13a05-121">See also</span></span>

- [<span data-ttu-id="13a05-122">& Işleci</span><span class="sxs-lookup"><span data-stu-id="13a05-122">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="13a05-123">+ = İşleci</span><span class="sxs-lookup"><span data-stu-id="13a05-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="13a05-124">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="13a05-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="13a05-125">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="13a05-125">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="13a05-126">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="13a05-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="13a05-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="13a05-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="13a05-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="13a05-128">Statements</span></span>](../../programming-guide/language-features/statements.md)

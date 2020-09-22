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
ms.openlocfilehash: 9b77c44aa77afd59e36e1d21451205d3929ef527
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874882"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="a972b-102">&amp;= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a972b-102">&amp;= Operator (Visual Basic)</span></span>

<span data-ttu-id="a972b-103">Bir `String` ifadeyi bir `String` değişkene veya özelliğe ekler ve sonucu değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="a972b-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a972b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a972b-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a972b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a972b-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="a972b-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a972b-106">Required.</span></span> <span data-ttu-id="a972b-107">Herhangi bir `String` değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="a972b-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="a972b-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a972b-108">Required.</span></span> <span data-ttu-id="a972b-109">Herhangi bir `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="a972b-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a972b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a972b-110">Remarks</span></span>  

 <span data-ttu-id="a972b-111">İşlecinin sol tarafındaki öğesi `&=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="a972b-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="a972b-112">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="a972b-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="a972b-113">İşleci, sol tarafında bulunan `&=` `String` değişkeni ya da özelliği için sağ taraftaki ifadeyi birleştirir `String` ve sonucu, sol tarafındaki değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="a972b-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a972b-114">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="a972b-114">Overloading</span></span>  

 <span data-ttu-id="a972b-115">[& işleci](concatenation-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a972b-115">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a972b-116">İşleci aşırı yüklemek `&` işlecin davranışını etkiler `&=` .</span><span class="sxs-lookup"><span data-stu-id="a972b-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="a972b-117">Kodunuzun `&=` bir sınıf veya yapı üzerinde kullanması durumunda `&` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a972b-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a972b-118">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a972b-118">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a972b-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a972b-119">Example</span></span>  

 <span data-ttu-id="a972b-120">Aşağıdaki örnek, `&=` iki `String` değişkeni birleştirmek ve sonucu ilk değişkene atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a972b-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a972b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a972b-121">See also</span></span>

- [<span data-ttu-id="a972b-122">& Işleci</span><span class="sxs-lookup"><span data-stu-id="a972b-122">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="a972b-123">+ = İşleci</span><span class="sxs-lookup"><span data-stu-id="a972b-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="a972b-124">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="a972b-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="a972b-125">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="a972b-125">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="a972b-126">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="a972b-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a972b-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="a972b-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a972b-128">Deyimler</span><span class="sxs-lookup"><span data-stu-id="a972b-128">Statements</span></span>](../../programming-guide/language-features/statements.md)

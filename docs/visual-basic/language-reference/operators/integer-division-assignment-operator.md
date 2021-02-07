---
description: ': = Işleci hakkında daha fazla bilgi'
title: '\= İşleci'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: a05e136cbf17eaf7102fb2213993adf9cf0e06be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665815"
---
# <a name="-operator"></a><span data-ttu-id="354a1-103">\\= İşleci</span><span class="sxs-lookup"><span data-stu-id="354a1-103">\\= Operator</span></span>

<span data-ttu-id="354a1-104">Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve tamsayı sonucunu değişkene veya özelliğe atar.</span><span class="sxs-lookup"><span data-stu-id="354a1-104">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="354a1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="354a1-105">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="354a1-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="354a1-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="354a1-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="354a1-107">Required.</span></span> <span data-ttu-id="354a1-108">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="354a1-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="354a1-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="354a1-109">Required.</span></span> <span data-ttu-id="354a1-110">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="354a1-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="354a1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="354a1-111">Remarks</span></span>  

 <span data-ttu-id="354a1-112">İşlecinin sol tarafındaki öğesi `\=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="354a1-112">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="354a1-113">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="354a1-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="354a1-114">`\=`İşleci, bir değişkenin veya özelliğin değerini solundaki değer ile sola böler ve tamsayı sonucunu sol tarafındaki değişkene veya özelliğe atar</span><span class="sxs-lookup"><span data-stu-id="354a1-114">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="354a1-115">Tamsayı bölme hakkında daha fazla bilgi için bkz. [\ işleç (Visual Basic)](integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="354a1-115">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="354a1-116">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="354a1-116">Overloading</span></span>  

 <span data-ttu-id="354a1-117">`\`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="354a1-117">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="354a1-118">İşleci aşırı yüklemek `\` işlecin davranışını etkiler `\=` .</span><span class="sxs-lookup"><span data-stu-id="354a1-118">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="354a1-119">Kodunuzun `\=` bir sınıf veya yapı üzerinde kullanması durumunda `\` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="354a1-119">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="354a1-120">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="354a1-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="354a1-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="354a1-121">Example</span></span>  

 <span data-ttu-id="354a1-122">Aşağıdaki örnek, `\=` bir `Integer` değişkeni ikinci olarak bölmek ve tamsayı sonucunu ilk değişkene atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="354a1-122">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="354a1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="354a1-123">See also</span></span>

- [<span data-ttu-id="354a1-124">\ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="354a1-124">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="354a1-125">/= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="354a1-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="354a1-126">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="354a1-126">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="354a1-127">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="354a1-127">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="354a1-128">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="354a1-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="354a1-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="354a1-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="354a1-130">Deyimler</span><span class="sxs-lookup"><span data-stu-id="354a1-130">Statements</span></span>](../../programming-guide/language-features/statements.md)

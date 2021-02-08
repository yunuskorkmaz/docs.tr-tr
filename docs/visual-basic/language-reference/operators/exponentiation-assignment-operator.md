---
description: 'Hakkında daha fazla bilgi edinin: ^ = Işleç (Visual Basic)'
title: ^= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 5894fdbedb411c6324a9355bd2d335bb6c6c5867
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773894"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="d8cb6-103">^= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8cb6-103">^= Operator (Visual Basic)</span></span>

<span data-ttu-id="d8cb6-104">Bir değişkenin veya özelliğin değerini bir ifadenin gücüne yükseltir ve sonucu değişkene veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-104">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8cb6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8cb6-105">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d8cb6-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d8cb6-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="d8cb6-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-107">Required.</span></span> <span data-ttu-id="d8cb6-108">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="d8cb6-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-109">Required.</span></span> <span data-ttu-id="d8cb6-110">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8cb6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8cb6-111">Remarks</span></span>  

 <span data-ttu-id="d8cb6-112">İşlecinin sol tarafındaki öğesi `^=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-112">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d8cb6-113">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d8cb6-114">`^=`İşleci ilk olarak, değişkenin veya özelliğin değerini (işlecin sol tarafında) ifadenin değerinin (işlecin sağ tarafında) kuvvetine yükseltir..</span><span class="sxs-lookup"><span data-stu-id="d8cb6-114">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="d8cb6-115">İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-115">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="d8cb6-116">Visual Basic her zaman [Double veri türünde](../data-types/double-data-type.md)üs gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-116">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span> <span data-ttu-id="d8cb6-117">Farklı türdeki işlenenler öğesine dönüştürülür `Double` ve sonuç her zaman olur `Double` .</span><span class="sxs-lookup"><span data-stu-id="d8cb6-117">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="d8cb6-118">Değeri `expression` kesirli, negatif veya her ikisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-118">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d8cb6-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d8cb6-119">Overloading</span></span>  

 <span data-ttu-id="d8cb6-120">[^ İşleci](exponentiation-operator.md) *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-120">The [^ Operator](exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d8cb6-121">İşleci aşırı yüklemek `^` işlecin davranışını etkiler `^=` .</span><span class="sxs-lookup"><span data-stu-id="d8cb6-121">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="d8cb6-122">Kodunuzun `^=` bir sınıf veya yapı üzerinde kullanması durumunda `^` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-122">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d8cb6-123">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d8cb6-123">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8cb6-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8cb6-124">Example</span></span>  

 <span data-ttu-id="d8cb6-125">Aşağıdaki örnek, `^=` bir `Integer` değişkenin değerini ikinci bir değişkenin gücüne yükseltmek ve sonucu ilk değişkene atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-125">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="d8cb6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8cb6-126">See also</span></span>

- [<span data-ttu-id="d8cb6-127">^ İşleci</span><span class="sxs-lookup"><span data-stu-id="d8cb6-127">^ Operator</span></span>](exponentiation-operator.md)
- [<span data-ttu-id="d8cb6-128">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="d8cb6-128">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="d8cb6-129">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="d8cb6-129">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="d8cb6-130">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="d8cb6-130">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="d8cb6-131">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="d8cb6-131">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="d8cb6-132">Deyimler</span><span class="sxs-lookup"><span data-stu-id="d8cb6-132">Statements</span></span>](../../programming-guide/language-features/statements.md)

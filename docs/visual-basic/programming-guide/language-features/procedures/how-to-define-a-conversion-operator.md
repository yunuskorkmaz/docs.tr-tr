---
title: 'Nasıl yapılır: Bir dönüşüm işleci (Visual Basic) tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 76d0769456e30766b830023c1f27381ceca59cbb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521536"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="5a234-102">Nasıl yapılır: Bir dönüşüm işleci (Visual Basic) tanımlama</span><span class="sxs-lookup"><span data-stu-id="5a234-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="5a234-103">Bir sınıf veya yapı tanımladıysanız, bir sınıf veya yapı türü ve başka bir veri türü arasında tür dönüştürme işleci tanımlama (gibi `Integer`, `Double`, veya `String`).</span><span class="sxs-lookup"><span data-stu-id="5a234-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="5a234-104">Tür dönüştürme olarak tanımlayan bir [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) yordam sınıf veya yapı içinde.</span><span class="sxs-lookup"><span data-stu-id="5a234-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="5a234-105">Tüm dönüştürme yordamları olmalıdır `Public Shared`, ve her biri belirtmeli [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) veya [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="5a234-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="5a234-106">Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.</span><span class="sxs-lookup"><span data-stu-id="5a234-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a234-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a234-107">Example</span></span>  
 <span data-ttu-id="5a234-108">Aşağıdaki örnek adlı bir yapıyı arasında dönüştürme işleçleri tanımlar `digit` ve `Byte`.</span><span class="sxs-lookup"><span data-stu-id="5a234-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="5a234-109">Yapıyı test edebilirsiniz `digit` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="5a234-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5a234-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a234-110">See also</span></span>
- [<span data-ttu-id="5a234-111">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="5a234-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="5a234-112">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="5a234-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="5a234-113">Nasıl yapılır: Bir işleç yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="5a234-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="5a234-114">Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="5a234-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="5a234-115">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="5a234-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="5a234-116">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="5a234-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="5a234-117">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="5a234-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="5a234-118">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="5a234-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="5a234-119">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="5a234-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

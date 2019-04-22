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
ms.openlocfilehash: cf7bfdd09c7f3429f9c730a7aec34b24af3f2e9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829232"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="dc8b5-102">Nasıl yapılır: Bir dönüşüm işleci (Visual Basic) tanımlama</span><span class="sxs-lookup"><span data-stu-id="dc8b5-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="dc8b5-103">Bir sınıf veya yapı tanımladıysanız, bir sınıf veya yapı türü ve başka bir veri türü arasında tür dönüştürme işleci tanımlama (gibi `Integer`, `Double`, veya `String`).</span><span class="sxs-lookup"><span data-stu-id="dc8b5-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="dc8b5-104">Tür dönüştürme olarak tanımlayan bir [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) yordam sınıf veya yapı içinde.</span><span class="sxs-lookup"><span data-stu-id="dc8b5-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="dc8b5-105">Tüm dönüştürme yordamları olmalıdır `Public Shared`, ve her biri belirtmeli [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) veya [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="dc8b5-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="dc8b5-106">Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.</span><span class="sxs-lookup"><span data-stu-id="dc8b5-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc8b5-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc8b5-107">Example</span></span>  
 <span data-ttu-id="dc8b5-108">Aşağıdaki örnek adlı bir yapıyı arasında dönüştürme işleçleri tanımlar `digit` ve `Byte`.</span><span class="sxs-lookup"><span data-stu-id="dc8b5-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="dc8b5-109">Yapıyı test edebilirsiniz `digit` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="dc8b5-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="dc8b5-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc8b5-110">See also</span></span>

- [<span data-ttu-id="dc8b5-111">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="dc8b5-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="dc8b5-112">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="dc8b5-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="dc8b5-113">Nasıl yapılır: Bir işleç yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="dc8b5-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="dc8b5-114">Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="dc8b5-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="dc8b5-115">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc8b5-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="dc8b5-116">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc8b5-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="dc8b5-117">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="dc8b5-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="dc8b5-118">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="dc8b5-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="dc8b5-119">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="dc8b5-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

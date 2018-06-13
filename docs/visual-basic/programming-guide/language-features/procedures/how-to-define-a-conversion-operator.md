---
title: 'Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 24bbe41af67f757cae661a78d482a423ff0ffd85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648479"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="9aaac-102">Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aaac-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="9aaac-103">Bir sınıf veya yapı tanımladıysanız, sınıf veya yapı türüne ve başka bir veri türü arasında tür dönüştürme işleci tanımlayabilirsiniz (gibi `Integer`, `Double`, veya `String`).</span><span class="sxs-lookup"><span data-stu-id="9aaac-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="9aaac-104">Tür dönüştürme olarak tanımlayan bir [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) yordam sınıf veya yapı içinde.</span><span class="sxs-lookup"><span data-stu-id="9aaac-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="9aaac-105">Tüm dönüştürme yordamları olmalıdır `Public Shared`, ve her biri ya da belirtmeniz gerekir [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) veya [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="9aaac-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="9aaac-106">Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.</span><span class="sxs-lookup"><span data-stu-id="9aaac-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aaac-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aaac-107">Example</span></span>  
 <span data-ttu-id="9aaac-108">Aşağıdaki örnek olarak adlandırılan bir yapıyı arasında dönüştürme işleçleri tanımlayan `digit` ve `Byte`.</span><span class="sxs-lookup"><span data-stu-id="9aaac-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="9aaac-109">Yapıyı test `digit` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="9aaac-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9aaac-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9aaac-110">See Also</span></span>  
 [<span data-ttu-id="9aaac-111">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="9aaac-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="9aaac-112">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="9aaac-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="9aaac-113">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="9aaac-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="9aaac-114">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="9aaac-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="9aaac-115">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="9aaac-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="9aaac-116">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="9aaac-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="9aaac-117">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="9aaac-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="9aaac-118">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="9aaac-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="9aaac-119">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="9aaac-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

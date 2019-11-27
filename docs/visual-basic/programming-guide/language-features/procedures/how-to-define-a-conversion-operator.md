---
title: 'Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 0ff95390206947e5a28f7a5b85547b496746a9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344893"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="350af-102">Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="350af-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="350af-103">Bir sınıf veya yapı tanımladıysanız, sınıfınızın veya yapınızın türü ile başka bir veri türü (`Integer`, `Double`veya `String`gibi) arasında bir tür dönüştürme işleci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="350af-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="350af-104">Tür dönüşümünü sınıf veya yapı içinde [CType işlev](../../../../visual-basic/language-reference/functions/ctype-function.md) yordamı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="350af-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="350af-105">Tüm dönüştürme yordamları `Public Shared`olmalıdır ve her birinin [genişletme](../../../../visual-basic/language-reference/modifiers/widening.md) veya [daraltma](../../../../visual-basic/language-reference/modifiers/narrowing.md)belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="350af-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="350af-106">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="350af-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="350af-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="350af-107">Example</span></span>  
 <span data-ttu-id="350af-108">Aşağıdaki örnek, `digit` ve `Byte`adlı bir yapı arasındaki dönüştürme işleçlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="350af-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="350af-109">Aşağıdaki kodla yapıyı `digit` test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="350af-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="350af-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="350af-110">See also</span></span>

- [<span data-ttu-id="350af-111">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="350af-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="350af-112">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="350af-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="350af-113">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="350af-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="350af-114">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="350af-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="350af-115">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="350af-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="350af-116">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="350af-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="350af-117">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="350af-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="350af-118">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="350af-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="350af-119">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="350af-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

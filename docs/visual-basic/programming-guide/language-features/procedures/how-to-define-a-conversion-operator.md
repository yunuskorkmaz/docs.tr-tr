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
ms.openlocfilehash: 2fabcf6c6ceb38fe77d4eed4f02dcb5a5e447bf1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085678"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="e2e80-102">Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2e80-102">How to: Define a Conversion Operator (Visual Basic)</span></span>

<span data-ttu-id="e2e80-103">Bir sınıf veya yapı tanımladıysanız, sınıfınızın veya yapınızın türü ile başka bir veri türü (, veya gibi) arasında bir tür dönüştürme işleci tanımlayabilirsiniz `Integer` `Double` `String` .</span><span class="sxs-lookup"><span data-stu-id="e2e80-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="e2e80-104">Tür dönüşümünü sınıf veya yapı içinde [CType işlev](../../../language-reference/functions/ctype-function.md) yordamı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e2e80-104">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="e2e80-105">Tüm dönüştürme yordamları olmalıdır `Public Shared` ve her birinin [genişletme](../../../language-reference/modifiers/widening.md) veya [daraltma](../../../language-reference/modifiers/narrowing.md)belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2e80-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="e2e80-106">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e2e80-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2e80-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2e80-107">Example</span></span>  

 <span data-ttu-id="e2e80-108">Aşağıdaki örnek, ve adlı bir yapı arasındaki dönüştürme işleçlerini tanımlar `digit` `Byte` .</span><span class="sxs-lookup"><span data-stu-id="e2e80-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="e2e80-109">Yapıyı aşağıdaki kodla test edebilirsiniz `digit` .</span><span class="sxs-lookup"><span data-stu-id="e2e80-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="e2e80-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e80-110">See also</span></span>

- [<span data-ttu-id="e2e80-111">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="e2e80-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e2e80-112">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="e2e80-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="e2e80-113">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="e2e80-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="e2e80-114">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="e2e80-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="e2e80-115">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="e2e80-115">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="e2e80-116">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="e2e80-116">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="e2e80-117">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="e2e80-117">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="e2e80-118">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="e2e80-118">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="e2e80-119">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="e2e80-119">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)

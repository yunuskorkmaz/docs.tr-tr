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
ms.openlocfilehash: 53b0211c6304625edd7ac24fa52ff0c051d8f0a0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388095"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="2e29f-102">Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e29f-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="2e29f-103">Bir sınıf veya yapı tanımladıysanız, sınıfınızın veya yapınızın türü ile başka bir veri türü (, veya gibi) arasında bir tür dönüştürme işleci tanımlayabilirsiniz `Integer` `Double` `String` .</span><span class="sxs-lookup"><span data-stu-id="2e29f-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="2e29f-104">Tür dönüşümünü sınıf veya yapı içinde [CType işlev](../../../language-reference/functions/ctype-function.md) yordamı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2e29f-104">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="2e29f-105">Tüm dönüştürme yordamları olmalıdır `Public Shared` ve her birinin [genişletme](../../../language-reference/modifiers/widening.md) veya [daraltma](../../../language-reference/modifiers/narrowing.md)belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e29f-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="2e29f-106">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2e29f-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e29f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e29f-107">Example</span></span>  
 <span data-ttu-id="2e29f-108">Aşağıdaki örnek, ve adlı bir yapı arasındaki dönüştürme işleçlerini tanımlar `digit` `Byte` .</span><span class="sxs-lookup"><span data-stu-id="2e29f-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="2e29f-109">Yapıyı aşağıdaki kodla test edebilirsiniz `digit` .</span><span class="sxs-lookup"><span data-stu-id="2e29f-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="2e29f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e29f-110">See also</span></span>

- [<span data-ttu-id="2e29f-111">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="2e29f-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="2e29f-112">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="2e29f-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="2e29f-113">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="2e29f-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="2e29f-114">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="2e29f-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="2e29f-115">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="2e29f-115">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="2e29f-116">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="2e29f-116">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="2e29f-117">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="2e29f-117">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="2e29f-118">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="2e29f-118">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="2e29f-119">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="2e29f-119">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)

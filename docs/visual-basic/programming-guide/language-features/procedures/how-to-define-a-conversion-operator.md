---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: dönüştürme Işleci tanımlama (Visual Basic)'
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
ms.openlocfilehash: c090e183e809974163625c4bfcf33536b1082b66
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481993"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="c8dbc-103">Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8dbc-103">How to: Define a Conversion Operator (Visual Basic)</span></span>

<span data-ttu-id="c8dbc-104">Bir sınıf veya yapı tanımladıysanız, sınıfınızın veya yapınızın türü ile başka bir veri türü (, veya gibi) arasında bir tür dönüştürme işleci tanımlayabilirsiniz `Integer` `Double` `String` .</span><span class="sxs-lookup"><span data-stu-id="c8dbc-104">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="c8dbc-105">Tür dönüşümünü sınıf veya yapı içinde [CType işlev](../../../language-reference/functions/ctype-function.md) yordamı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-105">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="c8dbc-106">Tüm dönüştürme yordamları olmalıdır `Public Shared` ve her birinin [genişletme](../../../language-reference/modifiers/widening.md) veya [daraltma](../../../language-reference/modifiers/narrowing.md)belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-106">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="c8dbc-107">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-107">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8dbc-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8dbc-108">Example</span></span>  

 <span data-ttu-id="c8dbc-109">Aşağıdaki örnek, ve adlı bir yapı arasındaki dönüştürme işleçlerini tanımlar `digit` `Byte` .</span><span class="sxs-lookup"><span data-stu-id="c8dbc-109">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="c8dbc-110">Yapıyı aşağıdaki kodla test edebilirsiniz `digit` .</span><span class="sxs-lookup"><span data-stu-id="c8dbc-110">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="c8dbc-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8dbc-111">See also</span></span>

- [<span data-ttu-id="c8dbc-112">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="c8dbc-112">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="c8dbc-113">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="c8dbc-113">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="c8dbc-114">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="c8dbc-114">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="c8dbc-115">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8dbc-115">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="c8dbc-116">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8dbc-116">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="c8dbc-117">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="c8dbc-117">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="c8dbc-118">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="c8dbc-118">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="c8dbc-119">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c8dbc-119">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c8dbc-120">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="c8dbc-120">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)

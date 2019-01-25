---
title: 'Nasıl yapılır: (Visual Basic) bir işleci tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: fb150298562c1ec91f73f3c8075f4f8a4fc20b27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679532"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="1b9e3-102">Nasıl yapılır: (Visual Basic) bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="1b9e3-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="1b9e3-103">Bir sınıf veya yapı tanımladıysanız, standart bir işleç davranışını tanımlayın (gibi `*`, `<>`, veya `And`) bir veya iki işlenenden olduğunda sınıf veya yapı türü.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="1b9e3-104">Standart işleci, sınıf veya yapı içinde bir işleç yordamı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="1b9e3-105">İşleç yordamları tüm olmalıdır `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="1b9e3-106">Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b9e3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b9e3-107">Example</span></span>  
 <span data-ttu-id="1b9e3-108">Aşağıdaki örnek tanımlar `+` işleci bir yapı için adlı `height`.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="1b9e3-109">Yapı ayak ve inç cinsinden yüksekliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="1b9e3-110">Bir *inç* 2,54 santimetre ve bir *altbilgi* 12 inçtir.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="1b9e3-111">Normalleştirilmiş değerleri (inç < 12.0) sağlamak için oluşturucu gerçekleştirir *modül* aritmetik 12.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="1b9e3-112">`+` İşleci normalleştirilmiş değerler oluşturmak için oluşturucu kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="1b9e3-113">Yapıyı test edebilirsiniz `height` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="1b9e3-114">Daha fazla bilgi ve örnekler için bkz. [işleci aşırı yüklemesi Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="1b9e3-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9e3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b9e3-115">See also</span></span>
- [<span data-ttu-id="1b9e3-116">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="1b9e3-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="1b9e3-117">Nasıl yapılır: Bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="1b9e3-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="1b9e3-118">Nasıl yapılır: Bir işleç yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="1b9e3-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="1b9e3-119">Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="1b9e3-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="1b9e3-120">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="1b9e3-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="1b9e3-121">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="1b9e3-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="1b9e3-122">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="1b9e3-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="1b9e3-123">Mod İşleci</span><span class="sxs-lookup"><span data-stu-id="1b9e3-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)

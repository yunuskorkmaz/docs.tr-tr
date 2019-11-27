---
title: 'Nasıl yapılır: Bir İşleci Tanımlama'
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
ms.openlocfilehash: b99af8ff4d5428f1749bfc1a4c51a136f12405ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344871"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="01514-102">Nasıl yapılır: Bir İşleci Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01514-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="01514-103">Bir sınıf veya yapı tanımladıysanız, işlenenleri bir veya her ikisi de sınıfınızın veya yapınızın türü olduğunda standart bir işlecin (`*`, `<>`veya `And`) davranışını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01514-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="01514-104">Standart işleci sınıf veya yapı içinde operatör yordamı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="01514-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="01514-105">Tüm operatör yordamları `Public` `Shared`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="01514-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="01514-106">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="01514-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01514-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="01514-107">Example</span></span>  
 <span data-ttu-id="01514-108">Aşağıdaki örnek, `height`adlı bir yapı için `+` işlecini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01514-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="01514-109">Yapı, fit ve inç cinsinden ölçülen yükseklikleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="01514-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="01514-110">Bir *inç* 2,54 santimetre, bir *Foot* ise 12 inç 'tir.</span><span class="sxs-lookup"><span data-stu-id="01514-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="01514-111">Normalleştirilmiş değerler (inç < 12,0) sağlamak için, Oluşturucu *Modül* 12 aritmetik işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="01514-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="01514-112">`+` işleci, normalleştirilmiş değerler oluşturmak için oluşturucuyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="01514-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="01514-113">Aşağıdaki kodla yapıyı `height` test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01514-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="01514-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01514-114">See also</span></span>

- [<span data-ttu-id="01514-115">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="01514-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="01514-116">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="01514-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="01514-117">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="01514-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="01514-118">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="01514-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="01514-119">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="01514-119">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="01514-120">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="01514-120">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="01514-121">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="01514-121">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="01514-122">Mod İşleci</span><span class="sxs-lookup"><span data-stu-id="01514-122">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)

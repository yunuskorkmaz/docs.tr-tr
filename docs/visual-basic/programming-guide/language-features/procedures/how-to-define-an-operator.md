---
title: 'Nasıl yapılır: Bir İşleci Tanımlama (Visual Basic)'
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
ms.openlocfilehash: 1f5a020a710cecdfd8722a9fca0a8b329697eced
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805405"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="2e411-102">Nasıl yapılır: Bir İşleci Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e411-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="2e411-103">Bir sınıf veya yapı tanımladıysanız, standart bir işleç davranışını tanımlayabilirsiniz (gibi `*`, `<>`, veya `And`) birine veya ikisine de işlenenler olduğunda sınıf veya yapı türünü.</span><span class="sxs-lookup"><span data-stu-id="2e411-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="2e411-104">Sınıf veya yapı içinde bir işleç yordamı olarak standart işleci tanımlama.</span><span class="sxs-lookup"><span data-stu-id="2e411-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="2e411-105">Tüm işleç yordamları olmalıdır `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="2e411-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="2e411-106">Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.</span><span class="sxs-lookup"><span data-stu-id="2e411-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e411-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e411-107">Example</span></span>  
 <span data-ttu-id="2e411-108">Aşağıdaki örnek tanımlar `+` işleci bir yapı için adlı `height`.</span><span class="sxs-lookup"><span data-stu-id="2e411-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="2e411-109">Yükseklik fit ve inç ölçülen yapısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e411-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="2e411-110">Bir *inç* 2,54 santimetreden ve bir *altbilgi* 12 inç'tir.</span><span class="sxs-lookup"><span data-stu-id="2e411-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="2e411-111">Normalleştirilmiş değerleri (inç < 12.0) sağlamak için Oluşturucusu yapar *modulo* 12 aritmetik.</span><span class="sxs-lookup"><span data-stu-id="2e411-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="2e411-112">`+` İşleci Oluşturucusu normalleştirilmiş değerlerini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e411-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="2e411-113">Yapıyı test `height` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="2e411-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="2e411-114">Daha fazla bilgi ve örnekler için bkz: [İşleç aşırı yüklemesi Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="2e411-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e411-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e411-115">See Also</span></span>  
 [<span data-ttu-id="2e411-116">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="2e411-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="2e411-117">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="2e411-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="2e411-118">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="2e411-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="2e411-119">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="2e411-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="2e411-120">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="2e411-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="2e411-121">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="2e411-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="2e411-122">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="2e411-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="2e411-123">Mod İşleci</span><span class="sxs-lookup"><span data-stu-id="2e411-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)

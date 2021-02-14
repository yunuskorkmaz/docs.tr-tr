---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Işleç tanımlama (Visual Basic)'
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
ms.openlocfilehash: ead96a302426c6f5b1667bb030aab56afe3284c8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462717"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="ae4c2-103">Nasıl yapılır: Bir İşleci Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae4c2-103">How to: Define an Operator (Visual Basic)</span></span>

<span data-ttu-id="ae4c2-104">Bir sınıf veya yapı tanımladıysanız, `*` `<>` işlenenleri bir `And` veya her ikisi de sınıfınızın veya yapınızın türü olduğunda standart işlecin (örneğin,, veya) davranışını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-104">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="ae4c2-105">Standart işleci sınıf veya yapı içinde operatör yordamı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-105">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="ae4c2-106">Tüm operatör yordamları olmalıdır `Public` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="ae4c2-106">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="ae4c2-107">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-107">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae4c2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae4c2-108">Example</span></span>  

 <span data-ttu-id="ae4c2-109">Aşağıdaki örnek, `+` adlı bir yapının işlecini tanımlar `height` .</span><span class="sxs-lookup"><span data-stu-id="ae4c2-109">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="ae4c2-110">Yapı, fit ve inç cinsinden ölçülen yükseklikleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-110">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="ae4c2-111">Bir *inç* 2,54 santimetre, bir *Foot* ise 12 inç 'tir.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-111">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="ae4c2-112">Normalleştirilmiş değerler (inç < 12,0) sağlamak için, Oluşturucu *Modül* 12 aritmetik işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-112">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="ae4c2-113">`+`İşleci, Normalleştirilmemiş değerler oluşturmak için oluşturucuyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-113">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="ae4c2-114">Yapıyı aşağıdaki kodla test edebilirsiniz `height` .</span><span class="sxs-lookup"><span data-stu-id="ae4c2-114">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="ae4c2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae4c2-115">See also</span></span>

- [<span data-ttu-id="ae4c2-116">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="ae4c2-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="ae4c2-117">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="ae4c2-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="ae4c2-118">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="ae4c2-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="ae4c2-119">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="ae4c2-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="ae4c2-120">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="ae4c2-120">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="ae4c2-121">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="ae4c2-121">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="ae4c2-122">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="ae4c2-122">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="ae4c2-123">Mod İşleci</span><span class="sxs-lookup"><span data-stu-id="ae4c2-123">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)

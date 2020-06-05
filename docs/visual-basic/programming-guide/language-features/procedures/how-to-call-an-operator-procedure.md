---
title: 'Nasıl yapılır: Bir İşleç Yordamı Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: fa2bc5417b8b917ff48502a5bd0a4daa21fab67e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388575"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="280b4-102">Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="280b4-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="280b4-103">Bir ifadede işleç sembolünü kullanarak bir işleç yordamı çağırın.</span><span class="sxs-lookup"><span data-stu-id="280b4-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="280b4-104">Bir dönüştürme işleci söz konusu olduğunda, bir değeri bir veri türünden diğerine dönüştürmek için [CType işlevini](../../../language-reference/functions/ctype-function.md) çağırın.</span><span class="sxs-lookup"><span data-stu-id="280b4-104">In the case of a conversion operator, you call the [CType Function](../../../language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="280b4-105">Operatör yordamlarını açıkça çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="280b4-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="280b4-106">Yalnızca işlecini veya bir deyimi, bir `CType` atama deyiminde veya bir ifadede, normalde bir işleci kullandığınız şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="280b4-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="280b4-107">Visual Basic işleç yordamına çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="280b4-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="280b4-108">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="280b4-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="280b4-109">Bir işleç yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="280b4-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="280b4-110">Bir ifadede işleç sembolünü normal şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="280b4-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="280b4-111">İşlenenlerin veri türlerinin operatör için uygun olduğundan ve doğru sırada olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="280b4-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="280b4-112">İşleci, ifadenin değerine beklenen şekilde katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="280b4-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="280b4-113">Bir dönüştürme işleci yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="280b4-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="280b4-114">`CType`Bir ifadenin içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="280b4-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="280b4-115">İşlenenlerin veri türlerinin dönüştürme için uygun olduğundan ve doğru sırada olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="280b4-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="280b4-116">`CType`dönüştürme işleci yordamını çağırır ve dönüştürülen değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="280b4-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="280b4-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="280b4-117">Example</span></span>  
 <span data-ttu-id="280b4-118">Aşağıdaki örnek iki yapı oluşturur <xref:System.TimeSpan> , bunları birlikte ekler ve sonucu üçüncü bir <xref:System.TimeSpan> yapıda depolar.</span><span class="sxs-lookup"><span data-stu-id="280b4-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="280b4-119"><xref:System.TimeSpan>Yapı, birkaç standart işlecin aşırı yüklenmesine yönelik operatör yordamlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="280b4-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="280b4-120"><xref:System.TimeSpan>Standart `+` işleci aşırı yüklediğinden, önceki örnek değerini hesaplarken bir işleç yordamını çağırır `combinedSpan` .</span><span class="sxs-lookup"><span data-stu-id="280b4-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="280b4-121">Bir konuşma işleci yordamı çağırma örneği için bkz. [nasıl yapılır: Işleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="280b4-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="280b4-122">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="280b4-122">Compile the code</span></span>  
 <span data-ttu-id="280b4-123">Kullandığınız sınıf veya yapının kullanmak istediğiniz işleci tanımladığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="280b4-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="280b4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="280b4-124">See also</span></span>

- [<span data-ttu-id="280b4-125">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="280b4-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="280b4-126">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="280b4-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="280b4-127">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="280b4-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="280b4-128">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="280b4-128">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="280b4-129">Genişletme</span><span class="sxs-lookup"><span data-stu-id="280b4-129">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="280b4-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="280b4-130">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="280b4-131">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="280b4-131">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="280b4-132">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="280b4-132">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="280b4-133">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="280b4-133">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="280b4-134">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="280b4-134">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)

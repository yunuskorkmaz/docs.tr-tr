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
ms.openlocfilehash: a977b17d4b2c797bbe38d289a57f3d9d31fa64fa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345961"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="d1570-102">Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1570-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="d1570-103">Bir ifadede işleç sembolünü kullanarak bir işleç yordamı çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1570-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="d1570-104">Bir dönüştürme işleci söz konusu olduğunda, bir değeri bir veri türünden diğerine dönüştürmek için [CType işlevini](../../../../visual-basic/language-reference/functions/ctype-function.md) çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1570-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="d1570-105">Operatör yordamlarını açıkça çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="d1570-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="d1570-106">Yalnızca işlecini veya `CType` işlevini, bir atama deyiminde veya bir ifadede, normalde bir işleci kullandığınız şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d1570-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="d1570-107">Visual Basic işleç yordamına çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="d1570-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="d1570-108">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d1570-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="d1570-109">Bir işleç yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="d1570-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="d1570-110">Bir ifadede işleç sembolünü normal şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1570-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="d1570-111">İşlenenlerin veri türlerinin operatör için uygun olduğundan ve doğru sırada olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d1570-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="d1570-112">İşleci, ifadenin değerine beklenen şekilde katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d1570-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="d1570-113">Bir dönüştürme işleci yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="d1570-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="d1570-114">`CType` bir ifadenin içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1570-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="d1570-115">İşlenenlerin veri türlerinin dönüştürme için uygun olduğundan ve doğru sırada olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d1570-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="d1570-116">`CType` dönüştürme işleci yordamını çağırır ve dönüştürülen değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1570-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1570-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1570-117">Example</span></span>  
 <span data-ttu-id="d1570-118">Aşağıdaki örnek iki <xref:System.TimeSpan> yapısı oluşturur, bunları birlikte ekler ve sonucu üçüncü bir <xref:System.TimeSpan> yapısında depolar.</span><span class="sxs-lookup"><span data-stu-id="d1570-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="d1570-119"><xref:System.TimeSpan> yapısı, birkaç standart işlecin aşırı yüklenmesine yönelik operatör yordamlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d1570-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="d1570-120"><xref:System.TimeSpan> standart `+` işlecini aşırı yüklediğinden, önceki örnek `combinedSpan`değerini hesaplarken bir işleç yordamını çağırır.</span><span class="sxs-lookup"><span data-stu-id="d1570-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="d1570-121">Bir konuşma işleci yordamı çağırma örneği için bkz. [nasıl yapılır: Işleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d1570-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="d1570-122">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="d1570-122">Compile the code</span></span>  
 <span data-ttu-id="d1570-123">Kullandığınız sınıf veya yapının kullanmak istediğiniz işleci tanımladığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d1570-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1570-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1570-124">See also</span></span>

- [<span data-ttu-id="d1570-125">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="d1570-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d1570-126">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d1570-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="d1570-127">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d1570-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="d1570-128">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="d1570-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="d1570-129">Widening</span><span class="sxs-lookup"><span data-stu-id="d1570-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="d1570-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="d1570-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="d1570-131">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="d1570-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="d1570-132">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="d1570-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="d1570-133">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="d1570-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="d1570-134">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d1570-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

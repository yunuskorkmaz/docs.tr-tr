---
title: 'Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)'
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
ms.openlocfilehash: b1dc4477daa4ceb9dfc6a9a6ab3f041e68011acd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649974"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="733d7-102">Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="733d7-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="733d7-103">Bir ifadeyi işleç simgesi kullanarak bir işleç yordamı çağırma.</span><span class="sxs-lookup"><span data-stu-id="733d7-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="733d7-104">Bir dönüşüm işleci söz konusu olduğunda, çağrı [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) bir değer bir veri türünden dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="733d7-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="733d7-105">İşleç yordamları açıkça çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="733d7-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="733d7-106">Yalnızca işlecini kullanın veya `CType` bir atama ifadesi veya bir ifade, bir işleç normalde kullandığınız gibi işlev.</span><span class="sxs-lookup"><span data-stu-id="733d7-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="733d7-107">Visual Basic işleç yordamı çağrıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="733d7-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="733d7-108">Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.</span><span class="sxs-lookup"><span data-stu-id="733d7-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="733d7-109">Bir işleç yordamı çağırma için</span><span class="sxs-lookup"><span data-stu-id="733d7-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="733d7-110">İşleç simgesi bir ifadede normal şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="733d7-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="733d7-111">İşlenen veri türlerini operatöre ve doğru sırada uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="733d7-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="733d7-112">İşleci, beklendiği gibi ifadenin değerini katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="733d7-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="733d7-113">Bir dönüştürme işleç yordamı çağırma için</span><span class="sxs-lookup"><span data-stu-id="733d7-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="733d7-114">Kullanım `CType` içinde bir ifade.</span><span class="sxs-lookup"><span data-stu-id="733d7-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="733d7-115">İşlenen veri türlerini dönüştürme işlemi için ve doğru sırada uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="733d7-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="733d7-116">`CType` dönüştürme işleci yordam çağrıları ve dönüştürülen değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="733d7-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="733d7-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="733d7-117">Example</span></span>  
 <span data-ttu-id="733d7-118">Aşağıdaki örnekte iki oluşturur <xref:System.TimeSpan> yapıları, bunları bir araya getirir ve üçüncü bir sonucu depolar <xref:System.TimeSpan> yapısı.</span><span class="sxs-lookup"><span data-stu-id="733d7-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="733d7-119"><xref:System.TimeSpan> Yapısı birkaç standart işleci aşırı yüklemeyi işleç yordamları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="733d7-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 <span data-ttu-id="733d7-120">Çünkü <xref:System.TimeSpan> standart overloads `+` işleci, önceki örnekte çağıran bir işleç yordamı değeri hesaplarken `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="733d7-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="733d7-121">Konuşma işleç yordamı çağırma örneği için bkz: [nasıl yapılır: bir sınıf tanımlar, işleçler kullanma](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="733d7-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="733d7-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="733d7-122">Compiling the Code</span></span>  
 <span data-ttu-id="733d7-123">Sınıf veya yapı kullanmakta olduğunuz kullanmak istediğiniz işleci tanımlar emin olun.</span><span class="sxs-lookup"><span data-stu-id="733d7-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733d7-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="733d7-124">See Also</span></span>  
 [<span data-ttu-id="733d7-125">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="733d7-125">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="733d7-126">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="733d7-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="733d7-127">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="733d7-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="733d7-128">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="733d7-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="733d7-129">Widening</span><span class="sxs-lookup"><span data-stu-id="733d7-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="733d7-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="733d7-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="733d7-131">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="733d7-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="733d7-132">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="733d7-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="733d7-133">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="733d7-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="733d7-134">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="733d7-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

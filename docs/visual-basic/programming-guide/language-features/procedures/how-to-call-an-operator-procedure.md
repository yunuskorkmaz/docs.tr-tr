---
title: 'Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21545f2488bfabd0abc9c6e316d21bbc4d5aeb91
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="b3840-102">Nasıl yapılır: Bir İşleç Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3840-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="b3840-103">Bir ifadeyi işleç simgesi kullanarak bir işleç yordamı çağırma.</span><span class="sxs-lookup"><span data-stu-id="b3840-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="b3840-104">Bir dönüşüm işleci söz konusu olduğunda, çağrı [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) bir değer bir veri türünden dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="b3840-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="b3840-105">İşleç yordamları açıkça çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="b3840-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="b3840-106">Yalnızca işlecini kullanın veya `CType` bir atama ifadesi veya bir ifade, bir işleç normalde kullandığınız gibi işlev.</span><span class="sxs-lookup"><span data-stu-id="b3840-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="b3840-107">Visual Basic işleç yordamı çağrıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b3840-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="b3840-108">Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.</span><span class="sxs-lookup"><span data-stu-id="b3840-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="b3840-109">Bir işleç yordamı çağırma için</span><span class="sxs-lookup"><span data-stu-id="b3840-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="b3840-110">İşleç simgesi bir ifadede normal şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3840-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="b3840-111">İşlenen veri türlerini operatöre ve doğru sırada uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3840-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="b3840-112">İşleci, beklendiği gibi ifadenin değerini katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b3840-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="b3840-113">Bir dönüştürme işleç yordamı çağırma için</span><span class="sxs-lookup"><span data-stu-id="b3840-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="b3840-114">Kullanım `CType` içinde bir ifade.</span><span class="sxs-lookup"><span data-stu-id="b3840-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="b3840-115">İşlenen veri türlerini dönüştürme işlemi için ve doğru sırada uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3840-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="b3840-116">`CType` dönüştürme işleci yordam çağrıları ve dönüştürülen değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b3840-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3840-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3840-117">Example</span></span>  
 <span data-ttu-id="b3840-118">Aşağıdaki örnekte iki oluşturur <xref:System.TimeSpan> yapıları, bunları bir araya getirir ve üçüncü bir sonucu depolar <xref:System.TimeSpan> yapısı.</span><span class="sxs-lookup"><span data-stu-id="b3840-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="b3840-119"><xref:System.TimeSpan> Yapısı birkaç standart işleci aşırı yüklemeyi işleç yordamları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b3840-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 <span data-ttu-id="b3840-120">Çünkü <xref:System.TimeSpan> standart overloads `+` işleci, önceki örnekte çağıran bir işleç yordamı değeri hesaplarken `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="b3840-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="b3840-121">Konuşma işleç yordamı çağırma örneği için bkz: [nasıl yapılır: bir sınıf tanımlar, işleçler kullanma](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="b3840-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3840-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b3840-122">Compiling the Code</span></span>  
 <span data-ttu-id="b3840-123">Sınıf veya yapı kullanmakta olduğunuz kullanmak istediğiniz işleci tanımlar emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3840-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3840-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3840-124">See Also</span></span>  
 [<span data-ttu-id="b3840-125">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="b3840-125">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="b3840-126">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="b3840-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="b3840-127">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="b3840-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="b3840-128">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="b3840-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="b3840-129">Widening</span><span class="sxs-lookup"><span data-stu-id="b3840-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="b3840-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="b3840-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="b3840-131">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="b3840-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="b3840-132">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="b3840-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="b3840-133">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b3840-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="b3840-134">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="b3840-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

---
title: 'Nasıl yapılır: (Visual Basic) bir işleç yordamı çağırma'
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
ms.openlocfilehash: d68781aa12ab7c1c717031ca252c5f3120649edc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335491"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="6fd60-102">Nasıl yapılır: (Visual Basic) bir işleç yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="6fd60-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="6fd60-103">Bir ifadede operatör sembolünü kullanarak, bir işleç yordamı çağırma.</span><span class="sxs-lookup"><span data-stu-id="6fd60-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="6fd60-104">Bir dönüştürme operatörünün söz konusu olduğunda, çağrı [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) bir değeri bir veri türünden dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="6fd60-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="6fd60-105">İşleç yordamları açıkça çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="6fd60-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="6fd60-106">İşleci, yalnızca kullandığınız ya da `CType` işlevi, atama deyiminin veya bir ifade, operatörün normalde kullandığınız gibi.</span><span class="sxs-lookup"><span data-stu-id="6fd60-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="6fd60-107">Visual Basic işleç yordamı çağrıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="6fd60-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="6fd60-108">Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.</span><span class="sxs-lookup"><span data-stu-id="6fd60-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="6fd60-109">Bir işleç yordamı çağırma için</span><span class="sxs-lookup"><span data-stu-id="6fd60-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="6fd60-110">İşlecin bir ifadede normal şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fd60-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="6fd60-111">İşlenen veri türlerini işleci için ve doğru sırada uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6fd60-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="6fd60-112">İşleci, beklenen şekilde ifadesinin değerine katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="6fd60-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="6fd60-113">Bir dönüştürme işleci yordam çağırmak için</span><span class="sxs-lookup"><span data-stu-id="6fd60-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="6fd60-114">Kullanım `CType` içinde bir ifade.</span><span class="sxs-lookup"><span data-stu-id="6fd60-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="6fd60-115">İşlenen veri türlerini dönüştürme ve doğru sırada uygun olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6fd60-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. `CType` <span data-ttu-id="6fd60-116">dönüştürme işleci yordam çağrıları ve dönüştürülen değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6fd60-116">calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fd60-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="6fd60-117">Example</span></span>  
 <span data-ttu-id="6fd60-118">Aşağıdaki örnek iki oluşturur <xref:System.TimeSpan> yapıları, bunları bir araya getirir ve sonucu bir üçüncü depolar <xref:System.TimeSpan> yapısı.</span><span class="sxs-lookup"><span data-stu-id="6fd60-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="6fd60-119"><xref:System.TimeSpan> Birkaç standart İşleç aşırı yüklemeyi işleç yordamları yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6fd60-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="6fd60-120">Çünkü <xref:System.TimeSpan> Standart aşırı `+` işleci, önceki örnekte çağıran bir işleç yordamı değerini hesaplarken `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="6fd60-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="6fd60-121">Konuşma bir işleç yordamı çağırma örneği için bkz: [nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="6fd60-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6fd60-122">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6fd60-122">Compiling the Code</span></span>  
 <span data-ttu-id="6fd60-123">Kullanmak istediğiniz işleci tanımlar, sınıfın veya yapının kullanmakta olduğunuz emin olun.</span><span class="sxs-lookup"><span data-stu-id="6fd60-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd60-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fd60-124">See also</span></span>

- [<span data-ttu-id="6fd60-125">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="6fd60-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="6fd60-126">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="6fd60-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="6fd60-127">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="6fd60-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="6fd60-128">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fd60-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="6fd60-129">Genişletme</span><span class="sxs-lookup"><span data-stu-id="6fd60-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="6fd60-130">Daraltma</span><span class="sxs-lookup"><span data-stu-id="6fd60-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="6fd60-131">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="6fd60-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="6fd60-132">Nasıl yapılır: Bir yapıyı bildirme</span><span class="sxs-lookup"><span data-stu-id="6fd60-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="6fd60-133">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="6fd60-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="6fd60-134">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="6fd60-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

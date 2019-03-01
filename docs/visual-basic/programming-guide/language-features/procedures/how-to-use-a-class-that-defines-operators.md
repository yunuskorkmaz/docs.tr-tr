---
title: 'Nasıl yapılır: İşleçler (Visual Basic) tanımlayan bir sınıf kullanma'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 358e81904f48ad844351a20a448b615a0fef8f89
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972527"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="f17ba-102">Nasıl yapılır: İşleçler (Visual Basic) tanımlayan bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="f17ba-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="f17ba-103">Bir sınıf veya kendi işleçleri tanımlayan bir yapı kullanıyorsanız, bu işleçler Visual Basic'ten erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f17ba-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="f17ba-104">Bir sınıf ya da yapı üzerinde operatör tanımlama olarak da adlandırılır *aşırı yükleme* işleci.</span><span class="sxs-lookup"><span data-stu-id="f17ba-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f17ba-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f17ba-105">Example</span></span>  
 <span data-ttu-id="f17ba-106">Aşağıdaki örnek SQL yapısı erişen <xref:System.Data.SqlTypes.SqlString>, dönüştürme işleçlerini tanımlar ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) SQL dizesi ve bir Visual Basic dize arasında iki yönlü.</span><span class="sxs-lookup"><span data-stu-id="f17ba-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="f17ba-107">Kullanım `CType(` *SQL dize ifadesi*, `String)` SQL dizesi bir Visual Basic dizeye dönüştürmek için ve `CType(` *Visual Basic dize ifadesinin*, <xref:System.Data.SqlTypes.SqlString> `)` diğer yönde dönüştürülecek.</span><span class="sxs-lookup"><span data-stu-id="f17ba-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="f17ba-108"><xref:System.Data.SqlTypes.SqlString> Yapısını tanımlayan bir dönüştürme operatörünün ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) öğesinden `String` için <xref:System.Data.SqlTypes.SqlString> ve başka bir uygulamadan <xref:System.Data.SqlTypes.SqlString> için `String`.</span><span class="sxs-lookup"><span data-stu-id="f17ba-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="f17ba-109">Atayan deyimi `title` için `jobTitle` ilk işlecini kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> ikinci işlev çağrısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f17ba-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f17ba-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f17ba-110">Compiling the Code</span></span>  
 <span data-ttu-id="f17ba-111">Kullanmak istediğiniz işleci tanımlar, sınıfın veya yapının kullanmakta olduğunuz emin olun.</span><span class="sxs-lookup"><span data-stu-id="f17ba-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="f17ba-112">Sınıfın veya yapının her işleci aşırı yükleme için kullanılabilir tanımladığı varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="f17ba-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="f17ba-113">Kullanılabilir işleçlerin bir listesi için bkz. [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f17ba-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="f17ba-114">Uygun dahil `Imports` kaynak dosyasının başında SQL dizesi deyimi (Bu durumda <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="f17ba-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="f17ba-115">Proje başvuruları System.Data ve System.XML olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f17ba-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17ba-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f17ba-116">See also</span></span>
- [<span data-ttu-id="f17ba-117">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="f17ba-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f17ba-118">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="f17ba-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="f17ba-119">Nasıl yapılır: Bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="f17ba-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="f17ba-120">Nasıl yapılır: Bir işleç yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="f17ba-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="f17ba-121">Widening</span><span class="sxs-lookup"><span data-stu-id="f17ba-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="f17ba-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="f17ba-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="f17ba-123">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="f17ba-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="f17ba-124">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="f17ba-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="f17ba-125">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="f17ba-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="f17ba-126">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="f17ba-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

---
title: "Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 223b3fc84fe75d1d530cd182c9332e5c663aa519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="27d01-102">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27d01-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="27d01-103">Bir sınıf veya kendi işleçleri tanımlayan yapı kullanıyorsanız, bu işleçler öğesinden erişebilirsiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27d01-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="27d01-104">Bir sınıf veya yapı bir işleci tanımlama olarak da adlandırılır *aşırı* işleci.</span><span class="sxs-lookup"><span data-stu-id="27d01-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27d01-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="27d01-105">Example</span></span>  
 <span data-ttu-id="27d01-106">Aşağıdaki örnek SQL yapısı erişen <xref:System.Data.SqlTypes.SqlString>, dönüşüm işleçleri tanımlar ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) bir SQL dizesi arasında iki yönlü ve [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dize.</span><span class="sxs-lookup"><span data-stu-id="27d01-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string.</span></span> <span data-ttu-id="27d01-107">Kullanım `CType(` *SQL dizesi ifadesini*, `String)` SQL dizeye dönüştürmek için bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dize ve `CType(` *Visual Basic dize ifadesi*, <xref:System.Data.SqlTypes.SqlString> `)` ters yönde dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="27d01-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="27d01-108"><xref:System.Data.SqlTypes.SqlString> Yapısını tanımlayan bir dönüşüm işleci ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) gelen `String` için <xref:System.Data.SqlTypes.SqlString> ve başka bir <xref:System.Data.SqlTypes.SqlString> için `String`.</span><span class="sxs-lookup"><span data-stu-id="27d01-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="27d01-109">Atayan deyimi `title` için `jobTitle` ilk işleci kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlev çağrısı kullanır ikinci.</span><span class="sxs-lookup"><span data-stu-id="27d01-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27d01-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="27d01-110">Compiling the Code</span></span>  
 <span data-ttu-id="27d01-111">Sınıf veya yapı kullanmakta olduğunuz kullanmak istediğiniz işleci tanımlar emin olun.</span><span class="sxs-lookup"><span data-stu-id="27d01-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="27d01-112">Sınıf veya yapı her işleci aşırı yükleme için kullanılabilir tanımlanmış varsayalım değil.</span><span class="sxs-lookup"><span data-stu-id="27d01-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="27d01-113">Kullanılabilir operatörler listesi için bkz: [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="27d01-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="27d01-114">Uygun dahil `Imports` başında SQL dizesi bildirimi kaynak dosyasının (Bu durumda <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="27d01-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="27d01-115">Projenizi System.Data ve System.XML başvuruları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27d01-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d01-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27d01-116">See Also</span></span>  
 [<span data-ttu-id="27d01-117">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="27d01-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="27d01-118">Nasıl yapılır: bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="27d01-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="27d01-119">Nasıl yapılır: bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="27d01-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="27d01-120">Nasıl yapılır: bir işleç yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="27d01-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="27d01-121">Genişletme</span><span class="sxs-lookup"><span data-stu-id="27d01-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="27d01-122">Daraltma</span><span class="sxs-lookup"><span data-stu-id="27d01-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="27d01-123">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="27d01-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="27d01-124">Nasıl yapılır: bir yapıyı bildirme</span><span class="sxs-lookup"><span data-stu-id="27d01-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="27d01-125">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="27d01-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="27d01-126">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="27d01-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

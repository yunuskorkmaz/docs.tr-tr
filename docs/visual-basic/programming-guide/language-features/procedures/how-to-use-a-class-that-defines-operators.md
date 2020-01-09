---
title: 'Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma'
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
ms.openlocfilehash: 455c839702b90738ec5aea37c1b09d72eba42ff4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347886"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="fcc1e-102">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcc1e-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="fcc1e-103">Kendi işleçlerini tanımlayan bir sınıf veya yapı kullanıyorsanız, bu işleçlere Visual Basic erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="fcc1e-104">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcc1e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcc1e-105">Example</span></span>  
 <span data-ttu-id="fcc1e-106">Aşağıdaki örnek, bir SQL dizesi ve bir Visual Basic dizesi arasında her iki yönde de dönüştürme işleçlerini ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) tanımlayan SQL yapısına erişir <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="fcc1e-107">`CType(`*SQL dize ifadesi*kullanın, bir sql dizesini Visual Basic bir dizeye dönüştürmek için `String)` ve `CType(`*Visual Basic dize ifadesi*, <xref:System.Data.SqlTypes.SqlString>`)` diğer yönde dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="fcc1e-108"><xref:System.Data.SqlTypes.SqlString> yapısı, `String` bir dönüştürme işlecini ([CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md)) <xref:System.Data.SqlTypes.SqlString> ve <xref:System.Data.SqlTypes.SqlString> arasında bir `String`tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="fcc1e-109">`jobTitle` `title` atayan ifade, ilk işleci kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlev çağrısı ikincisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="fcc1e-110">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="fcc1e-110">Compile the code</span></span>  
 <span data-ttu-id="fcc1e-111">Kullandığınız sınıf veya yapının kullanmak istediğiniz işleci tanımladığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="fcc1e-112">Sınıf veya yapının, aşırı yükleme için kullanılabilen her işleci tanımladığını varsayın.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="fcc1e-113">Kullanılabilir operatörlerin bir listesi için bkz. [operator deyimleri](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fcc1e-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="fcc1e-114">Kaynak dosyanızın başlangıcında SQL dizesi için uygun `Imports` ifadesini ekleyin (Bu durumda <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="fcc1e-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="fcc1e-115">Projenizin System. Data ve System. XML öğesine başvuruları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc1e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcc1e-116">See also</span></span>

- [<span data-ttu-id="fcc1e-117">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="fcc1e-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="fcc1e-118">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="fcc1e-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="fcc1e-119">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="fcc1e-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="fcc1e-120">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="fcc1e-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="fcc1e-121">Widening</span><span class="sxs-lookup"><span data-stu-id="fcc1e-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="fcc1e-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="fcc1e-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="fcc1e-123">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="fcc1e-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="fcc1e-124">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="fcc1e-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="fcc1e-125">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="fcc1e-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="fcc1e-126">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="fcc1e-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

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
ms.openlocfilehash: fe15e976e6a5469f2a9d1b3521a70a3e1860fdd3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414356"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="386d0-102">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="386d0-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="386d0-103">Kendi işleçlerini tanımlayan bir sınıf veya yapı kullanıyorsanız, bu işleçlere Visual Basic erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="386d0-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="386d0-104">Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="386d0-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="386d0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="386d0-105">Example</span></span>  
 <span data-ttu-id="386d0-106">Aşağıdaki örnek, <xref:System.Data.SqlTypes.SqlString> BIR SQL dizesi ve bir Visual Basic dizesi arasında her iki yönde de dönüştürme işleçlerini ([CType işlevi](../../../language-reference/functions/ctype-function.md)) tanımlayan SQL yapısına erişir.</span><span class="sxs-lookup"><span data-stu-id="386d0-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="386d0-107">SQL dize `CType(` *ifadesini*, `String)` bir SQL dizesini bir Visual Basic dizesine dönüştürmek için ve `CType(` *Visual Basic dize ifadesini*kullanarak <xref:System.Data.SqlTypes.SqlString> `)` diğer yönde dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="386d0-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="386d0-108"><xref:System.Data.SqlTypes.SqlString>Yapı, öğesinden ve öğesinden öğesinden öğesine bir dönüştürme işleci ([CType işlevi](../../../language-reference/functions/ctype-function.md)) tanımlar `String` <xref:System.Data.SqlTypes.SqlString> <xref:System.Data.SqlTypes.SqlString> `String` .</span><span class="sxs-lookup"><span data-stu-id="386d0-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="386d0-109">Öğesine atayan ifade `title` `jobTitle` , ilk işleci kullanır ve <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlev çağrısı ikincisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="386d0-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="386d0-110">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="386d0-110">Compile the code</span></span>  
 <span data-ttu-id="386d0-111">Kullandığınız sınıf veya yapının kullanmak istediğiniz işleci tanımladığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="386d0-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="386d0-112">Sınıf veya yapının, aşırı yükleme için kullanılabilen her işleci tanımladığını varsayın.</span><span class="sxs-lookup"><span data-stu-id="386d0-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="386d0-113">Kullanılabilir operatörlerin bir listesi için bkz. [operator deyimleri](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="386d0-113">For a list of available operators, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="386d0-114">`Imports`Kaynak dosyanızın başına (Bu durumda) SQL dizesi için uygun bir ifade ekleyin <xref:System.Data.SqlTypes> .</span><span class="sxs-lookup"><span data-stu-id="386d0-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="386d0-115">Projenizin System. Data ve System. XML öğesine başvuruları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="386d0-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="386d0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="386d0-116">See also</span></span>

- [<span data-ttu-id="386d0-117">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="386d0-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="386d0-118">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="386d0-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="386d0-119">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="386d0-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="386d0-120">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="386d0-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="386d0-121">Genişletme</span><span class="sxs-lookup"><span data-stu-id="386d0-121">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="386d0-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="386d0-122">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="386d0-123">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="386d0-123">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="386d0-124">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="386d0-124">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="386d0-125">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="386d0-125">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="386d0-126">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="386d0-126">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)

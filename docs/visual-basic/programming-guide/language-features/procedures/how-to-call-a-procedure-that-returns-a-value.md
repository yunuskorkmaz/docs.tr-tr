---
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 7f5d46babf31ea3c6babb29c0f1c08a23e51d598
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340736"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="eb0f9-102">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb0f9-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="eb0f9-103">A `Function` procedure returns a value to the calling code.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="eb0f9-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="eb0f9-105">To call a Function procedure within an expression</span><span class="sxs-lookup"><span data-stu-id="eb0f9-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="eb0f9-106">Use the `Function` procedure name the same way you would use a variable.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="eb0f9-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="eb0f9-108">Follow the procedure name with parentheses to enclose the argument list.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="eb0f9-109">If there are no arguments, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="eb0f9-110">However, using the parentheses makes your code easier to read.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="eb0f9-111">Place the arguments in the argument list within the parentheses, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="eb0f9-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="eb0f9-113">Alternatively, you can pass one or more arguments by name.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="eb0f9-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="eb0f9-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="eb0f9-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="eb0f9-116">To call a Function procedure in an assignment statement</span><span class="sxs-lookup"><span data-stu-id="eb0f9-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="eb0f9-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="eb0f9-118">Follow the procedure name with parentheses to enclose the argument list.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="eb0f9-119">If there are no arguments, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="eb0f9-120">However, using the parentheses makes your code easier to read.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="eb0f9-121">Place the arguments in the argument list within the parentheses, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="eb0f9-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="eb0f9-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb0f9-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb0f9-124">Example</span></span>  
 <span data-ttu-id="eb0f9-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="eb0f9-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="eb0f9-127">`Environ` takes the variable name as its sole argument.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="eb0f9-128">It returns the variable's value to the calling code.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="eb0f9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb0f9-129">See also</span></span>

- [<span data-ttu-id="eb0f9-130">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="eb0f9-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="eb0f9-131">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="eb0f9-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="eb0f9-132">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="eb0f9-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="eb0f9-133">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb0f9-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="eb0f9-134">Nasıl yapılır: Bir Yordamdan Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="eb0f9-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="eb0f9-135">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="eb0f9-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)

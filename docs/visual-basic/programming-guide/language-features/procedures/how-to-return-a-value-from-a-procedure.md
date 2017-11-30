---
title: "Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce7aa0942be413986cb010963753447ea18cdf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="5169d-102">Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5169d-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="5169d-103">A `Function` yordamı değeri döndürür çağıran kodu çalıştırarak ya da bir `Return` deyimi veya karşılaşmadan bir `Exit Function` veya `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5169d-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="5169d-104">Return deyimi kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="5169d-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="5169d-105">PUT bir `Return` yordam görev tamamlandı burada noktada deyimi.</span><span class="sxs-lookup"><span data-stu-id="5169d-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="5169d-106">İzleyin `Return` dönüş çağıran kodu istediğiniz anahtar sözcüğü ile değer döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="5169d-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="5169d-107">Birden fazla sahip `Return` aynı yordamı deyiminde.</span><span class="sxs-lookup"><span data-stu-id="5169d-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="5169d-108">Aşağıdaki `Function` yordamı uzun yan veya sağ üçgen hipotenüsü hesaplar ve arama kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5169d-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     <span data-ttu-id="5169d-109">Aşağıdaki örnek tipik bir çağrı gösterilmektedir `hypotenuse`, döndürülen değer depolar.</span><span class="sxs-lookup"><span data-stu-id="5169d-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="5169d-110">Exit işlevi veya End işlevi kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="5169d-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="5169d-111">En az bir yerinde `Function` yordamı, Ata bir değer yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="5169d-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="5169d-112">Çalıştırdığınızda bir `Exit Function` veya `End Function` deyimi, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] en son yordam adına atanmış bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="5169d-112">When you execute an `Exit Function` or `End Function` statement, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="5169d-113">Birden fazla sahip `Exit Function` aynı yordamı ve deyiminde karışık `Return` ve `Exit Function` aynı yordamı deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="5169d-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="5169d-114">Yalnızca bir bulunabilir `End Function` deyiminde bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="5169d-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="5169d-115">Daha fazla bilgi ve bir örnek için "Dönüş değeri" bölümüne bakın [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5169d-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5169d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5169d-116">See Also</span></span>  
 [<span data-ttu-id="5169d-117">Yordamları</span><span class="sxs-lookup"><span data-stu-id="5169d-117">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5169d-118">Alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="5169d-118">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="5169d-119">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="5169d-119">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="5169d-120">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="5169d-120">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="5169d-121">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="5169d-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5169d-122">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="5169d-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5169d-123">Return deyimi</span><span class="sxs-lookup"><span data-stu-id="5169d-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="5169d-124">Nasıl yapılır: değer döndüren bir yordam oluşturma</span><span class="sxs-lookup"><span data-stu-id="5169d-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="5169d-125">Nasıl yapılır: değer döndüren bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="5169d-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)

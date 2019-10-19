---
title: Return Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: edaaf09f5a984344f7e89c9da988c529774934e9
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583265"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="6126b-102">Return Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6126b-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="6126b-103">@No__t_0, `Sub`, `Get`, `Set` veya `Operator` yordamı çağıran koda denetim döndürür.</span><span class="sxs-lookup"><span data-stu-id="6126b-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6126b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6126b-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="6126b-105">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="6126b-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="6126b-106">@No__t_0, `Get` veya `Operator` yordamında gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6126b-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="6126b-107">Çağırma koduna döndürülecek değeri temsil eden ifade.</span><span class="sxs-lookup"><span data-stu-id="6126b-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6126b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6126b-108">Remarks</span></span>  
 <span data-ttu-id="6126b-109">Bir `Sub` veya `Set` yordamında `Return`, bir `Exit Sub` veya `Exit Property` ifadesiyle eşdeğerdir ve `expression` sağlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6126b-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="6126b-110">@No__t_0, `Get` veya `Operator` yordamında, `Return` deyimin `expression` içermesi gerekir ve `expression` yordamın dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6126b-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="6126b-111">Bir `Function` veya `Get` yordamında, dönüş değeri olarak kullanılacak yordam adına bir ifade atama ve sonra bir `Exit Function` ya da `Exit Property` deyimi yürütme alternatifi de vardır.</span><span class="sxs-lookup"><span data-stu-id="6126b-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="6126b-112">@No__t_0 yordamında `Return expression` kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6126b-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="6126b-113">Aynı yordamda uygun olan çok sayıda `Return` deyimi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6126b-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6126b-114">Bir `Finally` bloğundaki kod, bir `Try` `Return` deyimden sonra çalışır, ancak bu `Return` deyimin yürütmeden önce `Catch` bloğunda.</span><span class="sxs-lookup"><span data-stu-id="6126b-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="6126b-115">Bir `Return` deyimleri, bir `Finally` bloğuna dahil edilemez.</span><span class="sxs-lookup"><span data-stu-id="6126b-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6126b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="6126b-116">Example</span></span>  
 <span data-ttu-id="6126b-117">Aşağıdaki örnek, yordamı başka bir şey yapmak zorunda olmadığında çağırma koduna geri dönmek için `Return` ifadesini birkaç kez kullanır.</span><span class="sxs-lookup"><span data-stu-id="6126b-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="6126b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6126b-118">See also</span></span>

- [<span data-ttu-id="6126b-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="6126b-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="6126b-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="6126b-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6126b-121">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="6126b-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="6126b-122">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="6126b-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="6126b-123">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="6126b-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="6126b-124">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="6126b-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="6126b-125">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="6126b-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="6126b-126">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="6126b-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

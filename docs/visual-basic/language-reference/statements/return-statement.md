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
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957668"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="f1e3f-102">Return Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1e3f-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="f1e3f-103">`Function`, ,,`Sub`Veya yordamıçağıran`Operator` koda denetim döndürür. `Get` `Set`</span><span class="sxs-lookup"><span data-stu-id="f1e3f-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="f1e3f-105">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="f1e3f-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="f1e3f-106">`Function` ,`Get`Veya yordamında`Operator` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="f1e3f-107">Çağırma koduna döndürülecek değeri temsil eden ifade.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1e3f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1e3f-108">Remarks</span></span>  
 <span data-ttu-id="f1e3f-109">`Sub` Veya yordamında`Set` , ifade`Return` bir veyaifadesiyle`Exit Property` eşdeğerdir ve`expression`sağlanmamalıdır. `Exit Sub`</span><span class="sxs-lookup"><span data-stu-id="f1e3f-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="f1e3f-110">Bir `Function`, `Get`veya yordamında`Operator` ,`expression`ifadesinin içermesi gerekir ve`expression` yordamın dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmelidir. `Return`</span><span class="sxs-lookup"><span data-stu-id="f1e3f-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="f1e3f-111">Bir `Function` veya `Get` yordamında, dönüş değeri olarak kullanılacak yordam adına bir ifade atama ve sonra bir `Exit Function` veya `Exit Property` deyimini yürütme alternatifine de sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="f1e3f-112">Bir `Operator` yordamda, kullanmanız `Return expression`gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="f1e3f-113">Aynı yordamda uygun olan sayıda `Return` deyim dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1e3f-114">`Finally` Bir bloktaki kod, bir `Try` veya `Return` `Catch` bloğundaki deyimden sonra çalışır, ancak bu `Return` deyimden önce çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="f1e3f-115">Bir `Return` ifade bir `Finally` bloğa dahil edilemez.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1e3f-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1e3f-116">Example</span></span>  
 <span data-ttu-id="f1e3f-117">Aşağıdaki örnek, yordamı başka `Return` bir şey yapmak zorunda olmadığında çağıran koda dönmek için birkaç kez ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="f1e3f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1e3f-118">See also</span></span>

- [<span data-ttu-id="f1e3f-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="f1e3f-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="f1e3f-121">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="f1e3f-122">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="f1e3f-123">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="f1e3f-124">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="f1e3f-125">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="f1e3f-126">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1e3f-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

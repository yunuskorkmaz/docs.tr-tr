---
title: Return Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="08de6-102">Return Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08de6-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="08de6-103">Denetim adlı kodu döndürür bir `Function`, `Sub`, `Get`, `Set`, veya `Operator` yordamı.</span><span class="sxs-lookup"><span data-stu-id="08de6-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08de6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08de6-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="08de6-105">Bölümü</span><span class="sxs-lookup"><span data-stu-id="08de6-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="08de6-106">Gerekli bir `Function`, `Get`, veya `Operator` yordamı.</span><span class="sxs-lookup"><span data-stu-id="08de6-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="08de6-107">Çağrıyı yapan kod döndürülecek değer temsil eden ifade.</span><span class="sxs-lookup"><span data-stu-id="08de6-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08de6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08de6-108">Remarks</span></span>  
 <span data-ttu-id="08de6-109">İçinde bir `Sub` veya `Set` yordamı, `Return` açıklamadır eşdeğer bir `Exit Sub` veya `Exit Property` deyimi, ve `expression` sağlanmadı gerekir.</span><span class="sxs-lookup"><span data-stu-id="08de6-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="08de6-110">İçinde bir `Function`, `Get`, veya `Operator` yordamı, `Return` deyimi içermelidir `expression`, ve `expression` yordamı dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="08de6-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="08de6-111">İçinde bir `Function` veya `Get` yordamı, oluşturmuş olmanız da dönüş değeri olarak hizmet vermek için yordam adı bir ifade atamak ve ardından yürütme alternatif bir `Exit Function` veya `Exit Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="08de6-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="08de6-112">İçinde bir `Operator` yordamı kullanmalıdır `Return``expression`.</span><span class="sxs-lookup"><span data-stu-id="08de6-112">In an `Operator` procedure, you must use `Return``expression`.</span></span>  
  
 <span data-ttu-id="08de6-113">Kadar içerebilir `Return` deyimleri aynı yordamı uygun olarak.</span><span class="sxs-lookup"><span data-stu-id="08de6-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08de6-114">Kodda bir `Finally` blok sonra çalışan bir `Return` deyiminde bir `Try` veya `Catch` blok karşılaşıldı, ancak önce `Return` deyimini yürütür.</span><span class="sxs-lookup"><span data-stu-id="08de6-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="08de6-115">A `Return` deyimi yer olamaz bir `Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="08de6-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08de6-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="08de6-116">Example</span></span>  
 <span data-ttu-id="08de6-117">Aşağıdaki örnek kullanır `Return` deyimi yordamı başka bir şey yapmama gerek var çağıran kodu döndürülecek birkaç kez.</span><span class="sxs-lookup"><span data-stu-id="08de6-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="08de6-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08de6-118">See Also</span></span>  
 [<span data-ttu-id="08de6-119">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="08de6-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="08de6-120">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="08de6-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="08de6-121">Get deyimi</span><span class="sxs-lookup"><span data-stu-id="08de6-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="08de6-122">Set deyimi</span><span class="sxs-lookup"><span data-stu-id="08de6-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="08de6-123">Operator deyimi</span><span class="sxs-lookup"><span data-stu-id="08de6-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="08de6-124">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="08de6-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="08de6-125">Exit deyimi</span><span class="sxs-lookup"><span data-stu-id="08de6-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="08de6-126">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="08de6-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

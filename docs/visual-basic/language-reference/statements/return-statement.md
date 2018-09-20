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
ms.openlocfilehash: fe200add4e29fe4bbe0fdf335dcd94107b8ff1eb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323330"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="893ba-102">Return Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="893ba-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="893ba-103">Denetim çağıran koda döndürür bir `Function`, `Sub`, `Get`, `Set`, veya `Operator` yordamı.</span><span class="sxs-lookup"><span data-stu-id="893ba-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="893ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="893ba-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="893ba-105">Bölümü</span><span class="sxs-lookup"><span data-stu-id="893ba-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="893ba-106">Gerekli bir `Function`, `Get`, veya `Operator` yordamı.</span><span class="sxs-lookup"><span data-stu-id="893ba-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="893ba-107">Çağrıldığı koda döndürülecek değeri temsil eden ifade.</span><span class="sxs-lookup"><span data-stu-id="893ba-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="893ba-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="893ba-108">Remarks</span></span>  
 <span data-ttu-id="893ba-109">İçinde bir `Sub` veya `Set` yordamı `Return` deyimi, bir `Exit Sub` veya `Exit Property` deyimi ve `expression` belirtilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="893ba-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="893ba-110">İçinde bir `Function`, `Get`, veya `Operator` yordamı `Return` deyimi içermelidir `expression`, ve `expression` yordamın dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="893ba-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="893ba-111">İçinde bir `Function` veya `Get` yordamı,'iniz de alternatif yordam adı, dönüş değeri olarak görev yapacak bir ifade atayarak ve ardından yürütme bir `Exit Function` veya `Exit Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="893ba-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="893ba-112">İçinde bir `Operator` yordamı kullanmalıdır `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="893ba-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="893ba-113">Kadar içerebilir `Return` deyimleri aynı yordam içinde uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="893ba-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="893ba-114">Kodda bir `Finally` blok sonra çalışan bir `Return` deyiminde bir `Try` veya `Catch` bloğudur karşılaşıldı, ancak önce `Return` deyimi yürütür.</span><span class="sxs-lookup"><span data-stu-id="893ba-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="893ba-115">A `Return` deyimi eklenemiyor bir `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="893ba-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="893ba-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="893ba-116">Example</span></span>  
 <span data-ttu-id="893ba-117">Aşağıdaki örnekte `Return` deyimi yordamı başka bir şey yapmanız gerekmez, çağıran koda geri dönmek için birkaç kez.</span><span class="sxs-lookup"><span data-stu-id="893ba-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="893ba-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="893ba-118">See Also</span></span>  
 [<span data-ttu-id="893ba-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="893ba-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="893ba-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="893ba-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="893ba-121">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="893ba-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="893ba-122">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="893ba-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="893ba-123">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="893ba-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="893ba-124">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="893ba-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="893ba-125">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="893ba-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="893ba-126">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="893ba-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

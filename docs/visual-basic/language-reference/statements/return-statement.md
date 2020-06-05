---
title: Return Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: cdb58e32c30c8e6c1662fb698ac5576c3f71258c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404206"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="f7758-102">Return Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7758-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="f7758-103">,,, `Function` `Sub` `Get` `Set` Veya `Operator` yordamı çağıran koda denetim döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7758-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7758-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7758-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="f7758-105">Bölüm</span><span class="sxs-lookup"><span data-stu-id="f7758-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="f7758-106">`Function`, `Get` Veya `Operator` yordamında gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f7758-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="f7758-107">Çağırma koduna döndürülecek değeri temsil eden ifade.</span><span class="sxs-lookup"><span data-stu-id="f7758-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7758-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7758-108">Remarks</span></span>  
 <span data-ttu-id="f7758-109">`Sub`Veya `Set` yordamında, `Return` ifade bir `Exit Sub` veya `Exit Property` ifadesiyle eşdeğerdir ve `expression` sağlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7758-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="f7758-110">Bir `Function` , `Get` veya yordamında, `Operator` `Return` ifadesinin içermesi gerekir `expression` ve `expression` yordamın dönüş türüne dönüştürülebilir bir veri türü olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f7758-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="f7758-111">Bir `Function` veya `Get` yordamında, dönüş değeri olarak kullanılacak yordam adına bir ifade atama ve sonra bir veya deyimini yürütme alternatifine de sahipsiniz `Exit Function` `Exit Property` .</span><span class="sxs-lookup"><span data-stu-id="f7758-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="f7758-112">Bir `Operator` yordamda, kullanmanız gerekir `Return expression` .</span><span class="sxs-lookup"><span data-stu-id="f7758-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="f7758-113">`Return`Aynı yordamda uygun olan sayıda deyim dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7758-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7758-114">Bir bloktaki kod, `Finally` `Return` bir veya bloğundaki deyimden sonra çalışır `Try` `Catch` , ancak bu `Return` deyimden önce çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="f7758-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="f7758-115">Bir `Return` ifade bir bloğa dahil edilemez `Finally` .</span><span class="sxs-lookup"><span data-stu-id="f7758-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7758-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7758-116">Example</span></span>  
 <span data-ttu-id="f7758-117">Aşağıdaki örnek, `Return` yordamı başka bir şey yapmak zorunda olmadığında çağıran koda dönmek için birkaç kez ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7758-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="f7758-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7758-118">See also</span></span>

- [<span data-ttu-id="f7758-119">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7758-119">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="f7758-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7758-120">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="f7758-121">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7758-121">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="f7758-122">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="f7758-122">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="f7758-123">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7758-123">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="f7758-124">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7758-124">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="f7758-125">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7758-125">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="f7758-126">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7758-126">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)

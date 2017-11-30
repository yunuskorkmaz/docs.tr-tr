---
title: Call Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="27fd7-102">Call Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27fd7-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="27fd7-103">Aktarır denetlemek için bir `Function`, `Sub`, veya dinamik bağlantı kitaplığı (DLL) yordamı.</span><span class="sxs-lookup"><span data-stu-id="27fd7-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fd7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27fd7-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="27fd7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="27fd7-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="27fd7-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="27fd7-106">Required.</span></span> <span data-ttu-id="27fd7-107">Çağrılacak yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="27fd7-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="27fd7-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="27fd7-108">Optional.</span></span> <span data-ttu-id="27fd7-109">Değişkenleri ya da çağrıldığında yordamına geçirilen bağımsız değişkenlerini temsil eden ifadeleri listesi.</span><span class="sxs-lookup"><span data-stu-id="27fd7-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="27fd7-110">Birden çok bağımsız değişkenleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="27fd7-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="27fd7-111">Dahil ederseniz `argumentList`, parantez içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="27fd7-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27fd7-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27fd7-112">Remarks</span></span>  
 <span data-ttu-id="27fd7-113">Kullanabileceğiniz `Call` bir yordam çağırdığınızda anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="27fd7-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="27fd7-114">Yordam çağrıları için bu anahtar sözcük kullanmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="27fd7-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="27fd7-115">Tipik olarak kullandığınız `Call` çağrılan ifadesi bir tanımlayıcı ile başlatılamadığında anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="27fd7-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="27fd7-116">Kullanımı `Call` anahtar sözcüğü diğer kullanımlar için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="27fd7-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="27fd7-117">Yordam bir değer döndürürse `Call` deyimi atar.</span><span class="sxs-lookup"><span data-stu-id="27fd7-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27fd7-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="27fd7-118">Example</span></span>  
 <span data-ttu-id="27fd7-119">Aşağıdaki kod iki örnek gösterir nerede `Call` bir yordam çağrısı anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="27fd7-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="27fd7-120">Her iki örneklerde, çağrılan ifadesi bir tanımlayıcı ile başlamıyor.</span><span class="sxs-lookup"><span data-stu-id="27fd7-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="27fd7-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27fd7-121">See Also</span></span>  
 [<span data-ttu-id="27fd7-122">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="27fd7-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="27fd7-123">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="27fd7-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="27fd7-124">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="27fd7-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="27fd7-125">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="27fd7-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)

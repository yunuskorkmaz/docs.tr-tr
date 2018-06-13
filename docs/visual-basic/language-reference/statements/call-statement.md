---
title: Call Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 2074f44aedf59f1570e73c898a9bf64e57034923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603398"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="4a709-102">Call Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a709-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="4a709-103">Aktarır denetlemek için bir `Function`, `Sub`, veya dinamik bağlantı kitaplığı (DLL) yordamı.</span><span class="sxs-lookup"><span data-stu-id="4a709-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a709-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a709-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="4a709-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4a709-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="4a709-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4a709-106">Required.</span></span> <span data-ttu-id="4a709-107">Çağrılacak yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="4a709-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="4a709-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4a709-108">Optional.</span></span> <span data-ttu-id="4a709-109">Değişkenleri ya da çağrıldığında yordamına geçirilen bağımsız değişkenlerini temsil eden ifadeleri listesi.</span><span class="sxs-lookup"><span data-stu-id="4a709-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="4a709-110">Birden çok bağımsız değişkenleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="4a709-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="4a709-111">Dahil ederseniz `argumentList`, parantez içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a709-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a709-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a709-112">Remarks</span></span>  
 <span data-ttu-id="4a709-113">Kullanabileceğiniz `Call` bir yordam çağırdığınızda anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="4a709-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="4a709-114">Yordam çağrıları için bu anahtar sözcük kullanmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4a709-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="4a709-115">Tipik olarak kullandığınız `Call` çağrılan ifadesi bir tanımlayıcı ile başlatılamadığında anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="4a709-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="4a709-116">Kullanımı `Call` anahtar sözcüğü diğer kullanımlar için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="4a709-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="4a709-117">Yordam bir değer döndürürse `Call` deyimi atar.</span><span class="sxs-lookup"><span data-stu-id="4a709-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a709-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a709-118">Example</span></span>  
 <span data-ttu-id="4a709-119">Aşağıdaki kod iki örnek gösterir nerede `Call` bir yordam çağrısı anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4a709-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="4a709-120">Her iki örneklerde, çağrılan ifadesi bir tanımlayıcı ile başlamıyor.</span><span class="sxs-lookup"><span data-stu-id="4a709-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4a709-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a709-121">See Also</span></span>  
 [<span data-ttu-id="4a709-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="4a709-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="4a709-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="4a709-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="4a709-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="4a709-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="4a709-125">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="4a709-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)

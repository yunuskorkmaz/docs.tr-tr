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
ms.openlocfilehash: e706650ac6da84d9b4e77fc549811e731be61b92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594167"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="c6bda-102">Call Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6bda-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="c6bda-103">Aktarımı denetlemek için bir `Function`, `Sub`, veya dinamik bağlantı kitaplığı (DLL) yordam.</span><span class="sxs-lookup"><span data-stu-id="c6bda-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6bda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6bda-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c6bda-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c6bda-105">Parts</span></span>  
|||
|---|---|
|`procedureName`|<span data-ttu-id="c6bda-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c6bda-106">Required.</span></span> <span data-ttu-id="c6bda-107">Çağrılacak yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="c6bda-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="c6bda-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c6bda-108">Optional.</span></span> <span data-ttu-id="c6bda-109">Değişkenlerin veya onu çağrıldığında yönteme bağımsız değişkenlerini temsil eden ifadelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="c6bda-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="c6bda-110">Birden çok bağımsız değişkeni virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c6bda-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="c6bda-111">Eklerseniz `argumentList`, parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="c6bda-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="c6bda-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6bda-112">Remarks</span></span>  
 <span data-ttu-id="c6bda-113">Kullanabileceğiniz `Call` bir yordamı çağırdığınızda anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c6bda-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="c6bda-114">Yordam çağrıları için bu anahtar sözcüğünü kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c6bda-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="c6bda-115">Tipik olarak kullandığınız `Call` adlı ifade bir tanımlayıcıyla başlatılamadığında anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c6bda-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="c6bda-116">Kullanım `Call` anahtar sözcüğü diğer kullanımlar için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="c6bda-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="c6bda-117">Yordamı bir değer döndürürse `Call` deyimi atar.</span><span class="sxs-lookup"><span data-stu-id="c6bda-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6bda-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6bda-118">Example</span></span>  
 <span data-ttu-id="c6bda-119">Aşağıdaki kod iki örnek gösterir. burada `Call` bir yordam çağırmak anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c6bda-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="c6bda-120">Örneklerin her ikisi de adlı ifade bir tanımlayıcı ile başlamıyor.</span><span class="sxs-lookup"><span data-stu-id="c6bda-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c6bda-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6bda-121">See also</span></span>
- [<span data-ttu-id="c6bda-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c6bda-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="c6bda-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="c6bda-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c6bda-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="c6bda-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="c6bda-125">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="c6bda-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)

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
ms.openlocfilehash: 755443a99a1ad8b0430a76d2dba1ff27472d4c9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832651"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="d4fd0-102">Call Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4fd0-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="d4fd0-103">Aktarımı denetlemek için bir `Function`, `Sub`, veya dinamik bağlantı kitaplığı (DLL) yordam.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4fd0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4fd0-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d4fd0-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d4fd0-105">Parts</span></span>  
|||
|---|---|
|`procedureName`|<span data-ttu-id="d4fd0-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-106">Required.</span></span> <span data-ttu-id="d4fd0-107">Çağrılacak yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="d4fd0-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-108">Optional.</span></span> <span data-ttu-id="d4fd0-109">Değişkenlerin veya onu çağrıldığında yönteme bağımsız değişkenlerini temsil eden ifadelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="d4fd0-110">Birden çok bağımsız değişkeni virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="d4fd0-111">Eklerseniz `argumentList`, parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="d4fd0-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4fd0-112">Remarks</span></span>  
 <span data-ttu-id="d4fd0-113">Kullanabileceğiniz `Call` bir yordamı çağırdığınızda anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="d4fd0-114">Yordam çağrıları için bu anahtar sözcüğünü kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="d4fd0-115">Tipik olarak kullandığınız `Call` adlı ifade bir tanımlayıcıyla başlatılamadığında anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="d4fd0-116">Kullanım `Call` anahtar sözcüğü diğer kullanımlar için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="d4fd0-117">Yordamı bir değer döndürürse `Call` deyimi atar.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4fd0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4fd0-118">Example</span></span>  
 <span data-ttu-id="d4fd0-119">Aşağıdaki kod iki örnek gösterir. burada `Call` bir yordam çağırmak anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="d4fd0-120">Örneklerin her ikisi de adlı ifade bir tanımlayıcı ile başlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="d4fd0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4fd0-121">See also</span></span>

- [<span data-ttu-id="d4fd0-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4fd0-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d4fd0-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4fd0-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d4fd0-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="d4fd0-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="d4fd0-125">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="d4fd0-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)

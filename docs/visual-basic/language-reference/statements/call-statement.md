---
title: Call Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 7de194ea23827e08c49f4519c1000708a4bd91b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350156"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="c713c-102">Call Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c713c-102">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="c713c-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span><span class="sxs-lookup"><span data-stu-id="c713c-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c713c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c713c-104">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c713c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c713c-105">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="c713c-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c713c-106">Required.</span></span> <span data-ttu-id="c713c-107">Name of the procedure to call.</span><span class="sxs-lookup"><span data-stu-id="c713c-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="c713c-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c713c-108">Optional.</span></span> <span data-ttu-id="c713c-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span><span class="sxs-lookup"><span data-stu-id="c713c-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="c713c-110">Multiple arguments are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="c713c-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="c713c-111">If you include `argumentList`, you must enclose it in parentheses.</span><span class="sxs-lookup"><span data-stu-id="c713c-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="c713c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c713c-112">Remarks</span></span>

 <span data-ttu-id="c713c-113">You can use the `Call` keyword when you call a procedure.</span><span class="sxs-lookup"><span data-stu-id="c713c-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="c713c-114">For most procedure calls, you aren’t required to use this  keyword.</span><span class="sxs-lookup"><span data-stu-id="c713c-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="c713c-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span><span class="sxs-lookup"><span data-stu-id="c713c-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="c713c-116">Use of the `Call` keyword for other uses isn't recommended.</span><span class="sxs-lookup"><span data-stu-id="c713c-116">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="c713c-117">If the procedure returns a value, the `Call` statement discards it.</span><span class="sxs-lookup"><span data-stu-id="c713c-117">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="c713c-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="c713c-118">Example</span></span>

 <span data-ttu-id="c713c-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span><span class="sxs-lookup"><span data-stu-id="c713c-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="c713c-120">In both examples, the called expression doesn't start with an identifier.</span><span class="sxs-lookup"><span data-stu-id="c713c-120">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="c713c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c713c-121">See also</span></span>

- [<span data-ttu-id="c713c-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c713c-122">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="c713c-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="c713c-123">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="c713c-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="c713c-124">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="c713c-125">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="c713c-125">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)

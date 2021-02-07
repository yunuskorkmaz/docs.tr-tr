---
description: 'Daha fazla bilgi edinin: Call deyimleri (Visual Basic)'
title: Call Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 70e6c109621c3710ad9476a952e9c384a142ba3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674018"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="c18a9-103">Call Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c18a9-103">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="c18a9-104">Denetimi bir `Function` , `Sub` veya dinamik bağlantı KITAPLıĞı (dll) yordamına aktarır.</span><span class="sxs-lookup"><span data-stu-id="c18a9-104">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18a9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c18a9-105">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c18a9-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c18a9-106">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="c18a9-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c18a9-107">Required.</span></span> <span data-ttu-id="c18a9-108">Çağrılacak yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="c18a9-108">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="c18a9-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c18a9-109">Optional.</span></span> <span data-ttu-id="c18a9-110">Çağrıldığında yordama geçirilen bağımsız değişkenleri temsil eden değişkenlerin veya ifadelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="c18a9-110">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="c18a9-111">Birden çok bağımsız değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c18a9-111">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="c18a9-112">Dahil ederseniz `argumentList` , parantez içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c18a9-112">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="c18a9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c18a9-113">Remarks</span></span>

 <span data-ttu-id="c18a9-114">`Call`Bir yordamı çağırdığınızda anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c18a9-114">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="c18a9-115">Çoğu yordam çağrısı için bu anahtar sözcüğünü kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c18a9-115">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="c18a9-116">`Call`Çağrılan ifade bir tanımlayıcı ile başlamaksa, genellikle anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c18a9-116">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="c18a9-117">`Call`Diğer kullanımlar için anahtar sözcüğünün kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="c18a9-117">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="c18a9-118">Yordam bir değer döndürürse, `Call` ifade onu atar.</span><span class="sxs-lookup"><span data-stu-id="c18a9-118">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="c18a9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="c18a9-119">Example</span></span>

 <span data-ttu-id="c18a9-120">Aşağıdaki kod, `Call` bir yordamı çağırmak için anahtar sözcüğünün gerekli olduğu iki örneği göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c18a9-120">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="c18a9-121">Her iki örnekte de çağrılan ifade bir tanımlayıcı ile başlamaz.</span><span class="sxs-lookup"><span data-stu-id="c18a9-121">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="c18a9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c18a9-122">See also</span></span>

- [<span data-ttu-id="c18a9-123">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c18a9-123">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="c18a9-124">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="c18a9-124">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="c18a9-125">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="c18a9-125">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="c18a9-126">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="c18a9-126">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)

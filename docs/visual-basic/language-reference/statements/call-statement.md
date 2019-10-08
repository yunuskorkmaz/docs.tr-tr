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
ms.openlocfilehash: a04ebddc7db176188876da1082e1e6946e1e8eec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005172"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="43aca-102">Call Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43aca-102">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="43aca-103">Denetimi bir `Function`, `Sub` veya dinamik bağlantı kitaplığı (DLL) yordamına aktarır.</span><span class="sxs-lookup"><span data-stu-id="43aca-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43aca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43aca-104">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="43aca-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="43aca-105">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="43aca-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="43aca-106">Required.</span></span> <span data-ttu-id="43aca-107">Çağrılacak yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="43aca-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="43aca-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="43aca-108">Optional.</span></span> <span data-ttu-id="43aca-109">Çağrıldığında yordama geçirilen bağımsız değişkenleri temsil eden değişkenlerin veya ifadelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="43aca-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="43aca-110">Birden çok bağımsız değişken virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="43aca-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="43aca-111">@No__t-0 eklerseniz, parantez içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43aca-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="43aca-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43aca-112">Remarks</span></span>

 <span data-ttu-id="43aca-113">Bir yordamı çağırdığınızda `Call` anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43aca-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="43aca-114">Çoğu yordam çağrısı için bu anahtar sözcüğünü kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="43aca-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="43aca-115">Çağrılan ifade bir tanımlayıcı ile başlamadığınızda genellikle `Call` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="43aca-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="43aca-116">Diğer kullanımlar için `Call` anahtar sözcüğünün kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="43aca-116">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="43aca-117">Yordam bir değer döndürürse `Call` deyimleri onu atar.</span><span class="sxs-lookup"><span data-stu-id="43aca-117">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="43aca-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="43aca-118">Example</span></span>

 <span data-ttu-id="43aca-119">Aşağıdaki kodda, bir yordamı çağırmak için `Call` anahtar sözcüğünün gerekli olduğu iki örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="43aca-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="43aca-120">Her iki örnekte de çağrılan ifade bir tanımlayıcı ile başlamaz.</span><span class="sxs-lookup"><span data-stu-id="43aca-120">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="43aca-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43aca-121">See also</span></span>

- [<span data-ttu-id="43aca-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="43aca-122">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="43aca-123">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="43aca-123">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="43aca-124">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="43aca-124">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="43aca-125">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="43aca-125">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)

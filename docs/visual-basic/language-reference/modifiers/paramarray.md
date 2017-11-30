---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06770f05aabedcf13cc9af1970a2c511a30c73b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="c4229-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4229-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="c4229-103">Bir yordam parametresini belirtilen türdeki öğeleri isteğe bağlı bir dizi aldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4229-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="c4229-104">`ParamArray`parametre listesi yalnızca son parametresinin kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4229-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4229-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4229-105">Remarks</span></span>  
 <span data-ttu-id="c4229-106">`ParamArray`rasgele sayıda bağımsız değişken yordama geçirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4229-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="c4229-107">A `ParamArray` parametresi, kullanarak her zaman bildirilmiş [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="c4229-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="c4229-108">Bir veya daha fazla bağımsız değişken sağlayabilir bir `ParamArray` uygun veri dizisi geçirerek tür parametresi, virgülle ayrılmış bir liste değerleri veya hiçbir şey hiç.</span><span class="sxs-lookup"><span data-stu-id="c4229-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="c4229-109">Ayrıntılar için bkz: "Bir ParamArray çağırma" [parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="c4229-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4229-110">Süresiz olarak büyük olabilen bir dizi ile ilgilenir olduğunda, uygulamanızın iç bazı kapasite taşmasını riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="c4229-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="c4229-111">Bir parametre dizisi arama kodundan kabul ederseniz, uzunluğunu test ve uygulamanız için çok büyük ise uygun adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="c4229-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="c4229-112">`ParamArray` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c4229-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c4229-113">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="c4229-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="c4229-114">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="c4229-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c4229-115">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="c4229-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c4229-116">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="c4229-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4229-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4229-117">See Also</span></span>  
 [<span data-ttu-id="c4229-118">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c4229-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="c4229-119">Parametre dizileri</span><span class="sxs-lookup"><span data-stu-id="c4229-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)

---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: b9dee0fc876c6e7a02d085db7db4bf1c5dd2c68d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816673"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="151aa-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="151aa-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="151aa-103">Bir yordam parametresinin belirtilen türdeki öğeleri isteğe bağlı bir dizi aldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="151aa-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="151aa-104">`ParamArray` parametre listesi yalnızca son parametresinin kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="151aa-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="151aa-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="151aa-105">Remarks</span></span>  
 <span data-ttu-id="151aa-106">`ParamArray` rasgele sayıda bağımsız değişken yordama geçirmeye sağlar.</span><span class="sxs-lookup"><span data-stu-id="151aa-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="151aa-107">A `ParamArray` parametresi her zaman bildirilen kullanarak [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="151aa-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="151aa-108">Bir veya daha fazla bağımsız değişken için sağladığınız bir `ParamArray` uygun veri dizisi geçirerek tür parametresi, virgülle ayrılmış bir liste değerleri veya hiçbir şey hiç.</span><span class="sxs-lookup"><span data-stu-id="151aa-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="151aa-109">Ayrıntılar için "Bir ParamArray çağırma" bölümüne bakın. [parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="151aa-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="151aa-110">Süresiz olarak büyük olabilecek bir dizi işlem olduğunda, uygulamanızın bazı iç kapasite taşmasını riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="151aa-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="151aa-111">Çağıran kodun bir parametre dizisi kabul ederseniz, uzunluğunu test ve uygulamanız için çok büyük ise, uygun adımları atmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="151aa-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="151aa-112">`ParamArray` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="151aa-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="151aa-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="151aa-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="151aa-114">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="151aa-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="151aa-115">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="151aa-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="151aa-116">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="151aa-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="151aa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="151aa-117">See also</span></span>

- [<span data-ttu-id="151aa-118">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="151aa-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="151aa-119">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="151aa-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)

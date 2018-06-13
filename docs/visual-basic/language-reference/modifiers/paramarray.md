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
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597366"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="56473-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56473-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="56473-103">Bir yordam parametresini belirtilen türdeki öğeleri isteğe bağlı bir dizi aldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="56473-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="56473-104">`ParamArray` parametre listesi yalnızca son parametresinin kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56473-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56473-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56473-105">Remarks</span></span>  
 <span data-ttu-id="56473-106">`ParamArray` rasgele sayıda bağımsız değişken yordama geçirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56473-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="56473-107">A `ParamArray` parametresi, kullanarak her zaman bildirilmiş [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="56473-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="56473-108">Bir veya daha fazla bağımsız değişken sağlayabilir bir `ParamArray` uygun veri dizisi geçirerek tür parametresi, virgülle ayrılmış bir liste değerleri veya hiçbir şey hiç.</span><span class="sxs-lookup"><span data-stu-id="56473-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="56473-109">Ayrıntılar için bkz: "Bir ParamArray çağırma" [parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="56473-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56473-110">Süresiz olarak büyük olabilen bir dizi ile ilgilenir olduğunda, uygulamanızın iç bazı kapasite taşmasını riski yoktur.</span><span class="sxs-lookup"><span data-stu-id="56473-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="56473-111">Bir parametre dizisi arama kodundan kabul ederseniz, uzunluğunu test ve uygulamanız için çok büyük ise uygun adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="56473-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="56473-112">`ParamArray` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="56473-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="56473-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="56473-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="56473-114">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="56473-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="56473-115">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="56473-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="56473-116">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="56473-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="56473-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56473-117">See Also</span></span>  
 [<span data-ttu-id="56473-118">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="56473-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="56473-119">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="56473-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)

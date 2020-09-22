---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: baf9303101eea9eed27e8a4eee9e04d255c798e9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867819"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="cab5d-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cab5d-102">ParamArray (Visual Basic)</span></span>

<span data-ttu-id="cab5d-103">Bir yordam parametresinin, belirtilen türde öğe için isteğe bağlı bir dizi aldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cab5d-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="cab5d-104">`ParamArray` , yalnızca bir parametre listesinin son parametresinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cab5d-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cab5d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cab5d-105">Remarks</span></span>  

 <span data-ttu-id="cab5d-106">`ParamArray` yordama rastgele sayıda bağımsız değişken geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cab5d-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="cab5d-107">Bir `ParamArray` parametre, her zaman [ByVal](byval.md)kullanılarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cab5d-107">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="cab5d-108">`ParamArray`Uygun veri türünde bir diziyi, virgülle ayrılmış bir değer listesini veya hiç bir şeyi geçirerek bir parametreye bir veya daha fazla bağımsız değişken sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cab5d-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="cab5d-109">Ayrıntılar için, [parametre dizilerindeki](../../programming-guide/language-features/procedures/parameter-arrays.md)"ParamArray çağırma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="cab5d-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cab5d-110">Süresiz olarak büyük olabilecek bir dizi ile uğraşmanız durumunda, uygulamanızın bazı iç kapasitesini çok fazla çalıştırmaya yönelik bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="cab5d-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="cab5d-111">Çağıran koddan bir parametre dizisini kabul ediyorsanız, uzunluğunu sınamanız ve uygulamanız için çok büyükse uygun adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cab5d-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="cab5d-112">`ParamArray`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="cab5d-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="cab5d-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="cab5d-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="cab5d-114">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="cab5d-114">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="cab5d-115">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="cab5d-115">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="cab5d-116">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="cab5d-116">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cab5d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cab5d-117">See also</span></span>

- [<span data-ttu-id="cab5d-118">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="cab5d-118">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="cab5d-119">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="cab5d-119">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)

---
description: 'Daha fazla bilgi edinin: ParamArray (Visual Basic)'
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: 064bad8a558308ee3361c11d07020e0e3bf40c13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730401"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="7f072-103">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f072-103">ParamArray (Visual Basic)</span></span>

<span data-ttu-id="7f072-104">Bir yordam parametresinin, belirtilen türde öğe için isteğe bağlı bir dizi aldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f072-104">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="7f072-105">`ParamArray` , yalnızca bir parametre listesinin son parametresinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f072-105">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f072-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f072-106">Remarks</span></span>  

 <span data-ttu-id="7f072-107">`ParamArray` yordama rastgele sayıda bağımsız değişken geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f072-107">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="7f072-108">Bir `ParamArray` parametre, her zaman [ByVal](byval.md)kullanılarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f072-108">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="7f072-109">`ParamArray`Uygun veri türünde bir diziyi, virgülle ayrılmış bir değer listesini veya hiç bir şeyi geçirerek bir parametreye bir veya daha fazla bağımsız değişken sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f072-109">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="7f072-110">Ayrıntılar için, [parametre dizilerindeki](../../programming-guide/language-features/procedures/parameter-arrays.md)"ParamArray çağırma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="7f072-110">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7f072-111">Süresiz olarak büyük olabilecek bir dizi ile uğraşmanız durumunda, uygulamanızın bazı iç kapasitesini çok fazla çalıştırmaya yönelik bir risk vardır.</span><span class="sxs-lookup"><span data-stu-id="7f072-111">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="7f072-112">Çağıran koddan bir parametre dizisini kabul ediyorsanız, uzunluğunu sınamanız ve uygulamanız için çok büyükse uygun adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f072-112">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="7f072-113">`ParamArray`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7f072-113">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7f072-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f072-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="7f072-115">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f072-115">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="7f072-116">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f072-116">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="7f072-117">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f072-117">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7f072-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f072-118">See also</span></span>

- [<span data-ttu-id="7f072-119">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="7f072-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="7f072-120">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="7f072-120">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)

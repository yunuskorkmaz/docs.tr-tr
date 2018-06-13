---
title: Yığın için ayrılan alan doldu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593291"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="3c82f-102">Yığın için ayrılan alan doldu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c82f-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="3c82f-103">Yığın yürütülen programınızı taleplerini ile dinamik olarak büyür ve küçülür bellek bir çalışma alanıdır.</span><span class="sxs-lookup"><span data-stu-id="3c82f-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="3c82f-104">Kendi sınırlarını aştı.</span><span class="sxs-lookup"><span data-stu-id="3c82f-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3c82f-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3c82f-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="3c82f-106">Yordamlar çok fazla iç içe değil olduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3c82f-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="3c82f-107">Özyinelemeli yordamlar düzgün sonlandırma emin olun.</span><span class="sxs-lookup"><span data-stu-id="3c82f-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="3c82f-108">Yerel değişkenler kullanılabilir alandan daha fazla yerel değişken gerektiriyorsa, bazı değişkenler modülü düzeyinde bildirme deneyin.</span><span class="sxs-lookup"><span data-stu-id="3c82f-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="3c82f-109">Ayrıca tüm değişkenleri yordamda statik koyarak bildirebilirsiniz `Property`, `Sub`, veya `Function` anahtar sözcüğüyle `Static`.</span><span class="sxs-lookup"><span data-stu-id="3c82f-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="3c82f-110">Veya kullanabilirsiniz `Static` yordamları statik bağımsız değişkenler bildirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="3c82f-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="3c82f-111">Sabit uzunluklu dizeler değişken uzunluklu dizeler daha fazla yığın alanı kullanırken, sabit uzunluklu dizeler değişken uzunluklu dizeler olarak bazıları yeniden tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3c82f-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="3c82f-112">Burada, hiçbir yığın alanı gerektiriyor modülü düzeyinde dize tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="3c82f-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="3c82f-113">Sayısını denetleyin iç içe geçmiş `DoEvents` işlev çağrılarını kullanarak `Calls` hangi yordamların yığında etkin görüntülemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="3c82f-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="3c82f-114">"Olay cascade" olay yordamı zaten yığında çağıran bir olay tetikleme tarafından neden değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="3c82f-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="3c82f-115">Bir olay cascade bir Sonlandırılmamış özyinelemeli yordam çağrısına benzer, ancak çağrı kodda açık bir çağrı yerine, Visual Basic yapıldığından kadar belirgin.</span><span class="sxs-lookup"><span data-stu-id="3c82f-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="3c82f-116">Kullanım `Calls` hangi yordamların yığında etkin görüntülemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="3c82f-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c82f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c82f-117">See Also</span></span>  
 [<span data-ttu-id="3c82f-118">Bellek pencereleri</span><span class="sxs-lookup"><span data-stu-id="3c82f-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)

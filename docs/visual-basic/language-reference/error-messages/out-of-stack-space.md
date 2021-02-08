---
description: 'Hakkında daha fazla bilgi edinin: yığın alanı kalmadı (Visual Basic)'
title: Yığın için ayrılan alan doldu
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: a32ca0d2becade33177596501b7eabde4251e0a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795500"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="bd567-103">Yığın için ayrılan alan doldu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd567-103">Out of stack space (Visual Basic)</span></span>

<span data-ttu-id="bd567-104">Yığın, yürütülen programınızın taleplerini dinamik olarak büyüyen ve küçüldüğü belleğin çalışma alanıdır.</span><span class="sxs-lookup"><span data-stu-id="bd567-104">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="bd567-105">Sınırları aşıldı.</span><span class="sxs-lookup"><span data-stu-id="bd567-105">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd567-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bd567-106">To correct this error</span></span>  
  
1. <span data-ttu-id="bd567-107">Yordamların çok derin iç içe olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="bd567-107">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="bd567-108">Özyinelemeli yordamların düzgün sonlandırılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="bd567-108">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="bd567-109">Yerel değişkenler kullanılabilir olandan daha fazla yerel değişken alanı gerektiriyorsa, modül düzeyinde bazı değişkenler bildirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="bd567-109">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="bd567-110">Ayrıca `Property` ,, `Sub` veya `Function` anahtar sözcüğünden önce kullanarak statik yordamdaki tüm değişkenleri de bildirebilirsiniz `Static` .</span><span class="sxs-lookup"><span data-stu-id="bd567-110">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="bd567-111">Ya da `Static` yordamlar içindeki bağımsız statik değişkenleri bildirmek için ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd567-111">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="bd567-112">Sabit uzunluklu dizeler değişken uzunluklu dizeler olarak daha fazla yığın alanı kullanırken, sabit uzunluklu Dizelerinizin bazılarını değişken uzunluklu dizeler olarak yeniden tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bd567-112">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="bd567-113">Dizeyi, yığın alanı gerektirmeyen modül düzeyinde de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd567-113">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="bd567-114">`DoEvents` `Calls` Yığın üzerinde etkin olan yordamları görüntülemek için iletişim kutusunu kullanarak iç içe geçmiş işlev çağrılarının sayısını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bd567-114">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="bd567-115">Yığında zaten olan bir olay yordamını çağıran bir olay tetikleyerek bir "olay basamaklandırmaya" neden olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="bd567-115">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="bd567-116">Olay basamaklama, Sonlandırılmamış özyinelemeli yordam çağrısına benzerdir, ancak çağrı, koddaki açık bir çağrı yerine Visual Basic tarafından yapıldığından daha az açıktır.</span><span class="sxs-lookup"><span data-stu-id="bd567-116">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="bd567-117">`Calls`Yığında etkin olan yordamları görüntülemek için iletişim kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd567-117">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd567-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd567-118">See also</span></span>

- [<span data-ttu-id="bd567-119">Bellek Pencereleri</span><span class="sxs-lookup"><span data-stu-id="bd567-119">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)

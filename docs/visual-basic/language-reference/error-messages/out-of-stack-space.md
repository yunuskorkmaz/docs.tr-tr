---
title: Yığın için ayrılan alan doldu
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349192"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="ece27-102">Yığın için ayrılan alan doldu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ece27-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="ece27-103">Yığın, yürütülen programınızın taleplerini dinamik olarak büyüyen ve küçüldüğü belleğin çalışma alanıdır.</span><span class="sxs-lookup"><span data-stu-id="ece27-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="ece27-104">Sınırları aşıldı.</span><span class="sxs-lookup"><span data-stu-id="ece27-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ece27-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ece27-105">To correct this error</span></span>  
  
1. <span data-ttu-id="ece27-106">Yordamların çok derin iç içe olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="ece27-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="ece27-107">Özyinelemeli yordamların düzgün sonlandırılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="ece27-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="ece27-108">Yerel değişkenler kullanılabilir olandan daha fazla yerel değişken alanı gerektiriyorsa, modül düzeyinde bazı değişkenler bildirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="ece27-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="ece27-109">Ayrıca, `Static`ile `Property`, `Sub`veya `Function` anahtar sözcüğüyle önce statik yordamdaki tüm değişkenleri de bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece27-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="ece27-110">Ya da yordamlar içindeki bağımsız statik değişkenleri bildirmek için `Static` ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece27-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="ece27-111">Sabit uzunluklu dizeler değişken uzunluklu dizeler olarak daha fazla yığın alanı kullanırken, sabit uzunluklu Dizelerinizin bazılarını değişken uzunluklu dizeler olarak yeniden tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ece27-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="ece27-112">Dizeyi, yığın alanı gerektirmeyen modül düzeyinde de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece27-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="ece27-113">Yığın üzerinde etkin olan yordamları görüntülemek için `Calls` iletişim kutusunu kullanarak iç içe `DoEvents` işlev çağrılarının sayısını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ece27-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="ece27-114">Yığında zaten olan bir olay yordamını çağıran bir olay tetikleyerek bir "olay basamaklandırmaya" neden olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="ece27-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="ece27-115">Olay basamaklama, Sonlandırılmamış özyinelemeli yordam çağrısına benzerdir, ancak çağrı, koddaki açık bir çağrı yerine Visual Basic tarafından yapıldığından daha az açıktır.</span><span class="sxs-lookup"><span data-stu-id="ece27-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="ece27-116">Yığında etkin olan yordamları görüntülemek için `Calls` iletişim kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ece27-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece27-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ece27-117">See also</span></span>

- [<span data-ttu-id="ece27-118">Bellek Pencereleri</span><span class="sxs-lookup"><span data-stu-id="ece27-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)

---
title: Yığın için ayrılan alan doldu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 25905e65e74b11d167d3ce2ad258599fb958eb88
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814607"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="f5918-102">Yığın için ayrılan alan doldu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5918-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="f5918-103">Büyür ve küçülür bellek dinamik olarak yürütülen programınızın talepleri olan bir çalışma alanı yığınıdır.</span><span class="sxs-lookup"><span data-stu-id="f5918-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="f5918-104">Kendi sınırları aşıldı.</span><span class="sxs-lookup"><span data-stu-id="f5918-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5918-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f5918-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="f5918-106">Yordamlar çok derin iç içe değil olduğunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="f5918-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="f5918-107">Özyinelemeli yordamlar düzgün sonlandırmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="f5918-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="f5918-108">Yerel değişkenler kullanılabilir alandan daha fazla yerel değişken gerektiriyorsa, Modül düzeyinde bazı değişkenleri bildirme deneyin.</span><span class="sxs-lookup"><span data-stu-id="f5918-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="f5918-109">Ayrıca tüm değişkenleri yordamda statik koyarak bildirebilirsiniz `Property`, `Sub`, veya `Function` anahtar sözcüğü ile `Static`.</span><span class="sxs-lookup"><span data-stu-id="f5918-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="f5918-110">Ya da `Static` yordamları statik bağımsız değişkenler bildirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="f5918-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="f5918-111">Daha fazla yığın alanı değişken uzunluklu dizeler sabit uzunluklu dizeler kullanmak gibi bazı değişken uzunluklu dizeler olarak, sabit uzunluklu dizeler yeniden tanımlama.</span><span class="sxs-lookup"><span data-stu-id="f5918-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="f5918-112">Ayrıca, hiçbir yığın alanı gerektiren modül düzeyinde dizesi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5918-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="f5918-113">Sayısını denetleyin iç içe geçmiş `DoEvents` işlev çağrıları kullanarak `Calls` hangi yordamların yığında etkin görünüme iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="f5918-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="f5918-114">Bir "olay cascade" olay yordamı zaten yığında çağıran olarak olay tetiklemeyi tarafından neden olmadı emin olun.</span><span class="sxs-lookup"><span data-stu-id="f5918-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="f5918-115">Bir olay cascade Sonlandırılmamış özyinelemeli yordam çağrısı benzer, ancak kod içinde açık çağrı yerine, Visual Basic çağrı yapıldığından daha az belirgin.</span><span class="sxs-lookup"><span data-stu-id="f5918-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="f5918-116">Kullanım `Calls` hangi yordamların yığında etkin görünüme iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="f5918-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5918-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5918-117">See also</span></span>

- [<span data-ttu-id="f5918-118">Bellek Pencereleri</span><span class="sxs-lookup"><span data-stu-id="f5918-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)

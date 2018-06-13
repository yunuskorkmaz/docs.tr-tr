---
title: Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 6231d48f3f90d8e436dc80bf4670886c1d030387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587666"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="b6f86-102">Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="b6f86-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="b6f86-103">Önceki bir işlev değerlendirmesi zaman aşımına uğradığından İşlev değerlendirmesi devre dışı bırakılır. İşlev değerlendirmesi yeniden etkinleştirmek için yeniden adımını veya hata ayıklamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="b6f86-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="b6f86-104">Visual Studio hata ayıklayıcısı bir yordam çağrısı bir ifade belirtir, ancak başka bir değerlendirme zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b6f86-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="b6f86-105">Bir yordam çağrısı zaman aşımına olası nedenleri sonsuz bir döngüde olabilir veya *sonsuz bir döngüde*.</span><span class="sxs-lookup"><span data-stu-id="b6f86-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="b6f86-106">Daha fazla bilgi için bkz: [için... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6f86-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="b6f86-107">Sonsuz bir döngüde özel bir durumdur *özyineleme*.</span><span class="sxs-lookup"><span data-stu-id="b6f86-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="b6f86-108">Daha fazla bilgi için bkz: [özyinelemeli yordamlar](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b6f86-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="b6f86-109">**Hata Kimliği:** BC30957</span><span class="sxs-lookup"><span data-stu-id="b6f86-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6f86-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b6f86-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="b6f86-111">Mümkünse, önceki İşlev değerlendirmesi neydi ve zaman aşımına neyin neden olduğunu belirler. Aksi takdirde, bu hata yeniden karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6f86-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="b6f86-112">Hata ayıklayıcı yeniden adım veya sonlandırmak ve hata ayıklamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="b6f86-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f86-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6f86-113">See Also</span></span>  
 [<span data-ttu-id="b6f86-114">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b6f86-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="b6f86-115">Hata ayıklayıcısı ile kodlarda gezinme</span><span class="sxs-lookup"><span data-stu-id="b6f86-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)

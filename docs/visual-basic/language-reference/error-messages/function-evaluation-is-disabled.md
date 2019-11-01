---
title: Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: d004c89b742944622ce45e6a2be8d96116252745
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197572"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="35f2e-102">Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="35f2e-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="35f2e-103">Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı. İşlev değerlendirmesini yeniden etkinleştirmek için tekrar adımla veya hata ayıklamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="35f2e-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="35f2e-104">Visual Studio hata ayıklayıcısında bir ifade bir yordam çağrısını belirtir, ancak başka bir değerlendirme zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="35f2e-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="35f2e-105">Bir yordam çağrısının zaman aşımına yönelik olası nedenleri sonsuz döngü veya sonsuz *döngü*içerir.</span><span class="sxs-lookup"><span data-stu-id="35f2e-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="35f2e-106">Daha fazla bilgi için bkz.... [ Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="35f2e-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="35f2e-107">Sonsuz bir döngünün özel bir durumu *özyinelemedir*.</span><span class="sxs-lookup"><span data-stu-id="35f2e-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="35f2e-108">Daha fazla bilgi için bkz. [özyinelemeli yordamlar](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="35f2e-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="35f2e-109">**Hata kimliği:** BC30957</span><span class="sxs-lookup"><span data-stu-id="35f2e-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35f2e-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="35f2e-110">To correct this error</span></span>  
  
1. <span data-ttu-id="35f2e-111">Mümkünse, önceki işlev değerlendirmesinin ne olduğunu ve bunun neden zaman aşımına uğramadığını saptayın. Aksi takdirde, bu hatayla yeniden karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35f2e-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2. <span data-ttu-id="35f2e-112">Hata ayıklayıcıyı yeniden deneyin ya da Terminate ve hata ayıklamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="35f2e-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f2e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35f2e-113">See also</span></span>

- [<span data-ttu-id="35f2e-114">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="35f2e-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="35f2e-115">Hata Ayıklayıcısı ile Kodlarda gezinme</span><span class="sxs-lookup"><span data-stu-id="35f2e-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)

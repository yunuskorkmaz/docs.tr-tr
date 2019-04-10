---
title: Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: bc4d05e52434cf62fa90671d29b407c83114b5d2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315783"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="2cd51-102">Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="2cd51-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="2cd51-103">Bir önceki İşlev değerlendirmesi zaman aşımına uğradığından İşlev değerlendirmesi devre dışı bırakıldı. İşlev değerlendirmesi yeniden etkinleştirmek için adım yeniden veya hata ayıklamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="2cd51-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="2cd51-104">Visual Studio hata ayıklayıcı bir yordam çağrısı bir ifade belirtir, ancak başka bir değerlendirme zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2cd51-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="2cd51-105">Bir yordam çağrısı zaman aşımına olası nedenleri sonsuz bir döngü olabilir veya *sonsuz bir döngüye*.</span><span class="sxs-lookup"><span data-stu-id="2cd51-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="2cd51-106">Daha fazla bilgi için [için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2cd51-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="2cd51-107">Sonsuz bir döngüye özel bir durumdur *özyineleme*.</span><span class="sxs-lookup"><span data-stu-id="2cd51-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="2cd51-108">Daha fazla bilgi için [özyinelemeli yordamlar](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2cd51-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="2cd51-109">**Hata Kimliği:** BC30957</span><span class="sxs-lookup"><span data-stu-id="2cd51-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2cd51-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2cd51-110">To correct this error</span></span>  
  
1. <span data-ttu-id="2cd51-111">Mümkünse, önceki İşlev değerlendirmesi ne olduğunu ve ne zaman aşımı nedeniyle belirler. Aksi takdirde, bu hatayla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cd51-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2. <span data-ttu-id="2cd51-112">Hata ayıklayıcıyı yeniden adım veya sonlandırır ve hata ayıklamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="2cd51-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd51-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cd51-113">See also</span></span>

- [<span data-ttu-id="2cd51-114">Visual Studio'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2cd51-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="2cd51-115">Hata Ayıklayıcısı ile Kodlarda gezinme</span><span class="sxs-lookup"><span data-stu-id="2cd51-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)

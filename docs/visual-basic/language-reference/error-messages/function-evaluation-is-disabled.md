---
description: 'Şu konuda daha fazla bilgi edinin: BC30957: önceki bir işlev değerlendirmesi zaman aşımına uğradığından Işlev değerlendirmesi devre dışı bırakıldı'
title: Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 32e4b460a0334a542d59091bfc0b9a2337fdd089
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796190"
---
# <a name="bc30957-function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="158b1-103">BC30957: önceki bir işlev değerlendirmesi zaman aşımına uğradığından Işlev değerlendirmesi devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="158b1-103">BC30957: Function evaluation is disabled because a previous function evaluation timed out</span></span>

<span data-ttu-id="158b1-104">Önceki bir işlev değerlendirmesi zaman aşımına uğradığından işlev değerlendirmesi devre dışı bırakıldı. İşlev değerlendirmesini yeniden etkinleştirmek için tekrar adımla veya hata ayıklamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="158b1-104">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>

 <span data-ttu-id="158b1-105">Visual Studio hata ayıklayıcısında bir ifade bir yordam çağrısını belirtir, ancak başka bir değerlendirme zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="158b1-105">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>

 <span data-ttu-id="158b1-106">Bir yordam çağrısının zaman aşımına yönelik olası nedenleri sonsuz döngü veya sonsuz *döngü* içerir.</span><span class="sxs-lookup"><span data-stu-id="158b1-106">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="158b1-107">Daha fazla bilgi için bkz.... [ Sonraki Ifade](../statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="158b1-107">For more information, see [For...Next Statement](../statements/for-next-statement.md).</span></span>

 <span data-ttu-id="158b1-108">Sonsuz bir döngünün özel bir durumu *özyinelemedir*.</span><span class="sxs-lookup"><span data-stu-id="158b1-108">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="158b1-109">Daha fazla bilgi için bkz. [özyinelemeli yordamlar](../../programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="158b1-109">For more information, see [Recursive Procedures](../../programming-guide/language-features/procedures/recursive-procedures.md).</span></span>

 <span data-ttu-id="158b1-110">**Hata kimliği:** BC30957</span><span class="sxs-lookup"><span data-stu-id="158b1-110">**Error ID:** BC30957</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="158b1-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="158b1-111">To correct this error</span></span>

1. <span data-ttu-id="158b1-112">Mümkünse, önceki işlev değerlendirmesinin ne olduğunu ve bunun neden zaman aşımına uğramadığını saptayın. Aksi takdirde, bu hatayla yeniden karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="158b1-112">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>

2. <span data-ttu-id="158b1-113">Hata ayıklayıcıyı yeniden deneyin ya da Terminate ve hata ayıklamayı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="158b1-113">Either step the debugger again, or terminate and restart debugging.</span></span>

## <a name="see-also"></a><span data-ttu-id="158b1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="158b1-114">See also</span></span>

- [<span data-ttu-id="158b1-115">Visual Studio'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="158b1-115">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="158b1-116">Hata Ayıklayıcısı ile Kodlarda gezinme</span><span class="sxs-lookup"><span data-stu-id="158b1-116">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)

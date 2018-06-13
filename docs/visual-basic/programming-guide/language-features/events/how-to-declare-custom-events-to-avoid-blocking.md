---
title: 'Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 3cb66aed71195d2fd2335fbd59cc499b3dbf808e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646932"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="55f41-102">Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55f41-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="55f41-103">Bu bir olay işleyicisi değil sonraki olay işleyicileri engelle önemli olduğu durumlarda bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="55f41-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="55f41-104">Özel olaylar, olay işleyicileri zaman uyumsuz olarak çağırmak olay izin verin.</span><span class="sxs-lookup"><span data-stu-id="55f41-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="55f41-105">Varsayılan olarak, yedekleme deposu için bir olay bildirimi seri olarak tüm olay işleyicileri birleştiren bir çok noktaya yayın temsilci alandır.</span><span class="sxs-lookup"><span data-stu-id="55f41-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="55f41-106">Bu, bir işleyici tamamlanması uzun sürüyorsa, işlem tamamlanana kadar diğer işleyicilerin engellediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="55f41-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="55f41-107">(Uyum gösteren olay işleyicileri hiçbir zaman uzun veya olası engelleme işlemleri gerçekleştirmeniz gerekir.)</span><span class="sxs-lookup"><span data-stu-id="55f41-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="55f41-108">Visual Basic sağlar olayları varsayılan uygulaması kullanmak yerine özel bir olay olay işleyicileri yürütülecek zaman uyumsuz olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f41-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55f41-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="55f41-109">Example</span></span>  
 <span data-ttu-id="55f41-110">Bu örnekte, `AddHandler` erişimci ekler her işleyicisi için temsilci `Click` olaya bir <xref:System.Collections.ArrayList> depolanan `EventHandlerList` alan.</span><span class="sxs-lookup"><span data-stu-id="55f41-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="55f41-111">Ne zaman, başlatır kod `Click` olayı `RaiseEvent` erişimci tüm olay işleyici temsilcileri kullanarak zaman uyumsuz olarak çağırır <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55f41-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="55f41-112">Bu yöntem, bir çalışan iş parçacığı üzerinde her işleyiciyi çağırır ve işleyicileri birbirine engellemek için hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="55f41-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="55f41-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55f41-113">See Also</span></span>  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [<span data-ttu-id="55f41-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="55f41-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="55f41-115">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="55f41-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)

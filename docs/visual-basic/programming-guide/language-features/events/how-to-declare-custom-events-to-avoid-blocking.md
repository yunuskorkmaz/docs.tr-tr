---
title: 'Nasıl yapılır: (Visual Basic) engellemekten Kaçınacak şekilde özel olayları bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 6eea47ea2c8aee697eb34ca904dad22ca88e6ce4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051903"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="9ce49-102">Nasıl yapılır: (Visual Basic) engellemekten Kaçınacak şekilde özel olayları bildirme</span><span class="sxs-lookup"><span data-stu-id="9ce49-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="9ce49-103">Sonraki olay işleyicileri engelleme yapmadığından bu bir olay işleyicisi önemli olduğunda bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="9ce49-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="9ce49-104">Özel olaylar, olay, olay işleyicileri zaman uyumsuz olarak aramak izin verin.</span><span class="sxs-lookup"><span data-stu-id="9ce49-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="9ce49-105">Varsayılan olarak, bir olay bildirimi için yedekleme depolama alanı, tüm olay işleyicilerine seri olarak birleştiren çok noktaya yayın bir temsilcidir.</span><span class="sxs-lookup"><span data-stu-id="9ce49-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="9ce49-106">Bu, bir işleyici tamamlanması uzun sürerse, işlem tamamlanana kadar diğer işleyicilerin engellediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9ce49-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="9ce49-107">(Uyum gösteren olay işleyicileri hiçbir zaman uzun veya olası engelleme işlemleri gerçekleştirmeniz gerekir.)</span><span class="sxs-lookup"><span data-stu-id="9ce49-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="9ce49-108">Visual Basic sağlayan olaylar varsayılan uygulamasını kullanmak yerine, olay işleyicileri zaman uyumsuz olarak yürütmek için bir özel olay kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ce49-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce49-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ce49-109">Example</span></span>  
 <span data-ttu-id="9ce49-110">Bu örnekte, `AddHandler` erişimci ekliyor her işleyicisi için temsilci `Click` olayına bir <xref:System.Collections.ArrayList> depolanan `EventHandlerList` alan.</span><span class="sxs-lookup"><span data-stu-id="9ce49-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="9ce49-111">Harekete geçirirse kod `Click` olay `RaiseEvent` erişimci tüm olay işleyicisi temsilcileri kullanarak zaman uyumsuz olarak çağırır <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9ce49-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="9ce49-112">Bu yöntem, her bir iş parçacığı işleyicisini çağırır ve işleyicileri birbirine engellemek için hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ce49-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="9ce49-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ce49-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="9ce49-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="9ce49-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="9ce49-115">Nasıl yapılır: Bellekten kazanacak şekilde özel olayları bildirme</span><span class="sxs-lookup"><span data-stu-id="9ce49-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)

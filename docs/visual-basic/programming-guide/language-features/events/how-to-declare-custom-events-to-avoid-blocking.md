---
title: 'Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a9f9529d468a036d81c4e436429cbdb3207efd6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405163"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="26299-102">Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26299-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="26299-103">Bir olay işleyicisinin sonraki olay işleyicilerini engellemediğinden çok önemli olduğu durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="26299-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="26299-104">Özel olaylar olayın olay işleyicilerini zaman uyumsuz olarak çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="26299-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="26299-105">Varsayılan olarak, bir olay bildirimi için yedekleme depolama alanı, tüm olay işleyicilerini tamamen birleştiren bir çok noktaya yayın temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="26299-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="26299-106">Bu, bir işleyicinin tamamlanması uzun zaman alıyorsa, diğer işleyicileri tamamlanana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="26299-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="26299-107">(İyi davranmış olay işleyicileri asla uzun veya olası engelleme işlemleri gerçekleştirmemelidir.)</span><span class="sxs-lookup"><span data-stu-id="26299-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="26299-108">Visual Basic tarafından sağlanan varsayılan olay uygulamasını kullanmak yerine, olay işleyicilerini zaman uyumsuz olarak yürütmek için özel bir olay kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26299-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26299-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="26299-109">Example</span></span>  
 <span data-ttu-id="26299-110">Bu örnekte, erişimci, `AddHandler` olayın her işleyicisine ait temsilciyi `Click` <xref:System.Collections.ArrayList> alanında depolanan öğesine ekler `EventHandlerList` .</span><span class="sxs-lookup"><span data-stu-id="26299-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="26299-111">Kod olayı harekete geçirirse `Click` , `RaiseEvent` erişimci yöntemini kullanarak tüm olay işleyicisi temsilcilerinizi zaman uyumsuz olarak çağırır <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="26299-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="26299-112">Bu yöntem bir çalışan iş parçacığında her işleyiciyi çağırır ve hemen döndürür, bu nedenle işleyiciler birbirini engelleyemez.</span><span class="sxs-lookup"><span data-stu-id="26299-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="26299-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26299-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="26299-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="26299-114">Events</span></span>](index.md)
- [<span data-ttu-id="26299-115">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="26299-115">How to: Declare Custom Events To Conserve Memory</span></span>](how-to-declare-custom-events-to-conserve-memory.md)

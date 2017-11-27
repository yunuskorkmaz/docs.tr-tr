---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a><span data-ttu-id="bdebe-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="bdebe-102">AutoResetEvent</span></span>
<span data-ttu-id="bdebe-103"><xref:System.Threading.AutoResetEvent> Sınıfı işaret, tek bir bekleyen iş parçacığı bırakılıyor sonra olduğunda otomatik olarak sıfırlar yerel bekleme tanıtıcısı olayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bdebe-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="bdebe-104">Bu sınıf temel sınıfı olan özel bir durum gösteren <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="bdebe-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="bdebe-105">Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) kullanım ve otomatik sıfırlama olayları özelliklerini kavramsal belgeler.</span><span class="sxs-lookup"><span data-stu-id="bdebe-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="bdebe-106">Bir <xref:System.Threading.AutoResetEvent> nesne otomatik olarak sıfırlanır çok işaret olmayan sistem tarafından tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="bdebe-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="bdebe-107">İş parçacığı bekleyen olay nesnenin durumu iş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="bdebe-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="bdebe-108"><xref:System.Threading.AutoResetEvent>Win32 öğesine karşılık gelen `CreateEvent` çağrısı, belirtme `false` için `bManualReset` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="bdebe-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="bdebe-109">Kullanan bir örnek <xref:System.Threading.AutoResetEvent>, bkz: [İzleyici](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="bdebe-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdebe-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bdebe-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="bdebe-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="bdebe-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="bdebe-112">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdebe-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="bdebe-113">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="bdebe-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="bdebe-114">Bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="bdebe-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)

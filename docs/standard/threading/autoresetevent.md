---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ab06993eed4b39746875a6ef3ebfad5edbd2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581709"
---
# <a name="autoresetevent"></a><span data-ttu-id="a520f-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="a520f-102">AutoResetEvent</span></span>
<span data-ttu-id="a520f-103"><xref:System.Threading.AutoResetEvent> Sınıfı işaret, tek bir bekleyen iş parçacığı bırakılıyor sonra olduğunda otomatik olarak sıfırlar yerel bekleme tanıtıcısı olayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a520f-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="a520f-104">Bu sınıf temel sınıfı olan özel bir durum gösteren <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="a520f-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="a520f-105">Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) kullanım ve otomatik sıfırlama olayları özelliklerini kavramsal belgeler.</span><span class="sxs-lookup"><span data-stu-id="a520f-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="a520f-106">Bir <xref:System.Threading.AutoResetEvent> nesne otomatik olarak sıfırlanır çok işaret olmayan sistem tarafından tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="a520f-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="a520f-107">İş parçacığı bekleyen olay nesnenin durumu iş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="a520f-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="a520f-108"><xref:System.Threading.AutoResetEvent> Win32 öğesine karşılık gelen `CreateEvent` çağrısı, belirtme `false` için `bManualReset` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a520f-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="a520f-109">Kullanan bir örnek <xref:System.Threading.AutoResetEvent>, bkz: [İzleyici](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="a520f-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a520f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a520f-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="a520f-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="a520f-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="a520f-112">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a520f-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="a520f-113">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a520f-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="a520f-114">Bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="a520f-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)

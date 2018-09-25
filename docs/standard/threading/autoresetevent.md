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
ms.openlocfilehash: 38efbe0ecd88c02752d610de4b1eec8b62eca1f8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46937557"
---
# <a name="autoresetevent"></a><span data-ttu-id="46080-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="46080-102">AutoResetEvent</span></span>
<span data-ttu-id="46080-103"><xref:System.Threading.AutoResetEvent> Sınıf sinyal, tek bir bekleyen iş parçacığı bırakılıyor sonra otomatik olarak sıfırlanır bir yerel bekleme tanıtıcısı olayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46080-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="46080-104">Bu sınıfın temel sınıfının, özel bir durum temsil <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="46080-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="46080-105">Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) kullanın ve otomatik sıfırlama olayları özellikleri için kavramsal belgelerde.</span><span class="sxs-lookup"><span data-stu-id="46080-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="46080-106">Bir <xref:System.Threading.AutoResetEvent> nesne otomatik olarak sıfırlanır için verilmemiş sistem tarafından tek bir bekleyen iş parçacığı piyasaya sürüldükten sonra.</span><span class="sxs-lookup"><span data-stu-id="46080-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="46080-107">İş parçacığı bekliyorsanız, olay nesnenin durumu sinyal kalır.</span><span class="sxs-lookup"><span data-stu-id="46080-107">If no threads are waiting, the event object's state remains signaled.</span></span>
  
 <span data-ttu-id="46080-108">Kullanan bir örnek için <xref:System.Threading.AutoResetEvent>, bkz: <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="46080-108">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46080-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46080-109">See also</span></span>

- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Monitor>  
- [<span data-ttu-id="46080-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="46080-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [<span data-ttu-id="46080-111">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="46080-111">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="46080-112">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="46080-112">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="46080-113">Bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="46080-113">Wait Handles</span></span>](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)

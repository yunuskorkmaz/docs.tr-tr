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
ms.openlocfilehash: c1785ce223f0dcd4da7ea6ef9fa3a3e897a39dca
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143524"
---
# <a name="autoresetevent"></a><span data-ttu-id="aed7b-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="aed7b-102">AutoResetEvent</span></span>
<span data-ttu-id="aed7b-103"><xref:System.Threading.AutoResetEvent> Sınıf sinyal, tek bir bekleyen iş parçacığı bırakılıyor sonra otomatik olarak sıfırlanır bir yerel bekleme tanıtıcısı olayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aed7b-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="aed7b-104">Bu sınıfın temel sınıfının, özel bir durum temsil <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="aed7b-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="aed7b-105">Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) kullanın ve otomatik sıfırlama olayları özellikleri için kavramsal belgelerde.</span><span class="sxs-lookup"><span data-stu-id="aed7b-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="aed7b-106">Bir <xref:System.Threading.AutoResetEvent> nesne otomatik olarak sıfırlanır için verilmemiş sistem tarafından tek bir bekleyen iş parçacığı piyasaya sürüldükten sonra.</span><span class="sxs-lookup"><span data-stu-id="aed7b-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="aed7b-107">İş parçacığı bekliyorsanız, olay nesnenin durumu sinyal kalır.</span><span class="sxs-lookup"><span data-stu-id="aed7b-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="aed7b-108"><xref:System.Threading.AutoResetEvent> Win32 öğesine karşılık gelen `CreateEvent` belirleme çağrısında `false` için `bManualReset` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="aed7b-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="aed7b-109">Kullanan bir örnek için <xref:System.Threading.AutoResetEvent>, bkz: <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="aed7b-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed7b-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aed7b-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="aed7b-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="aed7b-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="aed7b-112">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="aed7b-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="aed7b-113">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="aed7b-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="aed7b-114">Bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="aed7b-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)

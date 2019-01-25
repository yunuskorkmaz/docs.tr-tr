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
ms.openlocfilehash: 70af739bdb90a70a1319354b4964c261e432912b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729963"
---
# <a name="autoresetevent"></a><span data-ttu-id="7bfd3-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="7bfd3-102">AutoResetEvent</span></span>
<span data-ttu-id="7bfd3-103"><xref:System.Threading.AutoResetEvent> Sınıf sinyal, tek bir bekleyen iş parçacığı bırakılıyor sonra otomatik olarak sıfırlanır bir yerel bekleme tanıtıcısı olayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7bfd3-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="7bfd3-104">Bu sınıfın temel sınıfının, özel bir durum temsil <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="7bfd3-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="7bfd3-105">Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) kullanın ve otomatik sıfırlama olayları özellikleri için kavramsal belgelerde.</span><span class="sxs-lookup"><span data-stu-id="7bfd3-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="7bfd3-106">Bir <xref:System.Threading.AutoResetEvent> nesne otomatik olarak sıfırlanır için verilmemiş sistem tarafından tek bir bekleyen iş parçacığı piyasaya sürüldükten sonra.</span><span class="sxs-lookup"><span data-stu-id="7bfd3-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="7bfd3-107">İş parçacığı bekliyorsanız, olay nesnenin durumu sinyal kalır.</span><span class="sxs-lookup"><span data-stu-id="7bfd3-107">If no threads are waiting, the event object's state remains signaled.</span></span>
  
 <span data-ttu-id="7bfd3-108">Kullanan bir örnek için <xref:System.Threading.AutoResetEvent>, bkz: <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="7bfd3-108">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfd3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bfd3-109">See also</span></span>

- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="7bfd3-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="7bfd3-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [<span data-ttu-id="7bfd3-111">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="7bfd3-111">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="7bfd3-112">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7bfd3-112">Threading</span></span>](index.md)

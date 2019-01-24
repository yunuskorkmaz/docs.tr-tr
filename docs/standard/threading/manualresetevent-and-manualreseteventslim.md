---
title: ManualResetEvent ve ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864c39aa6673537d66d8402896bce5b4fa92e5ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602449"
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="3d84b-102">ManualResetEvent ve ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="3d84b-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="3d84b-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Sınıf işareti verilen sonra el ile sıfırlamanız gerekir bir yerel bekleme tanıtıcısı olayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d84b-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="3d84b-104">Bu sınıfın temel sınıfının, özel bir durum temsil <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d84b-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3d84b-105">Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) el ile özellikleri ve kullanmak için kavramsal belgelerde olayların sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="3d84b-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="3d84b-106">A <xref:System.Threading.ManualResetEvent> nesne kadar sinyal kalır, <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3d84b-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="3d84b-107">Nesnenin durumu sinyal sırada iş parçacığı veya bu sinyal sonra olay beklemek iş parçacığı beklenirken, herhangi bir sayı serbest bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d84b-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span>
  
 <span data-ttu-id="3d84b-108">İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> bekleme süresini çok kısa olması beklenir ve olay, bir işlem sınırını aşan değil zamanı daha iyi performans için sınıf.</span><span class="sxs-lookup"><span data-stu-id="3d84b-108">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="3d84b-109"><xref:System.Threading.ManualResetEventSlim> Olayın sinyal haline beklerken kısa bir süre için dönen meşgul kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d84b-109"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="3d84b-110">Bekleme süresini kısa olduğunda dönme beklemeden çok daha düşük maliyetli bekleme tanıtıcıları kullanılarak olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d84b-110">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="3d84b-111">Ancak, olay belirli bir zaman döneminde sinyal haline değil <xref:System.Threading.ManualResetEventSlim> resorts normal olay işleyici bekleyin.</span><span class="sxs-lookup"><span data-stu-id="3d84b-111">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d84b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d84b-112">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="3d84b-113">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="3d84b-113">AutoResetEvent</span></span>](autoresetevent.md)
- [<span data-ttu-id="3d84b-114">SpinWait</span><span class="sxs-lookup"><span data-stu-id="3d84b-114">SpinWait</span></span>](spinwait.md)
- [<span data-ttu-id="3d84b-115">Semaphore ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="3d84b-115">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)
- [<span data-ttu-id="3d84b-116">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="3d84b-116">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [<span data-ttu-id="3d84b-117">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="3d84b-117">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="3d84b-118">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d84b-118">Threading</span></span>](index.md)

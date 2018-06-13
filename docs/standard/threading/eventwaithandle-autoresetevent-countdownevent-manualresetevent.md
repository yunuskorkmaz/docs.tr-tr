---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 543853f581436a5fb7e5c897012b99bef20dc289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582956"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="5d7b3-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="5d7b3-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="5d7b3-103">Olay bekleme tanıtıcıları etkinlikleri birbirine sinyal ve birbirlerinin sinyalleri bekleyen eşitlemek için iş parçacığı izin verir.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="5d7b3-104">Bu eşitleme olaylar üzerinde Win32 bekleme tanıtıcıları tabanlı ve iki türlerine ayrılabilir: da otomatik olarak işaret sıfırlanır ve da el ile sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="5d7b3-105">Olay bekleme tanıtıcıları, birçok aynı eşitleme senaryolarda kullanışlıdır <xref:System.Threading.Monitor> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="5d7b3-106">Olay bekleme tanıtıcıları daha kolay genellikle <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> yöntemleri ve sinyal üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="5d7b3-107">İzleyicileri uygulama etki alanı için yerel ise adlandırılmış olay bekleme tanıtıcıları etkinlikleri uygulama etki alanları ve işlemler arasında eşitlemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d7b3-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5d7b3-108">In This Section</span></span>  
 [<span data-ttu-id="5d7b3-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="5d7b3-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="5d7b3-110"><xref:System.Threading.EventWaitHandle> Sınıfı temsil edebilen ya da otomatik veya el ile sıfırlama olayları ve yerel ya da olaylar veya sistem olayları adlı.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="5d7b3-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="5d7b3-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="5d7b3-112"><xref:System.Threading.AutoResetEvent> Sınıfı türer <xref:System.Threading.EventWaitHandle> ve otomatik olarak sıfırlar yerel bir olayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="5d7b3-113">ManualResetEvent ve ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="5d7b3-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="5d7b3-114"><xref:System.Threading.ManualResetEvent> Sınıfı türer <xref:System.Threading.EventWaitHandle> ve el ile sıfırlamanız gerekir yerel bir olayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="5d7b3-115"><xref:System.Threading.ManualResetEventSlim> Aynı işlem içindeki olaylar için kullanılan basit ve hızlı bir sürüm bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="5d7b3-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="5d7b3-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="5d7b3-117"><xref:System.Threading.CountdownEvent> Sınıfı kullanır bekleme tanıtıcıları kodda çatalı/JOIN paralellik desenlerini uygulama için basitleştirilmiş bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5d7b3-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5d7b3-118">Related Sections</span></span>  
 [<span data-ttu-id="5d7b3-119">Bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="5d7b3-119">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="5d7b3-120"><xref:System.Threading.WaitHandle> Sınıf için temel sınıfı olan <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, ve <xref:System.Threading.Mutex> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="5d7b3-121">Statik yöntemler gibi içeren <xref:System.Threading.WaitHandle.SignalAndWait%2A> ve <xref:System.Threading.WaitHandle.WaitAll%2A> bekleme tanıtıcıları tüm türleri ile çalışırken yararlı olan.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7b3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d7b3-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="5d7b3-123">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="5d7b3-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="5d7b3-124">Yönetilen İş Parçacığı Oluşturma Temelleri</span><span class="sxs-lookup"><span data-stu-id="5d7b3-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)

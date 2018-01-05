---
title: "İş Parçacıklarını Zamanlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6bb715c11cc0d9b07e4ea8805ace7680ca92097c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="scheduling-threads"></a><span data-ttu-id="cf206-102">İş Parçacıklarını Zamanlama</span><span class="sxs-lookup"><span data-stu-id="cf206-102">Scheduling Threads</span></span>
<span data-ttu-id="cf206-103">Her iş parçacığı kendisine atanmış bir iş parçacığı önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="cf206-103">Every thread has a thread priority assigned to it.</span></span> <span data-ttu-id="cf206-104">Ortak dil çalışma zamanı içinde oluşturulan iş parçacığı başlangıçta önceliğini atanan **ThreadPriority.Normal**.</span><span class="sxs-lookup"><span data-stu-id="cf206-104">Threads created within the common language runtime are initially assigned the priority of **ThreadPriority.Normal**.</span></span> <span data-ttu-id="cf206-105">Çalışma zamanı dışında oluşturulan iş parçacıklarını yönetilen ortam girilen önce sahip oldukları öncelik korur.</span><span class="sxs-lookup"><span data-stu-id="cf206-105">Threads created outside the runtime retain the priority they had before they entered the managed environment.</span></span> <span data-ttu-id="cf206-106">Almak veya herhangi bir iş parçacığı ile önceliğini ayarlamak **Thread.Priority** özelliği.</span><span class="sxs-lookup"><span data-stu-id="cf206-106">You can get or set the priority of any thread with the **Thread.Priority** property.</span></span>  
  
 <span data-ttu-id="cf206-107">İş parçacığı kendi önceliği temelinde yürütme için zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="cf206-107">Threads are scheduled for execution based on their priority.</span></span> <span data-ttu-id="cf206-108">İş parçacığı içinde çalışma zamanı yürütme olsa bile, tüm iş parçacıklarının işlemci zaman dilimi işletim sistemi tarafından atanır.</span><span class="sxs-lookup"><span data-stu-id="cf206-108">Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.</span></span> <span data-ttu-id="cf206-109">İş parçacığı yürütüldüğü sırayı belirlemek için kullanılan zamanlama algoritması ayrıntılarını her işletim sistemiyle değişir.</span><span class="sxs-lookup"><span data-stu-id="cf206-109">The details of the scheduling algorithm used to determine the order in which threads are executed varies with each operating system.</span></span> <span data-ttu-id="cf206-110">Bazı işletim sistemlerinde iş parçacığı yüksek önceliği (yürütülebilir. Bu iş parçacıkları) ile her zaman ilk çalışacak şekilde zamanlanır.</span><span class="sxs-lookup"><span data-stu-id="cf206-110">Under some operating systems, the thread with the highest priority (of those threads that can be executed) is always scheduled to run first.</span></span> <span data-ttu-id="cf206-111">Birden çok iş parçacığı aynı önceliğe sahip iş parçacıklarının her iş parçacığı yürütme sabit bir zaman dilimi vererek, bu öncelikle Zamanlayıcı dolaşma tüm varsa.</span><span class="sxs-lookup"><span data-stu-id="cf206-111">If multiple threads with the same priority are all available, the scheduler cycles through the threads at that priority, giving each thread a fixed time slice in which to execute.</span></span> <span data-ttu-id="cf206-112">Yüksek bir önceliği olan bir iş parçacığı çalıştırmak için kullanılabilir olduğu sürece, daha düşük öncelikli iş parçacıklarının yürütmek almamış.</span><span class="sxs-lookup"><span data-stu-id="cf206-112">As long as a thread with a higher priority is available to run, lower priority threads do not get to execute.</span></span> <span data-ttu-id="cf206-113">Belirli bir öncelikte artık runnable iş parçacığı olduğunda Zamanlayıcı sonraki düşük önceliği taşır ve iş parçacığı yürütmesi için öncelikle zamanlar.</span><span class="sxs-lookup"><span data-stu-id="cf206-113">When there are no more runnable threads at a given priority, the scheduler moves to the next lower priority and schedules the threads at that priority for execution.</span></span> <span data-ttu-id="cf206-114">Daha yüksek bir öncelik iş parçacığı runnable olursa, daha düşük öncelikli işler için iş parçacığı etkisiz ve daha yüksek öncelik iş parçacığı bir kez daha yürütmeye izin.</span><span class="sxs-lookup"><span data-stu-id="cf206-114">If a higher priority thread becomes runnable, the lower priority thread is preempted and the higher priority thread is allowed to execute once again.</span></span> <span data-ttu-id="cf206-115">Bir uygulamanın kullanıcı arabiriminde ön ve arka plan arasında taşındıkça tüm, en üstünde, işletim sistemini de iş parçacığı öncelikleri dinamik olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf206-115">On top of all that, the operating system can also adjust thread priorities dynamically as an application's user interface is moved between foreground and background.</span></span> <span data-ttu-id="cf206-116">Diğer işletim sistemleri, farklı bir zamanlama algoritmasıdır kullanmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf206-116">Other operating systems might choose to use a different scheduling algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf206-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf206-117">See Also</span></span>  
 [<span data-ttu-id="cf206-118">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf206-118">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="cf206-119">Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf206-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)

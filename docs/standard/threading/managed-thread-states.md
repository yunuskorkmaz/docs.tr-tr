---
title: "Yönetilen İş Parçacığı Durumları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 956472ef0e3b0bab85a4eb0b5585f1a4d1e0a991
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="managed-thread-states"></a><span data-ttu-id="e6f61-102">Yönetilen İş Parçacığı Durumları</span><span class="sxs-lookup"><span data-stu-id="e6f61-102">Managed Thread States</span></span>
<span data-ttu-id="e6f61-103">Özellik <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> iş parçacığının geçerli durumunu belirten bir bit maskesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6f61-103">The property <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> provides a bit mask that indicates the thread's current state.</span></span> <span data-ttu-id="e6f61-104">Bir iş parçacığı her zaman en az bir olası durumlarda bulunduğu <xref:System.Threading.ThreadState> numaralandırma ve aynı anda birden çok durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6f61-104">A thread is always in at least one of the possible states in the <xref:System.Threading.ThreadState> enumeration, and can be in multiple states at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e6f61-105">İş parçacığı durumu olduğu yalnızca birkaç ilgi senaryoları hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="e6f61-105">Thread state is only of interest in a few debugging scenarios.</span></span> <span data-ttu-id="e6f61-106">Kodunuzu, iş parçacığı etkinliklerini eşitlemek için iş parçacığı durumu hiçbir zaman kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6f61-106">Your code should never use thread state to synchronize the activities of threads.</span></span>  
  
 <span data-ttu-id="e6f61-107">Yönetilen iş parçacığı oluşturduğunuzda, olur <xref:System.Threading.ThreadState.Unstarted> durumu.</span><span class="sxs-lookup"><span data-stu-id="e6f61-107">When you create a managed thread, it is in the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="e6f61-108">İş parçacığı kalan <xref:System.Threading.ThreadState.Unstarted> işletim sistemi tarafından başlatılan bir duruma getirilene kadar belirtin.</span><span class="sxs-lookup"><span data-stu-id="e6f61-108">The thread remains in the <xref:System.Threading.ThreadState.Unstarted> state until it is moved into the started state by the operating system.</span></span> <span data-ttu-id="e6f61-109">Çağırma <xref:System.Threading.Thread.Start%2A> bilmeniz işletim sistemi sağlar iş parçacığı başlatılabilir; iş parçacığı durumu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="e6f61-109">Calling <xref:System.Threading.Thread.Start%2A> lets the operating system know that the thread can be started; it does not change the state of the thread.</span></span>  
  
 <span data-ttu-id="e6f61-110">Yönetilen Ortam girin yönetilmeyen iş parçacığı zaten başlatılmış durumda.</span><span class="sxs-lookup"><span data-stu-id="e6f61-110">Unmanaged threads that enter the managed environment are already in the started state.</span></span> <span data-ttu-id="e6f61-111">Bir iş parçacığı başlatılmış durumda olduğunda, çeşitli eylemleri durumları değiştirmek için neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6f61-111">Once a thread is in the started state, a number of actions can cause it to change states.</span></span> <span data-ttu-id="e6f61-112">Aşağıdaki tabloda karşılık gelen yeni durum birlikte durumunun değişmesine neden eylemleri listeler.</span><span class="sxs-lookup"><span data-stu-id="e6f61-112">The following table lists the actions that cause a change of state, along with the corresponding new state.</span></span>  
  
|<span data-ttu-id="e6f61-113">Eylem</span><span class="sxs-lookup"><span data-stu-id="e6f61-113">Action</span></span>|<span data-ttu-id="e6f61-114">Sonuçta elde edilen yeni durumu</span><span class="sxs-lookup"><span data-stu-id="e6f61-114">Resulting new state</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="e6f61-115">Oluşturucusu <xref:System.Threading.Thread> sınıfı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e6f61-115">The constructor for the <xref:System.Threading.Thread> class is called.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="e6f61-116">Başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6f61-116">Another thread calls <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="e6f61-117">İş parçacığı yanıtlar <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> ve çalışmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="e6f61-117">The thread responds to <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> and starts running.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="e6f61-118">İş parçacığı çağrıları <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6f61-118">The thread calls <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="e6f61-119">İş parçacığı çağrıları <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> başka bir nesne üzerinde.</span><span class="sxs-lookup"><span data-stu-id="e6f61-119">The thread calls <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> on another object.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="e6f61-120">İş parçacığı çağrıları <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> başka bir iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="e6f61-120">The thread calls <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> on another thread.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="e6f61-121">Başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6f61-121">Another thread calls <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.SuspendRequested>|  
|<span data-ttu-id="e6f61-122">İş parçacığı yanıtlaması bir <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> isteği.</span><span class="sxs-lookup"><span data-stu-id="e6f61-122">The thread responds to a <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> request.</span></span>|<xref:System.Threading.ThreadState.Suspended>|  
|<span data-ttu-id="e6f61-123">Başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6f61-123">Another thread calls <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="e6f61-124">Başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6f61-124">Another thread calls <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.AbortRequested>|  
|<span data-ttu-id="e6f61-125">İş parçacığı yanıtlaması bir <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6f61-125">The thread responds to an <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<span data-ttu-id="e6f61-126"><xref:System.Threading.ThreadState.Aborted>, ardından<xref:System.Threading.ThreadState.Stopped></span><span class="sxs-lookup"><span data-stu-id="e6f61-126"><xref:System.Threading.ThreadState.Aborted>, then <xref:System.Threading.ThreadState.Stopped></span></span>|  
  
 <span data-ttu-id="e6f61-127">Çünkü <xref:System.Threading.ThreadState.Running> durumu 0 değerine sahip, bu durum bulmak için bir bit testi yapmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="e6f61-127">Because the <xref:System.Threading.ThreadState.Running> state has a value of 0, it is not possible to perform a bit test to discover this state.</span></span> <span data-ttu-id="e6f61-128">Bunun yerine, aşağıdaki testte (sözde kodu) kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e6f61-128">Instead, the following test (in pseudo-code) can be used:</span></span>  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 <span data-ttu-id="e6f61-129">İş parçacığı genellikle birden fazla belirli bir zamanda durumda.</span><span class="sxs-lookup"><span data-stu-id="e6f61-129">Threads are often in more than one state at any given time.</span></span> <span data-ttu-id="e6f61-130">Örneğin, bir iş parçacığı üzerinde engellenirse bir <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> çağrısı ve başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Abort%2A> aynı o iş parçacığı üzerinde hem de iş parçacığı olacaktır <xref:System.Threading.ThreadState.WaitSleepJoin> ve <xref:System.Threading.ThreadState.AbortRequested> aynı anda durumları.</span><span class="sxs-lookup"><span data-stu-id="e6f61-130">For example, if a thread is blocked on a <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> call and another thread calls <xref:System.Threading.Thread.Abort%2A> on that same thread, the thread will be in both the <xref:System.Threading.ThreadState.WaitSleepJoin> and the <xref:System.Threading.ThreadState.AbortRequested> states at the same time.</span></span> <span data-ttu-id="e6f61-131">Bu durumda, iş parçacığı çağrısı döndürür hemen <xref:System.Threading.Monitor.Wait%2A> veya kesintiye, onu alırsınız <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="e6f61-131">In that case, as soon as the thread returns from the call to <xref:System.Threading.Monitor.Wait%2A> or is interrupted, it will receive the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 <span data-ttu-id="e6f61-132">Bir iş parçacığı bırakır sonra <xref:System.Threading.ThreadState.Unstarted> yapılan bir çağrı sonucunda durum <xref:System.Threading.Thread.Start%2A>, hiçbir şekilde dönebilirsiniz <xref:System.Threading.ThreadState.Unstarted> durumu.</span><span class="sxs-lookup"><span data-stu-id="e6f61-132">Once a thread leaves the <xref:System.Threading.ThreadState.Unstarted> state as the result of a call to <xref:System.Threading.Thread.Start%2A>, it can never return to the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="e6f61-133">Bir iş parçacığı hiçbir zaman ayrılmaz <xref:System.Threading.ThreadState.Stopped> durumu.</span><span class="sxs-lookup"><span data-stu-id="e6f61-133">A thread can never leave the <xref:System.Threading.ThreadState.Stopped> state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f61-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6f61-134">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [<span data-ttu-id="e6f61-135">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e6f61-135">Threading</span></span>](../../../docs/standard/threading/index.md)

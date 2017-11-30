---
title: "Ön Plan ve Arka Plan İş Parçacıklarını Seçme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="f4c03-102">Ön Plan ve Arka Plan İş Parçacıklarını Seçme</span><span class="sxs-lookup"><span data-stu-id="f4c03-102">Foreground and Background Threads</span></span>
<span data-ttu-id="f4c03-103">Yönetilen iş parçacığı, arka plan iş parçacığı ya da bir ön plan iş parçacığı değil.</span><span class="sxs-lookup"><span data-stu-id="f4c03-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="f4c03-104">Arka plan iş parçacıkları bir özel durumla ön plan iş parçacıkları aynı: arka plan iş parçacığı çalıştıran yönetilen yürütme ortamını korumaz.</span><span class="sxs-lookup"><span data-stu-id="f4c03-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="f4c03-105">Tüm ön plan iş parçacıkları (.exe dosyası bir yönetilen derlemesi olduğu) yönetilen bir işlemde durdurulan sonra sistem tüm arka plan iş parçacıkları durdurur ve kapanır.</span><span class="sxs-lookup"><span data-stu-id="f4c03-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4c03-106">Çalışma zamanı işlem kapanmakta olduğundan bir arka plan iş parçacığı durduğunda, iş parçacığı hiçbir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="f4c03-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="f4c03-107">Ancak, ne zaman iş parçacığı durdurulur çünkü <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi bellekten uygulama etki alanı bir <xref:System.Threading.ThreadAbortException> ön ve arka plan iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f4c03-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="f4c03-108">Kullanım <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> özelliğini bir iş parçacığı bir arka plan ya da bir ön plan iş parçacığı olup olmadığını belirlemek veya durumunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f4c03-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="f4c03-109">Bir iş parçacığı bir arka plan iş parçacığı için herhangi bir zamanda ayarlayarak değiştirilebilir kendi <xref:System.Threading.Thread.IsBackground%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="f4c03-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4c03-110">Bir iş parçacığı ön plan veya arka plan durumunu bir iş parçacığı işlenmeyen bir özel durum sonucunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="f4c03-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="f4c03-111">.NET Framework sürüm 2. 0'da, uygulamanın sonlandırılmasıyla ön plan veya arka plan iş parçacığı işlenmeyen bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="f4c03-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="f4c03-112">Bkz: [yönetilen iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="f4c03-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="f4c03-113">Yönetilen iş parçacığı havuzuna ait iş parçacıkları (diğer bir deyişle, iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> özelliği `true`) arka plan iş parçacıkları şunlardır.</span><span class="sxs-lookup"><span data-stu-id="f4c03-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="f4c03-114">Yönetilmeyen koddan yönetilen yürütme ortamını girin tüm iş parçacıklarının arka plan iş parçacığı olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="f4c03-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="f4c03-115">Oluşturma ve yeni bir başlangıç tarafından oluşturulan tüm iş parçacıklarının <xref:System.Threading.Thread> nesne olan varsayılan ön plan iş parçacıkları tarafından.</span><span class="sxs-lookup"><span data-stu-id="f4c03-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="f4c03-116">Bir yuva bağlantısı gibi bir etkinliğini izlemek için bir iş parçacığı kullanırsanız ayarlamanız kendi <xref:System.Threading.Thread.IsBackground%2A> özelliğine `true` böylece iş parçacığı işleminizin sonlandırılıyor gelen engellemez.</span><span class="sxs-lookup"><span data-stu-id="f4c03-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c03-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4c03-117">See Also</span></span>  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>

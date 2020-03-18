---
title: Ön Plan ve Arka Plan İş Parçacıklarını Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 9e93f07b3b84264373db0317919b6ee519c8127c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138047"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="eb7a2-102">Ön Plan ve Arka Plan İş Parçacıklarını Seçme</span><span class="sxs-lookup"><span data-stu-id="eb7a2-102">Foreground and Background Threads</span></span>
<span data-ttu-id="eb7a2-103">Yönetilen iş parçacığı, arka plan iş parçacığı veya ön plan iş parçacığıdır.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="eb7a2-104">Arka plan iş parçacıkları, bir istisna dışında ön plan iş parçacıklarıyla aynıdır: arka plan iş parçacığı yönetilen yürütme ortamını çalışır durumda tutmaz.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="eb7a2-105">Tüm ön plan iş parçacıkları yönetilen bir işlemde durdurulduktan sonra (.exe dosyasının yönetilen bir derleme olduğu yerde), sistem tüm arka plan iş parçacıklarını durdurur ve kapanır.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb7a2-106">İşlem kapandığı için çalışma zamanı arka plan iş parçacığı durduğunda, iş parçacığına özel bir durum atılmaz.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="eb7a2-107">Ancak, <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntem uygulama etki alanını boşalttığı için iş <xref:System.Threading.ThreadAbortException> parçacıkları durdurulduğunda, hem ön plana hem de arka plan iş parçacığına bir a atılır.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="eb7a2-108">İş <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> parçacığının arka plan mı yoksa ön plan iş parçacığı mı olduğunu belirlemek veya durumunu değiştirmek için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="eb7a2-109">Bir iş parçacığı, özelliğini <xref:System.Threading.Thread.IsBackground%2A> . `true`</span><span class="sxs-lookup"><span data-stu-id="eb7a2-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eb7a2-110">Bir iş parçacığının ön plan veya arka plan durumu iş parçacığındaki işlenmemiş bir özel durumun sonucunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="eb7a2-111">.NET Framework sürüm 2.0'da, ön planda veya arka plan iş parçacığında işlenmemiş bir özel durum, uygulamanın sonlandırılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="eb7a2-112">[Yönetilen İş Parçacıklarındaki Özel Durumlara](../../../docs/standard/threading/exceptions-in-managed-threads.md)Bakın.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="eb7a2-113">Yönetilen iş parçacığı havuzuna ait iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> (diğer `true`bir şekilde, özelliği olan iş parçacıkları) arka plan iş parçacıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="eb7a2-114">Yönetilmeyen koddan yönetilen yürütme ortamına giren tüm iş parçacıkları arka plan iş parçacığı olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="eb7a2-115">Yeni <xref:System.Threading.Thread> bir nesne oluşturulup başlatılarak oluşturulan tüm iş parçacıkları varsayılan olarak ön plan iş parçacıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="eb7a2-116">Soket bağlantısı gibi bir etkinliği izlemek için bir iş <xref:System.Threading.Thread.IsBackground%2A> parçacığı `true` kullanıyorsanız, iş parçacığıişleminizin sonlandırmasını engellemeyecek şekilde özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb7a2-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>

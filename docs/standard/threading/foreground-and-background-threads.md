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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dbad5da42f5ed4e03751534a3a183615a9757cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960029"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="4cfa3-102">Ön Plan ve Arka Plan İş Parçacıklarını Seçme</span><span class="sxs-lookup"><span data-stu-id="4cfa3-102">Foreground and Background Threads</span></span>
<span data-ttu-id="4cfa3-103">Yönetilen iş parçacığı, bir arka plan iş parçacığı veya bir ön plan iş parçacığıdır.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="4cfa3-104">Arka plan iş parçacıkları tek bir özel durum içeren ön plan iş parçacıklarıyla aynıdır: arka plan iş parçacığı yönetilen yürütme ortamını çalışır durumda tutar.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="4cfa3-105">Yönetilen bir işlemde (. exe dosyasının yönetilen bir derleme olduğu) tüm ön plan iş parçacıkları durdurulduktan sonra, sistem tüm arka plan iş parçacıklarını durduruyor ve kapatır.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cfa3-106">Çalışma zamanı bir arka plan iş parçacığını durdurduğundan, iş parçacığında hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="4cfa3-107">Ancak, <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> Yöntem uygulama etki alanını kaldırdığından iş parçacıkları durdurulduğunda, hem ön planda <xref:System.Threading.ThreadAbortException> hem de arka plan iş parçacıklarında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="4cfa3-108">Bir iş parçacığının arka plan veya ön plan iş parçacığı olduğunu veya durumunu değiştirmek için özelliğinikullanın.<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4cfa3-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="4cfa3-109">Bir iş parçacığı, <xref:System.Threading.Thread.IsBackground%2A> özelliği olarak `true`ayarlanarak herhangi bir zamanda arka plan iş parçacığına değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4cfa3-110">Bir iş parçacığının ön plan veya arka plan durumu, iş parçacığında işlenmeyen bir özel durumun sonucunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="4cfa3-111">.NET Framework sürüm 2,0 ' de, ön planda veya arka plan iş parçacıklarında işlenmeyen bir özel durum uygulamanın sonlandırmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="4cfa3-112">Bkz. [yönetilen Iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="4cfa3-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="4cfa3-113">Yönetilen iş parçacığı havuzuna ait olan iş parçacıkları (diğer bir deyişle, <xref:System.Threading.Thread.IsThreadPoolThread%2A> `true`özelliği olan iş parçacıkları) arka plan iş parçacığıdır.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="4cfa3-114">Yönetilmeyen koddan yönetilen yürütme ortamına giriş yapan tüm iş parçacıkları arka plan iş parçacıkları olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="4cfa3-115">Yeni <xref:System.Threading.Thread> bir nesne oluşturup başlattıktan sonra oluşturulan tüm iş parçacıkları varsayılan ön plan iş parçacıklarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="4cfa3-116">Yuva bağlantısı gibi bir etkinliği izlemek için bir iş parçacığı kullanıyorsanız, iş parçacığının sonlandırmasını önleyememesi <xref:System.Threading.Thread.IsBackground%2A> için `true` özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cfa3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cfa3-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>

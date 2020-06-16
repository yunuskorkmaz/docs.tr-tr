---
title: Ön Plan ve Arka Plan İş Parçacıklarını Seçme
description: .NET 'teki Thread. IsBackground özelliğini kullanarak bir iş parçacığının arka plan iş parçacığı veya bir ön plan iş parçacığı olup olmadığını belirleme veya değiştirme.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 6cb7a92851728e16f4a317d6c24d072acee72a94
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769047"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="b636b-103">Ön Plan ve Arka Plan İş Parçacıklarını Seçme</span><span class="sxs-lookup"><span data-stu-id="b636b-103">Foreground and Background Threads</span></span>
<span data-ttu-id="b636b-104">Yönetilen iş parçacığı, bir arka plan iş parçacığı veya bir ön plan iş parçacığıdır.</span><span class="sxs-lookup"><span data-stu-id="b636b-104">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="b636b-105">Arka plan iş parçacıkları tek bir özel durum içeren ön plan iş parçacıklarıyla aynıdır: arka plan iş parçacığı yönetilen yürütme ortamını çalışır durumda tutar.</span><span class="sxs-lookup"><span data-stu-id="b636b-105">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="b636b-106">Yönetilen bir işlemde (. exe dosyasının yönetilen bir derleme olduğu) tüm ön plan iş parçacıkları durdurulduktan sonra, sistem tüm arka plan iş parçacıklarını durduruyor ve kapatır.</span><span class="sxs-lookup"><span data-stu-id="b636b-106">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b636b-107">Çalışma zamanı bir arka plan iş parçacığını durdurduğundan, iş parçacığında hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="b636b-107">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="b636b-108">Ancak, yöntem uygulama etki alanını kaldırdığından iş parçacıkları durdurulduğunda, <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> <xref:System.Threading.ThreadAbortException> hem ön planda hem de arka plan iş parçacıklarında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b636b-108">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="b636b-109"><xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>Bir iş parçacığının arka plan veya ön plan iş parçacığı olduğunu veya durumunu değiştirmek için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b636b-109">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="b636b-110">Bir iş parçacığı, özelliği olarak ayarlanarak herhangi bir zamanda arka plan iş parçacığına değiştirilebilir <xref:System.Threading.Thread.IsBackground%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="b636b-110">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b636b-111">Bir iş parçacığının ön plan veya arka plan durumu, iş parçacığında işlenmeyen bir özel durumun sonucunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="b636b-111">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="b636b-112">.NET Framework sürüm 2,0 ' de, ön planda veya arka plan iş parçacıklarında işlenmeyen bir özel durum uygulamanın sonlandırmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b636b-112">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="b636b-113">Bkz. [yönetilen Iş parçacıklarında özel durumlar](exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="b636b-113">See [Exceptions in Managed Threads](exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="b636b-114">Yönetilen iş parçacığı havuzuna ait olan iş parçacıkları (diğer bir deyişle, özelliği olan iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> `true` ) arka plan iş parçacığıdır.</span><span class="sxs-lookup"><span data-stu-id="b636b-114">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="b636b-115">Yönetilmeyen koddan yönetilen yürütme ortamına giriş yapan tüm iş parçacıkları arka plan iş parçacıkları olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="b636b-115">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="b636b-116">Yeni bir nesne oluşturup başlattıktan sonra oluşturulan tüm iş parçacıkları <xref:System.Threading.Thread> varsayılan ön plan iş parçacıklarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="b636b-116">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="b636b-117">Yuva bağlantısı gibi bir etkinliği izlemek için bir iş parçacığı kullanıyorsanız, <xref:System.Threading.Thread.IsBackground%2A> `true` iş parçacığının sonlandırmasını önleyememesi için özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b636b-117">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b636b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b636b-118">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>

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
ms.openlocfilehash: fcedd478ee1eb89c11dc9535b1d2ffe843d0f658
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868543"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="24675-102">Ön Plan ve Arka Plan İş Parçacıklarını Seçme</span><span class="sxs-lookup"><span data-stu-id="24675-102">Foreground and Background Threads</span></span>
<span data-ttu-id="24675-103">Yönetilen iş parçacığı veya bir arka plan iş parçacığı, hem de ön plan iş parçacığı değil.</span><span class="sxs-lookup"><span data-stu-id="24675-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="24675-104">Arka plan iş parçacığı bir özel durumla aynı ön plan iş parçacığı: arka plan iş parçacığı çalıştıran yönetilen yürütme ortamında korumaz.</span><span class="sxs-lookup"><span data-stu-id="24675-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="24675-105">(Burada .exe dosyasını, yönetilen bir derleme adıdır) yönetilen bir işlemde tüm ön plan iş parçacığı üzere durdurduktan sonra sistem tüm arka plan iş parçacığı durdurur ve kapanır.</span><span class="sxs-lookup"><span data-stu-id="24675-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24675-106">İşlem kapatıldığından, çalışma zamanı arka plan iş parçacığı sona erdiğinde, iş parçacığında hiçbir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24675-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="24675-107">Ancak, iş parçacığı durduruldu çünkü <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi kaldırır uygulama etki alanının bir <xref:System.Threading.ThreadAbortException> ön ve arka plan iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24675-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="24675-108">Kullanım <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> özelliği bir iş parçacığı bir arka plan ya da bir ön plan iş parçacığı olup olmadığını belirlemek için ya da kendi durumunu değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="24675-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="24675-109">Bir iş parçacığı bir arka plan iş parçacığı herhangi bir zamanda ayarlayarak değiştirilebilir, <xref:System.Threading.Thread.IsBackground%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="24675-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24675-110">Bir iş parçacığı durumunu ön plan veya arka plan iş parçacığı işlenmeyen bir özel durum sonucunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="24675-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="24675-111">.NET Framework sürüm 2. 0'da, uygulamanın sonlandırılmasıyla ön plan veya arka plan iş parçacığı işlenmeyen bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="24675-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="24675-112">Bkz: [yönetilen iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="24675-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="24675-113">Yönetilen iş parçacığı havuzuna ait iş parçacıkları (diğer bir deyişle, ayarlanmış iş parçacıkları <xref:System.Threading.Thread.IsThreadPoolThread%2A> özelliği `true`) arka plan iş parçacıklarının.</span><span class="sxs-lookup"><span data-stu-id="24675-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="24675-114">Tüm iş parçacıklarını yönetilmeyen koddan yönetilen yürütme ortamında girdiğiniz arka plan iş parçacığı işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="24675-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="24675-115">Tüm iş parçacıkları oluşturma ve yeni bir başlangıç tarafından oluşturulan <xref:System.Threading.Thread> nesne olan varsayılan ön plan iş parçacıkları tarafından.</span><span class="sxs-lookup"><span data-stu-id="24675-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="24675-116">Bir yuva bağlantısı gibi bir etkinliği izlemek için bir iş parçacığı kullanırsanız ayarlayın, <xref:System.Threading.Thread.IsBackground%2A> özelliğini `true` böylece iş parçacığı, işlem sonlandırılıyor gelen engellemez.</span><span class="sxs-lookup"><span data-stu-id="24675-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24675-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24675-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadAbortException>

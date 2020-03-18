---
title: İş parçacıklarını yok etme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: 842ca4ff17f9cbab3a1518d2dea37436c9b23f9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155938"
---
# <a name="destroying-threads"></a><span data-ttu-id="3d2d1-102">İş parçacıklarını yok etme</span><span class="sxs-lookup"><span data-stu-id="3d2d1-102">Destroying threads</span></span>

<span data-ttu-id="3d2d1-103">İş parçacığının yürütülmesini sonlandırmak için genellikle [kooperatif iptal modelini](cancellation-in-managed-threads.md)kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-103">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="3d2d1-104">Bazen bir iş parçacığının kooperatif iptali için tasarlanmadığından, iş parçacığının ortaklaşa durdurulması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-104">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="3d2d1-105">.NET Framework'deki <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntem, yönetilen bir iş parçacığının zorla sonlandırılması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-105">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="3d2d1-106">Çağrı <xref:System.Threading.Thread.Abort%2A>yaptığınızda, Ortak Dil Çalışma <xref:System.Threading.ThreadAbortException> Zamanı hedef iş parçacığına bir atar ve hedef iş parçacığı yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-106">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="3d2d1-107">Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-107">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3d2d1-108">Yöntem <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .NET Core'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-108">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="3d2d1-109">Üçüncü taraf kodunun yürütülmesini .NET Core'da zorla sonlandırmanız gerekiyorsa, bunu ayrı <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>bir işlemde çalıştırın ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-109">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="3d2d1-110">Bir iş parçacığı, yöntemi çağrıldığında yönetilmeyen kodu çalıştırıyorsa, <xref:System.Threading.Thread.Abort%2A> çalışma zamanı onu <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>işaretler.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-110">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3d2d1-111">İş parçacığı yönetilen koda döndüğünde özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-111">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="3d2d1-112">Bir iş parçacığı iptal edildikten sonra yeniden başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-112">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="3d2d1-113">Yöntem <xref:System.Threading.Thread.Abort%2A> iş parçacığının hemen iptal ineneden gelmez, çünkü <xref:System.Threading.ThreadAbortException> hedef iş parçacığı bir `finally` bloktaki rasgele kod tutarlarını yakalayabilir ve yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-113">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="3d2d1-114">İş parçacığı <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> bitene kadar beklemeniz gerekiyorsa arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-114">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="3d2d1-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>iş parçacığı gerçekten yürütmeyi durdurana veya isteğe bağlı bir zaman aşımı aralığı geçene kadar dönmeyen bir engelleme çağrısıdır.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="3d2d1-116">İptal edilen iş parçacığı <xref:System.Threading.Thread.ResetAbort%2A> yöntemi arayabilir veya bir `finally` blokta sınırsız işlem gerçekleştirebilir, bu nedenle bir zaman aşımı belirtmezseniz, beklemenin sona ermesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-116">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="3d2d1-117">Yönteme çağrı beklerken <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> bekleyen iş parçacıkları, '' yi <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>arayan diğer iş parçacıkları tarafından kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-117">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="3d2d1-118">ThreadAbortException işleme</span><span class="sxs-lookup"><span data-stu-id="3d2d1-118">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="3d2d1-119">İş parçacığınızın kendi kodunuzdan arama <xref:System.Threading.Thread.Abort%2A> sonucunda veya iş parçacığının çalıştırıldığı bir uygulama etki alanını boşaltma sı sonucunda<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> (iş parçacığısonlandırmak için <xref:System.Threading.ThreadAbortException> kullanır) olarak, iş `finally` parçacığınızın aşağıdaki kodda gösterildiği gibi bir yan tümcedeki son işlemi işlemesi ve gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-119">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try
{  
    // Code that is executing when the thread is aborted.  
}
catch (ThreadAbortException ex)
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.
}  
// Do not put clean-up code here, because the exception
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="3d2d1-120">Temizleme kodunuz `catch` yan tümcede veya `finally` yan tümcede olmalıdır, çünkü bir <xref:System.Threading.ThreadAbortException> `finally` yan tümcenin sonundaki `catch` sistem tarafından veya `finally` yan tümcenin sonunda yeniden atılır.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-120">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="3d2d1-121"><xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> Yöntemi arayarak sistemin özel durumu yeniden atmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-121">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d2d1-122">Ancak, bunu yalnızca kendi kodunuz . <xref:System.Threading.ThreadAbortException></span><span class="sxs-lookup"><span data-stu-id="3d2d1-122">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d2d1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d2d1-123">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="3d2d1-124">İş Parçacığı ve İş Parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="3d2d1-124">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 986b4dee17c41928327e7b2672d641bbb8b16f1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960085"
---
# <a name="destroying-threads"></a><span data-ttu-id="c8596-102">İş parçacıklarını yok etme</span><span class="sxs-lookup"><span data-stu-id="c8596-102">Destroying threads</span></span>
<span data-ttu-id="c8596-103">Yöntemi <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> , yönetilen bir iş parçacığını kalıcı olarak durdurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8596-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="c8596-104">' İ çağırdığınızda <xref:System.Threading.Thread.Abort%2A>, ortak dil çalışma zamanı hedef iş <xref:System.Threading.ThreadAbortException> parçacığında hedef iş parçacığının yakalayabileceği bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8596-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="c8596-105">Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8596-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8596-106">Bir iş parçacığı <xref:System.Threading.Thread.Abort%2A> yöntemi çağrıldığında yönetilmeyen kodu yürütüp, çalışma zamanı onu <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>işaretler.</span><span class="sxs-lookup"><span data-stu-id="c8596-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c8596-107">Özel durum, iş parçacığı yönetilen koda döndüğünde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8596-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="c8596-108">Bir iş parçacığı iptal edildikten sonra yeniden başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="c8596-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="c8596-109">Yöntemi, iş parçacığı bir `finally` blokta rastgele miktarda kod <xref:System.Threading.ThreadAbortException> yakalayıp yürütebildiğinden, iş parçacığının hemen durmasına neden olmaz. <xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="c8596-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="c8596-110">İş parçacığı sonlanana kadar beklemeniz gerekiyorsa, öğesini çağırabilirsiniz <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c8596-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="c8596-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, iş parçacığı gerçekten yürütmeyi durdurana veya isteğe bağlı bir zaman aşımı aralığı geçtiğinde döndürmeyen bir engelleme çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="c8596-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="c8596-112">Durdurulan iş parçacığı <xref:System.Threading.Thread.ResetAbort%2A> yöntemi çağırabilir veya bir `finally` blokta sınırsız işlem gerçekleştirebilir, bu nedenle bir zaman aşımı belirtmezseniz, bekleme işleminin bitmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="c8596-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="c8596-113">Yöntemine yapılan bir çağrıda bekleyen iş parçacıkları, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> çağıran <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>diğer iş parçacıkları tarafından kesintiye uğratılmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c8596-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="c8596-114">Threadadbortexception işleme</span><span class="sxs-lookup"><span data-stu-id="c8596-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="c8596-115">İş parçacığınızdan, kendi kodunuzun çağrılması <xref:System.Threading.Thread.Abort%2A> veya iş parçacığının çalıştığı bir uygulama etki alanının kaldırılması sonucu olarak (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> iş parçacıklarını sonlandırmak için kullanılır <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ), iş parçacığınızdan işlem yapmanız gerekir ve <xref:System.Threading.ThreadAbortException> , aşağıdaki kodda gösterildiği gibi bir `finally` yan tümcede son işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c8596-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="c8596-116">Temizleme kodunuz `catch` yan tümce `finally` <xref:System.Threading.ThreadAbortException> `finally` veya yan tümcesinde olmalıdır, çünkü yan tümcesinin sonunda sistem tarafından yeniden oluşturulur `finally` veya yan tümce yoksa `catch` yan tümcesinin sonunda.</span><span class="sxs-lookup"><span data-stu-id="c8596-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="c8596-117"><xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> Yöntemini çağırarak sistemin özel durumu yeniden oluşturmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8596-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c8596-118">Bununla birlikte, bunu yalnızca kendi kodunuz ' a neden <xref:System.Threading.ThreadAbortException>olursa yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8596-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8596-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8596-119">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="c8596-120">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8596-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)

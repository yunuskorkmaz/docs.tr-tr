---
title: "İş Parçacıklarını Yok Etme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3bdacb1cc54e3b67a1b4cef4f9fd274e65037faa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="destroying-threads"></a><span data-ttu-id="2af15-102">İş Parçacıklarını Yok Etme</span><span class="sxs-lookup"><span data-stu-id="2af15-102">Destroying Threads</span></span>
<span data-ttu-id="2af15-103"><xref:System.Threading.Thread.Abort%2A> Yöntemi yönetilen iş parçacığı kalıcı olarak durdurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2af15-103">The <xref:System.Threading.Thread.Abort%2A> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="2af15-104">Çağırdığınızda <xref:System.Threading.Thread.Abort%2A>, ortak dil çalışma zamanı oluşturur bir <xref:System.Threading.ThreadAbortException> hedef iş parçacığı yakalayabilir hedef iş parçacığında.</span><span class="sxs-lookup"><span data-stu-id="2af15-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="2af15-105">Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2af15-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2af15-106">Bir iş parçacığı çalıştırıldığında yönetilmeyen ne zaman kod kendi <xref:System.Threading.Thread.Abort%2A> yöntemi çağrıldığında, çalışma zamanı Bu işaretler <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2af15-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2af15-107">İş parçacığı için yönetilen kodu döndürdüğünde özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="2af15-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="2af15-108">Bir iş parçacığı durduruldu sonra yeniden başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2af15-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="2af15-109"><xref:System.Threading.Thread.Abort%2A> Yöntemi neden olmaz hemen durdurmak iş parçacığı hedef iş parçacığı yakalayabilir çünkü <xref:System.Threading.ThreadAbortException> ve kodda rasgele miktarda yürütme bir `finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="2af15-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="2af15-110">Çağırabilirsiniz <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> iş parçacığı sona erinceye kadar bekleyin gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="2af15-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="2af15-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>iş parçacığı yürütülmesi gerçekte durdurulana kadar döndürmeyen bir engelleme çağrısı veya bir isteğe bağlı zaman aşımı aralığı geçti.</span><span class="sxs-lookup"><span data-stu-id="2af15-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="2af15-112">Durdurulan iş parçacığı çağırabilirsiniz <xref:System.Threading.Thread.ResetAbort%2A> yöntemi veya sınırsız yönlendirilmeden bir `finally` engellemek için zaman aşımı belirtmezseniz beklemeyi sona erdirmek için kesin değildir.</span><span class="sxs-lookup"><span data-stu-id="2af15-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="2af15-113">Çağrı sırasında bekleyen iş parçacığı <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemini çağıran başka bir iş parçacığı tarafından kesintiye <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2af15-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="2af15-114">ThreadAbortException işleme</span><span class="sxs-lookup"><span data-stu-id="2af15-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="2af15-115">İş parçacığı, arama sonucu olarak da durdurulacak bekliyorsanız <xref:System.Threading.Thread.Abort%2A> kendi kodunuzu veya iş parçacığı çalışıyor uygulama etki alanı kaldırılması sonucunda (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> kullanan <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> iş parçacığı sonlandırmak için), iş parçacığı işlemesi gerekir <xref:System.Threading.ThreadAbortException> ve tüm son yönlendirilmeden bir `finally` aşağıdaki kodda gösterildiği gibi yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="2af15-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="2af15-116">Temizleme kodunuzun olmalıdır `catch` yan tümcesi veya `finally` yan tümcesi, çünkü bir <xref:System.Threading.ThreadAbortException> sonunda sistem tarafından işlenemezse `finally` yan tümcesi veya sonunda `catch` varsa yan tümcesi yok `finally` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="2af15-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="2af15-117">Özel durum gelen yeniden atma çağırarak sistem engelleyebilirsiniz <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2af15-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2af15-118">Ancak, bu yalnızca, kendi kodunuzu neden yapmalısınız <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="2af15-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af15-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2af15-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="2af15-120">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="2af15-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)

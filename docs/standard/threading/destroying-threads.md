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
ms.openlocfilehash: 9a243c95aff77a5de2b3af15542c0bcc44870333
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525699"
---
# <a name="destroying-threads"></a><span data-ttu-id="c8cb2-102">İş parçacıklarını yok etme</span><span class="sxs-lookup"><span data-stu-id="c8cb2-102">Destroying threads</span></span>
<span data-ttu-id="c8cb2-103"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Yöntemi, bir yönetilen iş parçacığı kalıcı olarak durdurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="c8cb2-104">Çağırdığınızda <xref:System.Threading.Thread.Abort%2A>, ortak dil çalışma zamanı bir <xref:System.Threading.ThreadAbortException> hedef iş parçacığı, hedef iş parçacığı yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="c8cb2-105">Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8cb2-106">Bir iş parçacığı yürütülüyorsa yönetilmeyen kod zaman kendi <xref:System.Threading.Thread.Abort%2A> yöntemi çağrıldığında, çalışma zamanı Bu işaretler <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c8cb2-107">İş parçacığı yönetilen koda geri döndüğünde, özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="c8cb2-108">Bir iş parçacığı durduruldu sonra yeniden başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="c8cb2-109"><xref:System.Threading.Thread.Abort%2A> Yöntemi neden olmaz hemen iptal etmek iş parçacığı çünkü hedef iş parçacığı yakalayabilir <xref:System.Threading.ThreadAbortException> ve rastgele miktarda kod yürütme bir `finally` blok.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="c8cb2-110">Çağırabilirsiniz <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> iş parçacığının sona erinceye kadar beklenecek gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="c8cb2-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yürütme iş parçacığını gerçekten bitirene kadar döndürmeyen engelleyici bir çağrıdır veya isteğe bağlı zaman aşımı aralığı geçti.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="c8cb2-112">Durdurulan iş parçacığı çağırabilir <xref:System.Threading.Thread.ResetAbort%2A> yöntemi veya sınırsız yönlendirilmeden bir `finally` engellemek için bir zaman aşımı belirtmezseniz, beklemeyi sona erdirmek için garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="c8cb2-113">Çağırması için bekleyen iş parçacıklarının <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemi çağıran başka iş parçacıklarının engellemelerinden kesintiye <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="c8cb2-114">ThreadAbortException işleme</span><span class="sxs-lookup"><span data-stu-id="c8cb2-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="c8cb2-115">İş parçacığınıza, arama sonucu olarak ya da iptal bekliyorsanız <xref:System.Threading.Thread.Abort%2A> kendi kodunuzu veya iş parçacığı çalıştığı uygulama etki alanı kaldırılması sonucunda (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> kullanır <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> iş parçacıkları sonlandırmak için), kendi iş parçacığı işlemesi gerekir <xref:System.Threading.ThreadAbortException> ve herhangi bir son işlem olarak bir `finally` yan tümcesi, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="c8cb2-116">Temizleme kodunuzun olmalıdır `catch` yan tümcesi veya `finally` yan tümcesi, çünkü bir <xref:System.Threading.ThreadAbortException> sonunda, sistem tarafından tekrar fırlatılan `finally` yan tümcesi ya da sonunda `catch` varsa yan tümcesi yok `finally` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="c8cb2-117">Özel durum gelen yeniden atma çağırarak sistem engelleyebilir <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c8cb2-118">Ancak, bu yalnızca, neden kendi kodunuzu yapmalısınız <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8cb2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8cb2-119">See also</span></span>

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- [<span data-ttu-id="c8cb2-120">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8cb2-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)

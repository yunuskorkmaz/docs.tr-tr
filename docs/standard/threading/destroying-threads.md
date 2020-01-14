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
ms.openlocfilehash: efd4c596f67d5eabace8ecafb48f2d350df6a18e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938042"
---
# <a name="destroying-threads"></a><span data-ttu-id="38b18-102">İş parçacıklarını yok etme</span><span class="sxs-lookup"><span data-stu-id="38b18-102">Destroying threads</span></span>

<span data-ttu-id="38b18-103">İş parçacığının yürütülmesini sonlandırmak için genellikle [birlikte bulunan iptal modelini](cancellation-in-managed-threads.md)kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="38b18-103">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="38b18-104">Bazen iş parçacığı işbirliği yapmak mümkün değildir, çünkü birlikte çalışma iptali için tasarlanmamış üçüncü taraf kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="38b18-104">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="38b18-105">.NET Framework <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi, yönetilen bir iş parçacığını zorla sonlandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38b18-105">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="38b18-106"><xref:System.Threading.Thread.Abort%2A>çağırdığınızda, ortak dil çalışma zamanı hedef iş parçacığında hedef iş parçacığının yakalayabileceği bir <xref:System.Threading.ThreadAbortException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38b18-106">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="38b18-107">Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38b18-107">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="38b18-108"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi .NET Core 'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="38b18-108">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="38b18-109">Üçüncü taraf kod yürütmeyi .NET Core 'da zorla sonlandırmak istiyorsanız, ayrı bir işlemde çalıştırın ve <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>kullanın.</span><span class="sxs-lookup"><span data-stu-id="38b18-109">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="38b18-110">Bir iş parçacığı <xref:System.Threading.Thread.Abort%2A> yöntemi çağrıldığında yönetilmeyen kodu yürütüp, çalışma zamanı <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>işaretler.</span><span class="sxs-lookup"><span data-stu-id="38b18-110">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="38b18-111">Özel durum, iş parçacığı yönetilen koda döndüğünde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="38b18-111">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="38b18-112">Bir iş parçacığı iptal edildikten sonra yeniden başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="38b18-112">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="38b18-113">Hedef iş parçacığı <xref:System.Threading.ThreadAbortException> yakalayıp `finally` bloğunda rastgele miktarda kod yürütebildiğinden <xref:System.Threading.Thread.Abort%2A> yöntemi iş parçacığının hemen iptal edilmesini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="38b18-113">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="38b18-114">İş parçacığı sonlanana kadar beklemeniz gerekiyorsa <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38b18-114">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="38b18-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, iş parçacığı gerçekten yürütmeyi durdurana veya isteğe bağlı bir zaman aşımı aralığı geçtiğinde döndürmeyen bir engelleme çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="38b18-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="38b18-116">Durdurulan iş parçacığı <xref:System.Threading.Thread.ResetAbort%2A> yöntemi çağırabilir veya bir `finally` bloğunda sınırsız işlem gerçekleştirebilir, bu nedenle bir zaman aşımı belirtmezseniz, bekleme işleminin bitmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="38b18-116">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="38b18-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrıda bekleyen iş parçacıkları, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>çağıran diğer iş parçacıkları tarafından kesintiye uğrar.</span><span class="sxs-lookup"><span data-stu-id="38b18-117">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="38b18-118">Threadadbortexception işleme</span><span class="sxs-lookup"><span data-stu-id="38b18-118">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="38b18-119">İş parçacığınızdan, kendi kodunuzda <xref:System.Threading.Thread.Abort%2A> çağırmanın veya iş parçacığının çalıştığı bir uygulama etki alanının kaldırılması sonucu olarak (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> iş parçacıklarını sonlandırmak için <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kullanıyorsa), iş parçacığın <xref:System.Threading.ThreadAbortException> işlemesi ve aşağıdaki kodda gösterildiği gibi `finally` yan tümcesinde son işlemleri gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="38b18-119">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="38b18-120">`finally` yan tümcesinin sonunda veya `catch` yan tümcesi yoksa `finally` yan tümcesinin sonunda bir <xref:System.Threading.ThreadAbortException> yeniden oluşturulduğu için, temizleme kodunuzun `catch` yan tümcesinde veya `finally` yan tümcesinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="38b18-120">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="38b18-121"><xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> yöntemini çağırarak sistemin özel durumu yeniden oluşturmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38b18-121">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="38b18-122">Ancak, bunu yalnızca kendi kodunuz <xref:System.Threading.ThreadAbortException>neden olduysa yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="38b18-122">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38b18-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38b18-123">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="38b18-124">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="38b18-124">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)

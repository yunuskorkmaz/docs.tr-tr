---
title: İş parçacıklarını yok etme
description: .NET 'teki bir iş parçacığını yok etmeniz gerektiğinde, birlikte çalışırken iptal veya Thread. Abort yöntemi gibi seçeneklerinizi öğrenin. Threadadbortexception işlemesini öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: baf9289413de0e99533f121eb2a404ff0d873511
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768514"
---
# <a name="destroying-threads"></a><span data-ttu-id="5ab92-104">İş parçacıklarını yok etme</span><span class="sxs-lookup"><span data-stu-id="5ab92-104">Destroying threads</span></span>

<span data-ttu-id="5ab92-105">İş parçacığının yürütülmesini sonlandırmak için genellikle [birlikte bulunan iptal modelini](cancellation-in-managed-threads.md)kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5ab92-105">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="5ab92-106">Bazen iş parçacığı işbirliği yapmak mümkün değildir, çünkü birlikte çalışma iptali için tasarlanmamış üçüncü taraf kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="5ab92-106">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="5ab92-107"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.NET Framework yöntemi, yönetilen bir iş parçacığını zorla sonlandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ab92-107">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="5ab92-108"><xref:System.Threading.Thread.Abort%2A>' İ çağırdığınızda, ortak dil çalışma zamanı hedef iş parçacığında <xref:System.Threading.ThreadAbortException> hedef iş parçacığının yakalayabileceği bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ab92-108">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="5ab92-109">Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ab92-109">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5ab92-110"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Yöntem .NET Core 'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5ab92-110">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="5ab92-111">.NET Core 'da üçüncü taraf kod yürütmeyi zorla sonlandırmak isterseniz, ayrı bir işlemde çalıştırın ve kullanın <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ab92-111">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="5ab92-112">Bir iş parçacığı yöntemi çağrıldığında yönetilmeyen kodu yürütüp <xref:System.Threading.Thread.Abort%2A> , çalışma zamanı onu işaretler <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ab92-112">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5ab92-113">Özel durum, iş parçacığı yönetilen koda döndüğünde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5ab92-113">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="5ab92-114">Bir iş parçacığı iptal edildikten sonra yeniden başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="5ab92-114">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="5ab92-115"><xref:System.Threading.Thread.Abort%2A>Yöntemi, iş parçacığı <xref:System.Threading.ThreadAbortException> bir blokta rastgele miktarda kod yakalayıp yürütebildiğinden, iş parçacığının hemen durmasına neden olmaz `finally` .</span><span class="sxs-lookup"><span data-stu-id="5ab92-115">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="5ab92-116"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>İş parçacığı sonlanana kadar beklemeniz gerekiyorsa, öğesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ab92-116">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="5ab92-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, iş parçacığı gerçekten yürütmeyi durdurana veya isteğe bağlı bir zaman aşımı aralığı geçtiğinde döndürmeyen bir engelleme çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="5ab92-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="5ab92-118">Durdurulan iş parçacığı <xref:System.Threading.Thread.ResetAbort%2A> yöntemi çağırabilir veya bir blokta sınırsız işlem gerçekleştirebilir, bu `finally` nedenle bir zaman aşımı belirtmezseniz, bekleme işleminin bitmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="5ab92-118">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="5ab92-119">Yöntemine yapılan bir çağrıda bekleyen iş parçacıkları, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> çağıran diğer iş parçacıkları tarafından kesintiye uğratılmasını sağlayabilir <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ab92-119">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="5ab92-120">Threadadbortexception işleme</span><span class="sxs-lookup"><span data-stu-id="5ab92-120">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="5ab92-121">İş parçacığınızdan, <xref:System.Threading.Thread.Abort%2A> kendi kodunuzun çağrılması veya iş parçacığının çalıştığı bir uygulama etki alanının kaldırılması sonucu olarak (iş <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> parçacıklarını sonlandırmak için kullanır), iş parçacığınızdan <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> , <xref:System.Threading.ThreadAbortException> `finally` aşağıdaki kodda gösterildiği gibi, bir yan tümcede herhangi bir son işlem gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ab92-121">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="5ab92-122">Temizleme kodunuz yan tümce `catch` veya yan tümcesinde olmalıdır `finally` , çünkü <xref:System.Threading.ThreadAbortException> yan tümcesinin sonunda sistem tarafından yeniden oluşturulur veya yan tümce yoksa `finally` `catch` yan tümcesinin sonunda `finally` .</span><span class="sxs-lookup"><span data-stu-id="5ab92-122">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="5ab92-123">Yöntemini çağırarak sistemin özel durumu yeniden oluşturmasını engelleyebilirsiniz <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ab92-123">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5ab92-124">Bununla birlikte, bunu yalnızca kendi kodunuz ' a neden olursa yapmanız gerekir <xref:System.Threading.ThreadAbortException> .</span><span class="sxs-lookup"><span data-stu-id="5ab92-124">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab92-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ab92-125">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="5ab92-126">Iş parçacıkları ve Iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="5ab92-126">Using Threads and Threading</span></span>](using-threads-and-threading.md)

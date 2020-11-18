---
title: 'Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme'
description: .NET 'teki bir görevi ve alt öğelerini iptal etme örneklerine bakın. Örnekler, iptal edilebilir görev oluşturma işleminden, görevin iptal edildiğini fark eden adımları kapsar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 578544a910127f41dfdfd577316b23d6d5a60bc4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817269"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="b6b87-104">Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme</span><span class="sxs-lookup"><span data-stu-id="b6b87-104">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="b6b87-105">Bu örnekler, aşağıdaki görevlerin nasıl gerçekleştirildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="b6b87-105">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="b6b87-106">İptal edilebilen bir görevi oluşturmak ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="b6b87-106">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="b6b87-107">Kullanıcı temsilcinize ve isteğe bağlı olarak görev örneğine bir iptal belirteci geçirmek.</span><span class="sxs-lookup"><span data-stu-id="b6b87-107">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="b6b87-108">Kullanıcı temsilcinizde iptal belirtecini fark etmek ve buna yanıt vermek.</span><span class="sxs-lookup"><span data-stu-id="b6b87-108">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="b6b87-109">İsteğe bağlı olarak, çağıran iş parçacığında görevin iptal edildiğini belirlemek.</span><span class="sxs-lookup"><span data-stu-id="b6b87-109">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="b6b87-110">Çağıran iş parçacığı görevi zorla bitirmez; yalnızca iptalin istendiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b6b87-110">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="b6b87-111">Görev zaten çalışıyorsa, isteği fark etmek ve uygun bir şekilde karşılık vermek kullanıcı temsilcisinin görevidir.</span><span class="sxs-lookup"><span data-stu-id="b6b87-111">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="b6b87-112">Görev çalışmadan iptal istenirse, kullanıcı temsilcisi asla yürütülmez ve görev nesnesi Canceled durumuna geçer.</span><span class="sxs-lookup"><span data-stu-id="b6b87-112">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6b87-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6b87-113">Example</span></span>  
 <span data-ttu-id="b6b87-114">Bu örnek, bir iptal isteğine yanıt olarak bir <xref:System.Threading.Tasks.Task> öğesinin ve alt öğelerinin nasıl sonlandırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6b87-114">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="b6b87-115">Ayrıca, kullanıcı temsilcisi bir <xref:System.Threading.Tasks.TaskCanceledException> oluşturarak sonlandırdığında, çağıran iş parçacığının, isteğe bağlı olarak, görevlerin bitmesini beklemek için <xref:System.Threading.Tasks.Task.Wait%2A> yöntemini veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemini kullanabileceğini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6b87-115">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="b6b87-116">Bu durumda, özel durumları işlemek için çağıran iş parçacığında bir `try/catch` bloğu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6b87-116">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="b6b87-117"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı, <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> ve <xref:System.Threading.CancellationToken?displayProperty=nameWithType> türlerini temel alan iptal modeliyle tamamen tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="b6b87-117">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="b6b87-118">Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](../threading/cancellation-in-managed-threads.md) ve [Görev iptali](task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="b6b87-118">For more information, see [Cancellation in Managed Threads](../threading/cancellation-in-managed-threads.md) and [Task Cancellation](task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b87-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6b87-119">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="b6b87-120">Görev tabanlı zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="b6b87-120">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="b6b87-121">Eklenen ve Ayrılan Alt Görevler</span><span class="sxs-lookup"><span data-stu-id="b6b87-121">Attached and Detached Child Tasks</span></span>](attached-and-detached-child-tasks.md)
- [<span data-ttu-id="b6b87-122">PLıNQ ve TPL 'deki lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b6b87-122">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)

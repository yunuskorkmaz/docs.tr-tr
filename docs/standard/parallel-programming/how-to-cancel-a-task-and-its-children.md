---
title: 'Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb520169f8e7925862d415a4dfb65af09263b0d2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196731"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="d5ec3-102">Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme</span><span class="sxs-lookup"><span data-stu-id="d5ec3-102">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="d5ec3-103">Bu örnekler, aşağıdaki görevlerin nasıl gerçekleştirildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="d5ec3-103">These examples show how to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="d5ec3-104">İptal edilebilen bir görevi oluşturmak ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-104">Create and start a cancelable task.</span></span>  
  
2.  <span data-ttu-id="d5ec3-105">Kullanıcı temsilcinize ve isteğe bağlı olarak görev örneğine bir iptal belirteci geçirmek.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-105">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3.  <span data-ttu-id="d5ec3-106">Kullanıcı temsilcinizde iptal belirtecini fark etmek ve buna yanıt vermek.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-106">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4.  <span data-ttu-id="d5ec3-107">İsteğe bağlı olarak, çağıran iş parçacığında görevin iptal edildiğini belirlemek.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-107">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="d5ec3-108">Çağıran iş parçacığı görevi zorla bitirmez; yalnızca iptalin istendiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-108">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="d5ec3-109">Görev zaten çalışıyorsa, isteği fark etmek ve uygun bir şekilde karşılık vermek kullanıcı temsilcisinin görevidir.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-109">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="d5ec3-110">Görev çalışmadan iptal istenirse, kullanıcı temsilcisi asla yürütülmez ve görev nesnesi Canceled durumuna geçer.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-110">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5ec3-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5ec3-111">Example</span></span>  
 <span data-ttu-id="d5ec3-112">Bu örnek, bir iptal isteğine yanıt olarak bir <xref:System.Threading.Tasks.Task> öğesinin ve alt öğelerinin nasıl sonlandırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-112">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="d5ec3-113">Ayrıca, kullanıcı temsilcisi bir <xref:System.Threading.Tasks.TaskCanceledException> oluşturarak sonlandırdığında, çağıran iş parçacığının, isteğe bağlı olarak, görevlerin bitmesini beklemek için <xref:System.Threading.Tasks.Task.Wait%2A> yöntemini veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemini kullanabileceğini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-113">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="d5ec3-114">Bu durumda, özel durumları işlemek için çağıran iş parçacığında bir `try/catch` bloğu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-114">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="d5ec3-115"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı, <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> ve <xref:System.Threading.CancellationToken?displayProperty=nameWithType> türlerini temel alan iptal modeliyle tamamen tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-115">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="d5ec3-116">Daha fazla bilgi için [yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md) ve [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).</span><span class="sxs-lookup"><span data-stu-id="d5ec3-116">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md) and [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ec3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5ec3-117">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
- [<span data-ttu-id="d5ec3-118">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="d5ec3-118">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
- [<span data-ttu-id="d5ec3-119">Eklenen ve Ayrılan Alt Görevler</span><span class="sxs-lookup"><span data-stu-id="d5ec3-119">Attached and Detached Child Tasks</span></span>](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
- [<span data-ttu-id="d5ec3-120">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="d5ec3-120">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)

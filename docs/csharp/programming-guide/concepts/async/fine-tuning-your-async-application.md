---
title: Zaman uyumsuz uygulamanızda ince ayar yapma (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970236"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="e94d0-102">Zaman uyumsuz uygulamanızda ince ayar yapma (C#)</span><span class="sxs-lookup"><span data-stu-id="e94d0-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="e94d0-103"><xref:System.Threading.Tasks.Task> türünün kullanılabilir hale getiren yöntemleri ve özellikleri kullanarak zaman uyumsuz uygulamalarınıza duyarlık ve esneklik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e94d0-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="e94d0-104">Bu bölümdeki konularda, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>gibi <xref:System.Threading.CancellationToken> ve önemli `Task` yöntemleri kullanan örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e94d0-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e94d0-105">`WhenAny` ve `WhenAll`kullanarak, birden çok görevi daha kolay başlatabilir ve tek bir görevi izleyerek tamamlanmasını deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e94d0-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="e94d0-106">`WhenAny`, bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="e94d0-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="e94d0-107">`WhenAny`kullanan örnekler için bkz. [kalan zaman uyumsuz görevleri bir işlem tamamlandıktan sonra iptal etmeC#()](./cancel-remaining-async-tasks-after-one-is-complete.md) ve [birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsaC#() işlem](./start-multiple-async-tasks-and-process-them-as-they-complete.md)yapın.</span><span class="sxs-lookup"><span data-stu-id="e94d0-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="e94d0-108">`WhenAll`, bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="e94d0-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="e94d0-109">Daha fazla bilgi ve `WhenAll`kullanan bir örnek için, bkz. [Task. WhenAllC#() kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="e94d0-109">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="e94d0-110">Bu bölüm aşağıdaki örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e94d0-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="e94d0-111">[Zaman uyumsuz bir görevi veya görev listesini (C#) iptal edin](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="e94d0-111">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="e94d0-112">Zaman uyumsuz görevleri bir süre sonra iptal et (C#)</span><span class="sxs-lookup"><span data-stu-id="e94d0-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="e94d0-113">Tamamlandıktan sonra kalan zaman uyumsuz görevleri iptal et (C#)</span><span class="sxs-lookup"><span data-stu-id="e94d0-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="e94d0-114">Birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa (C#) işleyin</span><span class="sxs-lookup"><span data-stu-id="e94d0-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="e94d0-115">Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e94d0-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="e94d0-116">Projeler, aşağıdaki görüntüde gösterildiği gibi, işlemi başlatan bir düğme ve bunu iptal eden bir düğme içeren bir kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e94d0-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="e94d0-117">Düğmeler `startButton` ve `cancelButton`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e94d0-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="e94d0-118">![Iptal düğmesi olan WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi ile iletişim kutusu")</span><span class="sxs-lookup"><span data-stu-id="e94d0-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="e94d0-119">Tüm Windows Presentation Foundation (WPF) projelerini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="e94d0-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e94d0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e94d0-120">See also</span></span>

- [<span data-ttu-id="e94d0-121">Async ve await (C#) ile zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="e94d0-121">Asynchronous Programming with async and await (C#)</span></span>](./index.md)

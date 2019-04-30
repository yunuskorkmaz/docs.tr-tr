---
title: (C#) Async uygulamanızda hassas ayar yapma
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 31d9fcf04780d421faa609e06e18e66e0e8b9ce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702688"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="f306b-102">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="f306b-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="f306b-103">Özellikler ve yöntemler kullanarak zaman uyumsuz uygulamalarınıza kesinlik ve esneklik ekleyebilirsiniz, <xref:System.Threading.Tasks.Task> türü kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="f306b-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="f306b-104">Bu bölümdeki konular, kullanan örnekler <xref:System.Threading.CancellationToken> ve önemli `Task` gibi yöntemler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f306b-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f306b-105">Kullanarak `WhenAny` ve `WhenAll`, daha kolay birden çok görev başlatabilir ve tek bir görevi izleyerek bunların tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="f306b-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="f306b-106">`WhenAny` bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="f306b-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="f306b-107">Kullanan örnekler `WhenAny`, bkz: [sonra bir tamamlandı (C#) kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) ve [birden çok zaman uyumsuz görevleri başlatın ve işlemi bunları olarak bunlar tam (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="f306b-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="f306b-108">`WhenAll` bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="f306b-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="f306b-109">Daha fazla bilgi ve kullanan bir örnek için `WhenAll`, bkz: [nasıl yapılır: Zaman uyumsuz izlenecek yolu Task.WhenAll kullanarak genişletme (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="f306b-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="f306b-110">Bu bölüm aşağıdaki örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f306b-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="f306b-111">[Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="f306b-111">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="f306b-112">Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="f306b-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="f306b-113">Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="f306b-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="f306b-114">Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme</span><span class="sxs-lookup"><span data-stu-id="f306b-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="f306b-115">Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f306b-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="f306b-116">Projeleri, işlem başlatan bir düğme ve aşağıda gösterildiği gibi iptal eden bir düğme içeren bir Arabirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f306b-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="f306b-117">Düğmeleri adlı `startButton` ve `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="f306b-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="f306b-118">![İptal düğmesiyle okno WPF](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "iletişim kutusunu başlatma ve durdurma düğmesi")</span><span class="sxs-lookup"><span data-stu-id="f306b-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="f306b-119">Tam bir Windows Presentation Foundation (WPF) projelerden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="f306b-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f306b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f306b-120">See also</span></span>

- [<span data-ttu-id="f306b-121">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="f306b-121">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)

---
title: "(C#) Async uygulamanızda hassas ayar yapma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c42f51d627f827e216e6c25b3bde60e32b9ba027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="de3aa-102">(C#) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="de3aa-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="de3aa-103">Özellikler ve yöntemler kullanarak zaman uyumsuz uygulamalarınızı duyarlık ve esneklik ekleyebilirsiniz, <xref:System.Threading.Tasks.Task> türünü kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="de3aa-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="de3aa-104">Bu bölümdeki konular, kullanan örnekler <xref:System.Threading.CancellationToken> ve önemli `Task` gibi yöntemler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de3aa-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="de3aa-105">Kullanarak `WhenAny` ve `WhenAll`, daha kolay birden çok görevi başlatma ve tek bir görev izleme ile bunların tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="de3aa-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="de3aa-106">`WhenAny`bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="de3aa-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="de3aa-107">Kullanma örnekleri için `WhenAny`, bkz: [bir tamamlandı (C#) sonra geri kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) ve [Başlat birden çok zaman uyumsuz görevleri ve işlem bunları olarak bunlar tam (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="de3aa-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="de3aa-108">`WhenAll`bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="de3aa-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="de3aa-109">Daha fazla bilgi ve kullanan bir örnek için `WhenAll`, bkz: [nasıl yapılır: zaman uyumsuz izlenecek yol Task.WhenAll kullanma (C#) tarafından genişletmek](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="de3aa-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="de3aa-110">Bu bölüm aşağıdaki örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="de3aa-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="de3aa-111">[Zaman uyumsuz görevi veya görev (C#) listesini iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="de3aa-111">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="de3aa-112">Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="de3aa-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="de3aa-113">Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="de3aa-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="de3aa-114">Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme</span><span class="sxs-lookup"><span data-stu-id="de3aa-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="de3aa-115">Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="de3aa-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="de3aa-116">Projeleri işlemi başlatan bir düğme ve aşağıdaki görüntü gösterildiği gibi iptal düğmesi içeren bir kullanıcı Arabirimi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="de3aa-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="de3aa-117">Düğmeleri adlı `startButton` ve `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="de3aa-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="de3aa-118">![WPF penceresi iptal düğmesi](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "iptali")</span><span class="sxs-lookup"><span data-stu-id="de3aa-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="de3aa-119">Tam Windows Presentation Foundation (WPF) projelerden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="de3aa-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3aa-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de3aa-120">See Also</span></span>  
 [<span data-ttu-id="de3aa-121">Zaman uyumsuz programlama ile async ve await (C#)</span><span class="sxs-lookup"><span data-stu-id="de3aa-121">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)

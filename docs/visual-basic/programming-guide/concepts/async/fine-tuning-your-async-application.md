---
title: (Visual Basic) Async uygulamanızda hassas ayar yapma
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 3e9a6d02ec4948103b892ae012b8c51f66dd06c4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624729"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="0fb8b-102">(Visual Basic) Async uygulamanızda hassas ayar yapma</span><span class="sxs-lookup"><span data-stu-id="0fb8b-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="0fb8b-103">Özellikler ve yöntemler kullanarak zaman uyumsuz uygulamalarınıza kesinlik ve esneklik ekleyebilirsiniz, <xref:System.Threading.Tasks.Task> türü kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="0fb8b-104">Bu bölümdeki konular, kullanan örnekler <xref:System.Threading.CancellationToken> ve önemli `Task` gibi yöntemler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0fb8b-105">Kullanarak `WhenAny` ve `WhenAll`, daha kolay birden çok görev başlatabilir ve tek bir görevi izleyerek bunların tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="0fb8b-106">`WhenAny` bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="0fb8b-107">Kullanan örnekler `WhenAny`, bkz: [sonra bir tamamlandı (Visual Basic) kalan zaman uyumsuz görevleri iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)ve [birden çok zaman uyumsuz görevleri başlatın ve işlemi bunları olarak bunlar tam (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="0fb8b-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="0fb8b-108">`WhenAll` bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="0fb8b-109">Daha fazla bilgi ve kullanan bir örnek için `WhenAll`, bkz: [nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="0fb8b-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="0fb8b-110">Bu bölüm aşağıdaki örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="0fb8b-111">[Zaman uyumsuz bir görev veya görevleri (Visual Basic) listesini iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="0fb8b-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="0fb8b-112">(Visual Basic) bir süre sonra zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="0fb8b-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="0fb8b-113">Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme</span><span class="sxs-lookup"><span data-stu-id="0fb8b-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="0fb8b-114">Birden çok zaman uyumsuz görev başlatma ve bunlar (Visual Basic) tamamlandıkça işleme</span><span class="sxs-lookup"><span data-stu-id="0fb8b-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="0fb8b-115">Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="0fb8b-116">Projeleri, işlem başlatan bir düğme ve aşağıda gösterildiği gibi iptal eden bir düğme içeren bir Arabirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="0fb8b-117">Düğmeleri adlı `startButton` ve `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="0fb8b-118">![İptal düğmesiyle okno WPF](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "iletişim kutusunu başlatma ve durdurma düğmesi")</span><span class="sxs-lookup"><span data-stu-id="0fb8b-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="0fb8b-119">Tam bir Windows Presentation Foundation (WPF) projelerden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="0fb8b-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb8b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fb8b-120">See also</span></span>

- [<span data-ttu-id="0fb8b-121">Zaman uyumsuz programlama ile Async ve Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fb8b-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)

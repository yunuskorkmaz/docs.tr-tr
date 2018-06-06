---
title: Async uygulamanızda (Visual Basic) hassas ayar yapma
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 6e919d3998719186d0355b9bd187782fcb0e5332
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696682"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Async uygulamanızda (Visual Basic) hassas ayar yapma
Özellikler ve yöntemler kullanarak zaman uyumsuz uygulamalarınızı duyarlık ve esneklik ekleyebilirsiniz, <xref:System.Threading.Tasks.Task> türünü kullanılabilir hale getirir. Bu bölümdeki konular, kullanan örnekler <xref:System.Threading.CancellationToken> ve önemli `Task` gibi yöntemler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Kullanarak `WhenAny` ve `WhenAll`, daha kolay birden çok görevi başlatma ve tek bir görev izleme ile bunların tamamlanmasını bekler.  
  
-   `WhenAny` bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanma örnekleri için `WhenAny`, bkz: [bir tamamlandı (Visual Basic) sonra geri kalan zaman uyumsuz görevleri iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)ve [Başlat birden çok zaman uyumsuz görevleri ve işlem bunları olarak bunlar tam (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan bir örnek için `WhenAll`, bkz: [nasıl yapılır: Task.WhenAll kullanarak (Visual Basic) tarafından zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
-   [Zaman uyumsuz görevi veya görev (Visual Basic) listesi iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Bir süre (Visual Basic) sonra zaman uyumsuz görevleri iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Birden çok zaman uyumsuz görev başlatma ve bunlar (Visual Basic) tamamlandıkça işleme](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.  
  
 Projeleri işlemi başlatan bir düğme ve aşağıdaki görüntü gösterildiği gibi iptal düğmesi içeren bir kullanıcı Arabirimi oluşturma. Düğmeleri adlı `startButton` ve `cancelButton`.  
  
 ![WPF penceresi iptal düğmesi](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "iptali")  
  
 Tam Windows Presentation Foundation (WPF) projelerden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)

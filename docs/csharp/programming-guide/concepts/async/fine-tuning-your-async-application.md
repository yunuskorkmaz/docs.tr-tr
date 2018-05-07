---
title: (C#) Async uygulamanızda hassas ayar yapma
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cf4e0082fbaa2a5189646014e53f0320e16f40de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="fine-tuning-your-async-application-c"></a>(C#) Async uygulamanızda hassas ayar yapma
Özellikler ve yöntemler kullanarak zaman uyumsuz uygulamalarınızı duyarlık ve esneklik ekleyebilirsiniz, <xref:System.Threading.Tasks.Task> türünü kullanılabilir hale getirir. Bu bölümdeki konular, kullanan örnekler <xref:System.Threading.CancellationToken> ve önemli `Task` gibi yöntemler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Kullanarak `WhenAny` ve `WhenAll`, daha kolay birden çok görevi başlatma ve tek bir görev izleme ile bunların tamamlanmasını bekler.  
  
-   `WhenAny` bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanma örnekleri için `WhenAny`, bkz: [bir tamamlandı (C#) sonra geri kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) ve [Başlat birden çok zaman uyumsuz görevleri ve işlem bunları olarak bunlar tam (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan bir örnek için `WhenAll`, bkz: [nasıl yapılır: zaman uyumsuz izlenecek yol Task.WhenAll kullanma (C#) tarafından genişletmek](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
-   [Zaman uyumsuz görevi veya görev (C#) listesini iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 olmalıdır veya daha yeni bilgisayarınızda yüklü.  
  
 Projeleri işlemi başlatan bir düğme ve aşağıdaki görüntü gösterildiği gibi iptal düğmesi içeren bir kullanıcı Arabirimi oluşturma. Düğmeleri adlı `startButton` ve `cancelButton`.  
  
 ![WPF penceresi iptal düğmesi](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "iptali")  
  
 Tam Windows Presentation Foundation (WPF) projelerden indirebilirsiniz [zaman uyumsuz örnek: ince ayar uygulamanız](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)

---
title: (C#) Async uygulamanızda hassas ayar yapma
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 23557c0c920fbd858e9bdf8ae629bd5ef5f0355b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032266"
---
# <a name="fine-tuning-your-async-application-c"></a>(C#) Async uygulamanızda hassas ayar yapma
Özellikler ve yöntemler kullanarak zaman uyumsuz uygulamalarınıza kesinlik ve esneklik ekleyebilirsiniz, <xref:System.Threading.Tasks.Task> türü kullanıma sunar. Bu bölümdeki konular, kullanan örnekler <xref:System.Threading.CancellationToken> ve önemli `Task` gibi yöntemler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Kullanarak `WhenAny` ve `WhenAll`, daha kolay birden çok görev başlatabilir ve tek bir görevi izleyerek bunların tamamlanmasını bekler.  
  
-   `WhenAny` bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanan örnekler `WhenAny`, bkz: [sonra bir tamamlandı (C#) kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) ve [birden çok zaman uyumsuz görevleri başlatın ve işlemi bunları olarak bunlar tam (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan bir örnek için `WhenAll`, bakın [nasıl yapılır: zaman uyumsuz izlenecek yolu Task.WhenAll (C#) kullanarak genişletme](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
-   [Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
 Projeleri, işlem başlatan bir düğme ve aşağıda gösterildiği gibi iptal eden bir düğme içeren bir Arabirim oluşturur. Düğmeleri adlı `startButton` ve `cancelButton`.  
  
 ![İptal düğmesiyle okno WPF](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "iptal")  
  
 Tam bir Windows Presentation Foundation (WPF) projelerden indirebileceğiniz [zaman uyumsuz örneği: ince uygulamanıza](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)

---
title: (C#) Async uygulamanızda hassas ayar yapma
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 31d9fcf04780d421faa609e06e18e66e0e8b9ce7
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679171"
---
# <a name="fine-tuning-your-async-application-c"></a>(C#) Async uygulamanızda hassas ayar yapma
Özellikler ve yöntemler kullanarak zaman uyumsuz uygulamalarınıza kesinlik ve esneklik ekleyebilirsiniz, <xref:System.Threading.Tasks.Task> türü kullanıma sunar. Bu bölümdeki konular, kullanan örnekler <xref:System.Threading.CancellationToken> ve önemli `Task` gibi yöntemler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Kullanarak `WhenAny` ve `WhenAll`, daha kolay birden çok görev başlatabilir ve tek bir görevi izleyerek bunların tamamlanmasını bekler.  
  
-   `WhenAny` bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanan örnekler `WhenAny`, bkz: [sonra bir tamamlandı (C#) kalan zaman uyumsuz görevleri iptal](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) ve [birden çok zaman uyumsuz görevleri başlatın ve işlemi bunları olarak bunlar tam (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan bir örnek için `WhenAll`, bkz: [nasıl yapılır: Zaman uyumsuz izlenecek yolu Task.WhenAll kullanarak genişletme (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
-   [Zaman uyumsuz bir görev veya görevleri (C#) listesini iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Bir süre (C#) sonra zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Tam (C#) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Birden çok zaman uyumsuz görev başlatma ve bunlar (C#) tamamlandıkça işleme](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
 Projeleri, işlem başlatan bir düğme ve aşağıda gösterildiği gibi iptal eden bir düğme içeren bir Arabirim oluşturur. Düğmeleri adlı `startButton` ve `cancelButton`.  
  
 ![İptal düğmesiyle okno WPF](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "iletişim kutusunu başlatma ve durdurma düğmesi")  
  
 Tam bir Windows Presentation Foundation (WPF) projelerden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz programlama ile async ve await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)

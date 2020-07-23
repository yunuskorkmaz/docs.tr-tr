---
title: Zaman uyumsuz uygulamanızda ince ayar yapma (C#)
description: Bu C# örnekleri, zaman uyumsuz uygulamalar üzerinde ince ayar yapmak için, CancellationToken ve Task. WhenAll ve Task. Whengibi önemli görev yöntemlerini kullanır.
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 46457f889a78932e306d2bd21dca666625d744eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925325"
---
# <a name="fine-tuning-your-async-application-c"></a>Zaman uyumsuz uygulamanızda ince ayar yapma (C#)
Türün kullanılabilir hale getiren yöntemleri ve özellikleri kullanarak, zaman uyumsuz uygulamalarınıza duyarlık ve esneklik ekleyebilirsiniz <xref:System.Threading.Tasks.Task> . Bu bölümdeki konularda, <xref:System.Threading.CancellationToken> ve gibi önemli Yöntemler ve kullanılan örnekler gösterilmektedir `Task` <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .  
  
 Ve kullanarak `WhenAny` `WhenAll` , birden çok görevi daha kolay başlatabilir ve tek bir görevi izleyerek tamamlanmasını deneyebilirsiniz.  
  
- `WhenAny`bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanan örnekler için `WhenAny` , bkz. [kalan zaman uyumsuz görevleri bir işlem tamamlandıktan sonra iptal etme (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) ve [birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa (c#) işler](./start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan bir örnek için `WhenAll` , bkz. [Task. WhenAll (C#) kullanarak zaman uyumsuz izlenecek yolu genişletme](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
- [Zaman uyumsuz bir görevi veya görev listesini Iptal etme (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Kalan zaman uyumsuz görevleri bir tane tamamlandıktan sonra iptal etme (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Birden çok zaman uyumsuz görev başlatma ve bunları tamamlarsa Işleme (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.  
  
 Projeler, aşağıdaki görüntüde gösterildiği gibi, işlemi başlatan bir düğme ve bunu iptal eden bir düğme içeren bir kullanıcı arabirimi oluşturur. Düğmeler ve olarak adlandırılır `startButton` `cancelButton` .  
  
 ![Iptal düğmesi olan WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi ile iletişim kutusu")  
  
 Tüm Windows Presentation Foundation (WPF) projelerini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (C#)](./index.md)

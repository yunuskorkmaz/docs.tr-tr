---
title: Zaman uyumsuz uygulamanızda ince ayar yapma (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: 4a37966566d701e7070c33248d6ff4187a26e9f1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595807"
---
# <a name="fine-tuning-your-async-application-c"></a>Zaman uyumsuz uygulamanızda ince ayar yapma (C#)
<xref:System.Threading.Tasks.Task> Türün kullanılabilir hale getiren yöntemleri ve özellikleri kullanarak, zaman uyumsuz uygulamalarınıza duyarlık ve esneklik ekleyebilirsiniz. Bu bölümdeki <xref:System.Threading.CancellationToken> konularda, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve `Task` gibiönemliYöntemlervekullanılanörneklergösterilmektedir.<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>  
  
 `WhenAny` Ve`WhenAll`kullanarak, birden çok görevi daha kolay başlatabilir ve tek bir görevi izleyerek tamamlanmasını deneyebilirsiniz.  
  
- `WhenAny`bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanan `WhenAny`örnekler için bkz. [kalan zaman uyumsuz görevleri bir işlem tamamlandıktan sonra iptal etmeC#()](./cancel-remaining-async-tasks-after-one-is-complete.md) ve [birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsaC#() işlem yapın](./start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan `WhenAll`bir örnek için bkz [. nasıl yapılır: Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)kullanarak zaman uyumsuz izlenecek yolu genişletin.  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
- [Zaman uyumsuz bir görevi veya görev listesini (C#) iptal edin](./cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zaman uyumsuz görevleri bir süre sonra iptal et (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Tamamlandıktan sonra kalan zaman uyumsuz görevleri iptal et (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa (C#) işleyin](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.  
  
 Projeler, aşağıdaki görüntüde gösterildiği gibi, işlemi başlatan bir düğme ve bunu iptal eden bir düğme içeren bir kullanıcı arabirimi oluşturur. Düğmeler ve `startButton` `cancelButton`olarak adlandırılır.  
  
 ![İptal düğmesi olan WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi Ile iletişim kutusu")  
  
 Tüm Windows Presentation Foundation (WPF) projelerini [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)hassas bir şekilde ayarlama.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await (C#) ile zaman uyumsuz programlama](./index.md)

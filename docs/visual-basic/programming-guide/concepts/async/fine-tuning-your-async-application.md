---
title: Zaman Uyumsuz Uygulamanızda Hassas Ayar Yapma
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 6ad4f9a526e0497029ff8ddc3e93637a4f9acb00
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075440"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)

Türün kullanılabilir hale getiren yöntemleri ve özellikleri kullanarak, zaman uyumsuz uygulamalarınıza duyarlık ve esneklik ekleyebilirsiniz <xref:System.Threading.Tasks.Task> . Bu bölümdeki konularda, <xref:System.Threading.CancellationToken> ve gibi önemli Yöntemler ve kullanılan örnekler gösterilmektedir `Task` <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> .  
  
 Ve kullanarak `WhenAny` `WhenAll` , birden çok görevi daha kolay başlatabilir ve tek bir görevi izleyerek tamamlanmasını deneyebilirsiniz.  
  
- `WhenAny` bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanan örnekler için `WhenAny` , bkz.  [kalan zaman uyumsuz görevleri bir işlem tamamlandıktan sonra iptal etme (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)ve [birden çok zaman uyumsuz görev başlatın ve bunları tamamladıktan sonra işleyin (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan bir örnek için `WhenAll` bkz. [nasıl yapılır: görev. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
- [Zaman uyumsuz bir görevi veya görev listesini Iptal edin (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zaman uyumsuz görevleri bir süre sonra iptal et (Visual Basic)](cancel-async-tasks-after-a-period-of-time.md)  
  
- [Kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal et (Visual Basic)](cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa Işleyin (Visual Basic)](start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.  
  
 Projeler, aşağıdaki görüntüde gösterildiği gibi, işlemi başlatan bir düğme ve bunu iptal eden bir düğme içeren bir kullanıcı arabirimi oluşturur. Düğmeler ve olarak adlandırılır `startButton` `cancelButton` .  
  
 ![Iptal düğmesi olan WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi ile iletişim kutusu")  
  
 Tüm Windows Presentation Foundation (WPF) projelerini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](index.md)

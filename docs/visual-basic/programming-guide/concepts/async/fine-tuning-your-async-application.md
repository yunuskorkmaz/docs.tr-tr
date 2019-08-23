---
title: Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 49e57d56c4df79cd9a3e8d5f76d6fc76ebdfa722
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958176"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)
<xref:System.Threading.Tasks.Task> Türün kullanılabilir hale getiren yöntemleri ve özellikleri kullanarak, zaman uyumsuz uygulamalarınıza duyarlık ve esneklik ekleyebilirsiniz. Bu bölümdeki <xref:System.Threading.CancellationToken> konularda, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve `Task` gibiönemliYöntemlervekullanılanörneklergösterilmektedir.<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>  
  
 `WhenAny` Ve`WhenAll`kullanarak, birden çok görevi daha kolay başlatabilir ve tek bir görevi izleyerek tamamlanmasını deneyebilirsiniz.  
  
- `WhenAny`bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanan `WhenAny`örnekler için, bkz. [kalan zaman uyumsuz görevleri bir işlem tamamlandıktan sonra iptal etme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)ve [birden çok zaman uyumsuz görev başlatın ve bunları tamamladıktan sonra işleyin (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan `WhenAll`bir örnek için bkz [. nasıl yapılır: Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)kullanarak zaman uyumsuz izlenecek yolu genişletin.  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
- [Zaman uyumsuz bir görevi veya görev listesini Iptal edin (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zaman uyumsuz görevleri bir süre sonra iptal et (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal et (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa Işleyin (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.  
  
 Projeler, aşağıdaki görüntüde gösterildiği gibi, işlemi başlatan bir düğme ve bunu iptal eden bir düğme içeren bir kullanıcı arabirimi oluşturur. Düğmeler ve `startButton` `cancelButton`olarak adlandırılır.  
  
 ![İptal düğmesi olan WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi Ile iletişim kutusu")  
  
 Tüm Windows Presentation Foundation (WPF) projelerini [zaman uyumsuz örnekten indirebilirsiniz: Uygulamanızı](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)hassas bir şekilde ayarlama.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)

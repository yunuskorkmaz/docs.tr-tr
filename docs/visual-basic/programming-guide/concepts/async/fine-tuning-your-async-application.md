---
title: Async Uygulamanızda Hassas Ayar Yapma
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 51786993cf16cd12b39cde3d47832191b3fdca8d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345828"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Zaman uyumsuz uygulamanızda ince ayar yapma (Visual Basic)
<xref:System.Threading.Tasks.Task> türünün kullanılabilir hale getiren yöntemleri ve özellikleri kullanarak zaman uyumsuz uygulamalarınıza duyarlık ve esneklik ekleyebilirsiniz. Bu bölümdeki konularda, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>gibi <xref:System.Threading.CancellationToken> ve önemli `Task` yöntemleri kullanan örnekler gösterilmektedir.  
  
 `WhenAny` ve `WhenAll`kullanarak, birden çok görevi daha kolay başlatabilir ve tek bir görevi izleyerek tamamlanmasını deneyebilirsiniz.  
  
- `WhenAny`, bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     `WhenAny`kullanan örnekler için, bkz. [kalan zaman uyumsuz görevleri Iptal etme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)ve [birden çok zaman uyumsuz görev başlatma ve bunları tamamlandıklarında işleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`, bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve `WhenAll`kullanan bir örnek için, bkz. [nasıl yapılır: görev. WhenAll kullanarak zaman uyumsuz Izlenecek yolu genişletme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
- [Zaman uyumsuz bir görevi veya görev listesini Iptal edin (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Zaman uyumsuz görevleri bir süre sonra iptal et (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Kalan zaman uyumsuz görevleri bir süre tamamlandıktan sonra iptal et (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Birden çok zaman uyumsuz görev başlatın ve bunları tamamlarsa Işleyin (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Örnekleri çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.  
  
 Projeler, aşağıdaki görüntüde gösterildiği gibi, işlemi başlatan bir düğme ve bunu iptal eden bir düğme içeren bir kullanıcı arabirimi oluşturur. Düğmeler `startButton` ve `cancelButton`olarak adlandırılır.  
  
 ![Iptal düğmesi olan WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi ile iletişim kutusu")  
  
 Tüm Windows Presentation Foundation (WPF) projelerini [zaman uyumsuz örnekten indirebilirsiniz: uygulamanızı hassas bir şekilde ayarlama](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)

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
# <a name="fine-tuning-your-async-application-visual-basic"></a>(Visual Basic) Async uygulamanızda hassas ayar yapma
Özellikler ve yöntemler kullanarak zaman uyumsuz uygulamalarınıza kesinlik ve esneklik ekleyebilirsiniz, <xref:System.Threading.Tasks.Task> türü kullanıma sunar. Bu bölümdeki konular, kullanan örnekler <xref:System.Threading.CancellationToken> ve önemli `Task` gibi yöntemler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Kullanarak `WhenAny` ve `WhenAll`, daha kolay birden çok görev başlatabilir ve tek bir görevi izleyerek bunların tamamlanmasını bekler.  
  
- `WhenAny` bir koleksiyondaki herhangi bir görev tamamlandığında tamamlanan bir görev döndürür.  
  
     Kullanan örnekler `WhenAny`, bkz: [sonra bir tamamlandı (Visual Basic) kalan zaman uyumsuz görevleri iptal](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)ve [birden çok zaman uyumsuz görevleri başlatın ve işlemi bunları olarak bunlar tam (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` bir koleksiyondaki tüm görevler tamamlandığında tamamlanan bir görev döndürür.  
  
     Daha fazla bilgi ve kullanan bir örnek için `WhenAll`, bkz: [nasıl yapılır: (Visual Basic) Task.WhenAll kullanarak zaman uyumsuz izlenecek yolu genişletme](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Bu bölüm aşağıdaki örnekleri içerir.  
  
- [Zaman uyumsuz bir görev veya görevleri (Visual Basic) listesini iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [(Visual Basic) bir süre sonra zaman uyumsuz görevleri iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Tam (Visual Basic) biridir sonra geri kalan zaman uyumsuz görevleri iptal etme](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Birden çok zaman uyumsuz görev başlatma ve bunlar (Visual Basic) tamamlandıkça işleme](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Yeni bilgisayarınızda yüklü veya örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 yüklü olmalıdır.  
  
 Projeleri, işlem başlatan bir düğme ve aşağıda gösterildiği gibi iptal eden bir düğme içeren bir Arabirim oluşturur. Düğmeleri adlı `startButton` ve `cancelButton`.  
  
 ![İptal düğmesiyle okno WPF](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "iletişim kutusunu başlatma ve durdurma düğmesi")  
  
 Tam bir Windows Presentation Foundation (WPF) projelerden indirebileceğiniz [zaman uyumsuz örneği: Uygulamanızı ince ayar](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz programlama ile Async ve Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)

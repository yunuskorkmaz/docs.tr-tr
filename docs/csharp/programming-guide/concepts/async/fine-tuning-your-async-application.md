---
title: Async Uygulamanızda İnce Ayar (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970236"
---
# <a name="fine-tuning-your-async-application-c"></a>Async Uygulamanızda İnce Ayar (C#)
Async uygulamalarınız için, <xref:System.Threading.Tasks.Task> türün kullanıma sunduğu yöntemleri ve özellikleri kullanarak hassasiyet ve esneklik ekleyebilirsiniz. Bu bölümdeki konular, kullanılan <xref:System.Threading.CancellationToken> örnekleri `Task` ve <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> önemli <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>yöntemleri gösterir.  
  
 Kullanarak `WhenAny` ve, `WhenAll`daha kolay birden çok görevi başlatabilir ve tek bir görevi izleyerek bunların tamamlanmasını bekleyebilirsiniz.  
  
- `WhenAny`Bir koleksiyondaki herhangi bir görev tamamlandığında tamamlayan bir görev döndürür.  
  
     Kullanan `WhenAny`örnekler için bkz: [Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) ve [Birden Çok Async Görevi Başlatın ve Bunları Tamamlanında İşleyin (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll`Bir koleksiyondaki tüm görevler tamamlandığında tamamlayan bir görev döndürür.  
  
     Daha fazla bilgi ve `WhenAll`kullanan bir örnek için [Task.WhenAll (C#) kullanarak async walkthrough genişletmek için nasıl](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)bakın.
  
 Bu bölümde aşağıdaki örnekler yer almaktadır.  
  
- [Bir Async Görevi veya Görev Listesi (C#) iptal edin.](./cancel-an-async-task-or-a-list-of-tasks.md)  
  
- [Bir Süre Sonra Async Görevlerini İptal Etme (C#)](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [Bir Tamamlandıktan Sonra Kalan Async Görevlerini İptal Et (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Birden Çok Async Görevi Başlatın ve Tamamlanındıkları Gibi İşleyin (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Örnekleri çalıştırmak için Visual Studio 2012 veya daha yeni ve .NET Framework 4.5 veya daha yeni bilgisayarınıza yüklü olması gerekir.  
  
 Projeler, aşağıdaki resimde görüldüğü gibi işlemi başlatan bir düğme ve iptal eden bir düğme içeren bir ui oluşturur. Düğmeler adlandırılmış `startButton` `cancelButton`ve .  
  
 ![İptal düğmesi ile WPF penceresi](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Başlat ve Durdur düğmesi olan iletişim kutusu")  
  
 Windows Presentation Foundation (WPF) projelerinin tamamını [Async Sample: Fine Tuning Your Application'dan](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)indirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Async ve await ile Asynchronous Programlama (C#)](./index.md)

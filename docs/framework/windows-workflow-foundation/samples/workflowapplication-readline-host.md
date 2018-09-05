---
title: WorkflowApplication ReadLine konağı
ms.date: 03/30/2017
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
ms.openlocfilehash: 4388ff0285de58b0dc6f86af93aad84b2894373f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502941"
---
# <a name="workflowapplication-readline-host"></a>WorkflowApplication ReadLine konağı
Bu örnek, bir genel ReadLine ana bilgisayardır. Yük ve dahil edilen kullanarak herhangi bir iş akışı çalıştırma `ReadLine` etkinlik (veya dizelerle sürdürüldü yer işaretleri veri alma diğer etkinlikler, gibi). Çıktı `WriteLine` etkinlik veya herhangi bir şey yazma <xref:System.Activities.Statements.WriteLine.TextWriter%2A> uzantısı, ana pencereyi yönlendirilir. Örneği boşta olduğunda, bu örnek için mevcut yer işaretlerini bir birleşik giriş kutusunda görünür. Bir yer işaretini seçerek, metin giriş yapma ve sürdürme yer işareti düğmesine basarak iş akışlarının yürütülmesini devam eder. İptal etme, iptal etmek veya seçili bir iş akışı sonlandırılmak. Kalıcılık varsayılan olarak açık – konağı kapatın ve yeniden getirmek ve örnek listesi veritabanında depolanan örnekleri ile doldurulur. Kullanılan izleme çıktısına <xref:System.Activities.WorkflowApplication>-düzeyindeki olayları etkinlik düzeyinde ayrıntılı izleme ekleme seçeneğine sahip bir konağa.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu konak için iki katmanı vardır: Görünüm ve örnek Yöneticisi. Görünüm oluşan `HostView` ve `WorkflowApplicationInfo` sınıfları. Bu konak için genel düzen içindir `HostView` kullanıcıya kullanılabilir seçenekleri görüntülemek için sınıf temel alarak `WorkflowApplicationInfo` makul temsil ettikleri örnekleri ile eşitlemede tutulduğu nesneleri. Örnek Yöneticisi katman oluşan `WorkflowApplicationManager` tüm konak iletişim çekirdeği olan bir sınıfı ve `WorkflowDefinitionExtension` örneği ve ile başlatıldı program tanımı arasındaki ilişkiyi devam ederse sınıfı ve diğer birkaç sınıfları. `HostView` Çağrıları üzerinde işlemler denetim `WorkflowApplicationManager`. Bu çağrılar duyarlı kullanıcı arabirimi korumak için genellikle zaman uyumsuz olması. Zaman uyumsuz tam çağırdığında `WorkflowApplicationManager` iyi tanımlanmış bir arabirim görünümü katmana geri çağrılar (`IHostView`). `HostView` Sınıfı çoğunlukla bu çağrılarından gönderir `WorkflowApplicationManager` kullanıcı arabirimi iş parçacığına sınıfı. Metin yazı, iş parçacığı açısından güvenli yapılır <xref:System.Activities.Statements.WriteLine.TextWriter%2A> tarafından sağlanan nesneler `HostView` sınıfı. Kullanıcı arabirimi olayları gereken tek şey değildir. <xref:System.Activities.WorkflowApplication> Nesneleri ayrıca sinyal `WorkflowApplicationManager` zaman gitmeleri `Idle`, `Complete`, veya `Aborted`, örneğin. `WorkflowApplicationManager` Sınıf temizleme gönderme veya konağa iş güncelleştirme olay iş parçacığından alır.  
  
 Kaydı başlatmak için kullanılan dosyanın bir <xref:System.Activities.WorkflowApplication> tarafından kolaylaştırılan `WorkflowDefinitionExtension` sınıfı. Bunu uygulayan <xref:System.Activities.Persistence.PersistenceIOParticipant> kalıcı katılır ve iş akışı tanımı yolu kalıcı hale getirmek için arabirim.  
  
 `WorkflowApplicationManager.Load` Yöntemi tamamlanmamış yükleme için gerekli iş akışı programları örneklemek için saklı yolunu kullanır <xref:System.Activities.WorkflowApplication> nesneleri.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Bu örnek, yüklenecek SQL Express gerektirir. SQL Express ile birlikte gelen [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Visual Studio 2010 Komut istemi açın.  
  
3.  Örnek dizine (\WF\Basic\Execution\ControllingWorkflowApplications) gidin ve CreateInstanceStore.cmd çalıştırın.  
  
4.  SQL Server 2008 Express varsayılan örneğinde veritabanı oluşturma CreateInstanceStore.cmd betik çalışır. Veritabanını farklı bir örneğinde yüklemek istiyorsanız, bunu yapmak için komut dosyasını değiştirin.  
  
5.  WorkflowApplicationReadLineHost projeyi derleyin ve komut satırından çalıştırın.  
  
6.  Kalıcılık isteğe bağlı olarak çalışmaya sonra açıp kapatabilirsiniz. Ayrıca, isteğe bağlı olarak ayrıntılı etkinlik açıp izleme kapatabilirsiniz.  
  
7.  Yanındaki üç nokta düğmesine basın **çalıştırma** bir XAML dosyasında tanımlanan bir iş akışı için Gözat düğmesine  
  
     İki örnek SampleWorkflows klasörü altında bulunabilir. Parallel1.xaml örnek boşta gider.  
  
8.  Bir örnek seçtikten sonra basın **çalıştırma** düğmesi.  
  
9. Varsa veya iş akışı boş olduğunda **yer işaretleri** birleşik giriş kutusu kullanılabilir yer işaretleri ile doldurulur.  
  
10. Bu noktada yer imi sürdürme iptal etme, iptal etmek veya iş akışı sonlandırma seçenekleridir. Ayrıca, konak kapatın ve yeniden başlatın. Kalıcılık üzerinde bırakılırsa örnekleri kapanışında kaldırıldı ve Başlat'kurmak yeniden.  
  
     Bir yer işareti sürdürmek için istenen yer işareti Seç, birleşik giriş kutusu ve ENTER tuşuna yanındaki metin kutusuna bir değer yazın **sürdürme yer işareti**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Örnek deposu veritabanını kaldırmak için  
  
1.  Visual Studio 2010 Komut istemi açın.  
  
2.  Örnek dizine (\WF\Basic\Execution\ControllingWorkflowApplications) gidin ve RemoveInstanceStore.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`
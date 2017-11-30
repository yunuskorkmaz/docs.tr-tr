---
title: WorkflowApplication ReadLine ana bilgisayar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5efe784f434ff357120343061c1c4b9447cc8cd1
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="workflowapplication-readline-host"></a>WorkflowApplication ReadLine ana bilgisayar
Bu örnek bir genel ReadLine ana bilgisayardır. Yük ve birlikte kullanarak tüm iş akışını çalıştırma `ReadLine` etkinlik (veya bu gibi veri yer işaretleri dizelerle sürdürüldü almanız diğer etkinlikler). Çıktı `WriteLine` etkinlik veya herhangi bir şeyi yazma <xref:System.Activities.Statements.WriteLine.TextWriter%2A> uzantısı konak penceresine yönlendirilir. Bir örnek boşta olduğunda, bu örnek için kullanılabilir yer işaretleri açılan kutuda görünür. Yer işareti seçerek, bazı metinleri giriş yapma ve sürdürme yer işareti düğmesine basarak iş akışının yürütülmesini devam eder. İptal etmek, iptal etmek veya seçili bir iş akışı sonlandırılmak. Kalıcılık varsayılan olarak açık – konak kapatın ve geri getirmek ve örnek listesi veritabanında depolanan örnekleri ile doldurulur. İzleme kullanılır çıktıya <xref:System.Activities.WorkflowApplication>-düzeyinde etkinlik düzeyinde ayrıntılı izleme ekleme seçeneğine sahip bir konağa olayları.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu konak iki katmanı vardır: Görünüm ve örnek Yöneticisi. Görünüm oluşan `HostView` ve `WorkflowApplicationInfo` sınıfları. Bu konak için genel deseni içindir `HostView` kullanılabilir seçenekler kullanıcıya görüntülenecek sınıf temel alarak `WorkflowApplicationInfo` temsil ettikleri örnekleri ile eşitleme makul tutulan nesneleri. Örnek Yöneticisi katman oluşan `WorkflowApplicationManager` tüm konak iletişimler çekirdek olan sınıf ve `WorkflowDefinitionExtension` örneği ile başlatıldı program tanımı arasındaki ilişki devam ederse sınıfı ve diğer birkaç sınıfları. `HostView` Çağrıları üzerinde işlemlerini kontrol `WorkflowApplicationManager`. Bu çağrı bir Esnek kullanıcı arabirimi korumak için genellikle uyumsuzdur. Zaman uyumsuz tam, çağırdığında `WorkflowApplicationManager` iyi tanımlanmış bir arabirimi aracılığıyla görünüm katmana geri çağrılar (`IHostView`). `HostView` Sınıfı çoğunlukla bu çağrılarından gönderir `WorkflowApplicationManager` kullanıcı arabirimi iş parçacığı sınıfı. Metin yazma, iş parçacığı açısından güvenli yapılır <xref:System.Activities.Statements.WriteLine.TextWriter%2A> tarafından sağlanan nesnelerini `HostView` sınıfı. Kullanıcı arabirimi olayları oluşturma tek şey değil. <xref:System.Activities.WorkflowApplication> Nesneler de sinyal `WorkflowApplicationManager` zaman Git `Idle`, `Complete`, veya `Aborted`, örneğin. `WorkflowApplicationManager` Sınıfı temizleme gönderme veya iş konağa güncelleştirme olay iş parçacığı alır.  
  
 Kaydı başlatmak için kullanılan dosya, bir <xref:System.Activities.WorkflowApplication> da sayesinde kolaylaşır `WorkflowDefinitionExtension` sınıfı. Bunu uygulayan <xref:System.Activities.Persistence.PersistenceIOParticipant> içinde Kalıcılık katılmak ve iş akışı tanımı yoluna kalıcı hale getirmek için arabirim.  
  
 `WorkflowApplicationManager.Load` Yöntemi yüklenmesi tamamlanmamış gerekli iş akışı programları örneği oluşturmak için depolanmış yolunu kullanır <xref:System.Activities.WorkflowApplication> nesneleri.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Bu örnek, yüklenecek SQL Express gerektirir. SQL Express ile birlikte gelen [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Visual Studio 2010 Komut istemi açın.  
  
3.  Örnek dizine (\WF\Basic\Execution\ControllingWorkflowApplications) gidin ve CreateInstanceStore.cmd çalıştırın.  
  
4.  CreateInstanceStore.cmd komut dosyası, SQL Server 2008 Express varsayılan örneğinde veritabanı oluşturma dener. Veritabanını farklı bir örneğinde yüklemek istiyorsanız, bunu yapmak için komut dosyasını değiştirin.  
  
5.  WorkflowApplicationReadLineHost projeyi derleyin ve komut satırından çalıştırın.  
  
6.  Çalışan sonra kapatma veya isteğe bağlı olarak Kalıcılık kapatabilirsiniz. Ayrıca, isteğe bağlı olarak ayrıntılı etkinlik açmak veya kapatmak izlemeyi açabilirsiniz.  
  
7.  Yanındaki üç nokta düğmesine basın **çalıştırmak** XAML dosyasında tanımlanan iş akışı gözatmak için düğmeyi  
  
     İki örnek SampleWorkflows klasörü altında bulunabilir. Parallel1.xaml örnek boşta gider.  
  
8.  Bir örnek seçildikten sonra basın **çalıştırmak** düğmesi.  
  
9. Varsa veya iş akışının boşta gittiğinde **yer işaretleri** birleşik giriş kutusu kullanılabilir yer işaretleri ile doldurulur.  
  
10. Bu noktada yer işareti sürdürmek, iptal, durdurmak veya iş akışının sonlandırmak için seçeneklerdir. Ana bilgisayar kapatın ve yeniden başlatın. Kalıcılık üzerinde bırakılırsa örnekleri kapanışında kaldırıldı ve yukarı başlangıç yeniden.  
  
     Yer işareti sürdürmek için istenen yer işaretini seçin, birleşik giriş kutusu ve tuşuna yanındaki metin kutusuna bir değer yazın **sürdürme yer işareti**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Örnek deposu veritabanı kaldırmak için  
  
1.  Visual Studio 2010 Komut istemi açın.  
  
2.  Örnek dizine (\WF\Basic\Execution\ControllingWorkflowApplications) gidin ve RemoveInstanceStore.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`
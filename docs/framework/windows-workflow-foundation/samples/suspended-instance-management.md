---
title: "Askıya alınmış örnek Yönetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24c94f93524f6b31b622c527da068379ce7e724d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="suspended-instance-management"></a>Askıya alınmış örnek Yönetimi
Bu örnek, askıya alınan iş akışı örnekleri yönetmek gösterilmiştir.  İçin varsayılan eylem <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> olan `AbandonAndSuspend`. Varsayılan olarak, içinde bir iş akışı örneğinden oluşturulan işlenmeyen özel durumları barındırılan yani <xref:System.ServiceModel.WorkflowServiceHost> örneği (terk) bellekten çıkarılması ve dayanıklı ve kalıcı örneğinin sürümü, askıya alındı olarak işaretlenmesine neden olacak. Askıya alınan iş akışı örneği çalıştırabilir ve onu unsuspended kadar olmaz.  
  
 Komut satırı yardımcı programını askıya alınmış örnekleri için sorgu ve kullanıcı sürdürün veya örnek sonlandırmak için seçenek sunmak amacıyla nasıl nasıl uygulanabilir örnek gösterir. Bu örnekte, bir iş akışı hizmeti bilerek, askıya duruma neden olan bir özel durum oluşturur. Komut satırı yardımcı programı daha sonra örnek için sorgu ve daha sonra sürdürün veya örnek sonlandırmak için kullanılabilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.WorkflowServiceHost>ile <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> içinde [!INCLUDE[wf](../../../../includes/wf-md.md)].  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte uygulanan komut satırı yardımcı programı içinde birlikte gelen SQL örneği mağaza uygulamasına belirli [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Özel bir örnek deposuna uygulanmasına sahip sonra değiştirerek bu yardımcı program uyarlayabilirsiniz `WorkflowInstanceCommand` örnek uygulamalarında örneği deponuza belirli uygulamaları.  
  
 Sağlanan uygulama SQL komutlarını doğrudan askıya alınmış örneklerini listelemek için SQL örneği depo çalıştırır ve kullanır. bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> eklenen <xref:System.ServiceModel.WorkflowServiceHost> sürdürün veya örnekleri sonlandırmak için.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Bu örnek, aşağıdaki Windows bileşenleri etkin olmasını gerektirir:  
  
    1.  Microsoft Message sıraları (MSMQ) sunucusu  
  
    2.  SQL Server Express  
  
2.  SQL Server veritabanı ayarlama.  
  
    1.  Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi, aşağıdaki SuspendedInstanceManagement örnek dizinden "setup.cmd" çalıştırın:  
  
        1.  SQL Server Express kullanarak bir Kalıcılık veritabanı oluşturur. Bırakılan ve yeniden oluşturulması Kalıcılık veritabanı zaten varsa  
  
        2.  Veritabanı kalıcılığı için ayarlar.  
  
        3.  IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\Network Service kalıcılığı için veritabanı ayarlarken tanımlandı InstanceStoreUsers rolüne ekler.  
  
3.  Hizmet sırasını ayarlayın.  
  
    1.  İçinde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], sağ **SampleWorkflowApp** proje ve tıklatın **başlangıç projesi olarak ayarla**.  
  
    2.  Derleme ve tuşlarına basarak SampleWorkflowApp çalıştırma **F5**. Bu, gerekli sıra oluşturur.  
  
    3.  Tuşuna **Enter** SampleWorkflowApp durdurmak için.  
  
    4.  Bir komut isteminden Compmgmt.msc çalıştırarak Bilgisayar Yönetimi konsolunu açın.  
  
    5.  Genişletme **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.  
  
    6.  Sağ tıklayın **ReceiveTx** sıraya ve seçin **özellikleri**.  
  
    7.  Seçin **güvenlik** sekmesinde ve izin **herkesin** izinlerine sahip olmasını **İleti Al**, **iletiye**, ve  **İleti gönderme**.  
  
4.  Şimdi, örnek çalıştırın.  
  
    1.  İçinde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SampleWorkflowApp projeyi yeniden tuşlarına basarak hata ayıklama olmadan çalıştırma **Ctrl + F5**. İki uç nokta adresleri konsol penceresinde yazdırılan: uygulama uç noktası için bir tane ve öğesinden sonra diğer <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>. Bir iş akışı örneği sonra oluşturulur ve bu örnek için kayıtları izleme konsol penceresinde görünür. İş akışı örneği askıya ve iptal örneği neden olan bir özel durum oluşturur.  
  
    2.  Komut satırı yardımcı programı daha sonra başka bir işlem bu örnekler hiçbirinde yapmanıza için kullanılabilir. Komut satırı bağımsız değişkenleri için söz dizimi aşağıdaki gibidir:  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         Desteklenen komutlar: `Query`, `Resume`, ve `Terminate`.  InstanceId anahtar yalnızca gerekli olan `Resume` ve `Terminate` işlemleri.  
  
#### <a name="to-cleanup-optional"></a>Temizleme (isteğe bağlı)  
  
1.  Gelen Compmgmt.msc çalıştırarak Bilgisayar Yönetimi konsolunu açın bir `vs2010` komut istemi.  
  
2.  Genişletme **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.  
  
3.  Silme **ReceiveTx** sırası.  
  
4.  Kalıcılık veritabanını kaldırmak için cleanup.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`

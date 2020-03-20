---
title: Askıya Alınmış Örnek Yönetimi
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 784ec3cdda8eedb188c3c776ed412ea40baf37ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182797"
---
# <a name="suspended-instance-management"></a>Askıya Alınmış Örnek Yönetimi
Bu örnek, askıya alınan iş akışı örneklerinin nasıl yönetileceğiaçık.  Bunun için <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> varsayılan `AbandonAndSuspend`eylem. Bu, varsayılan olarak, barındırılan bir iş akışı örneğinden atılan işlenmemiş özel durumların örneğin bellekten atılmasına (terk edilmiş) ve örneğin kalıcı/kalıcı sürümünün askıya alınmış olarak işaretlenecek olmasına neden <xref:System.ServiceModel.WorkflowServiceHost> olacağı anlamına gelir. Askıya alınan iş akışı örneği askıya alınmadan çalıştırılamaz.

 Örnek, askıya alınan örnekleri sorgulamak için komut satırı yardımcı lığının nasıl uygulanabileceğini ve kullanıcıya örneği devam ettirme veya sonlandırma seçeneğinin nasıl verileceği gösterilmektedir. Bu örnekte, bir iş akışı hizmeti kasıtlı olarak bir özel durum atarak askıya alınmasına neden olur. Komut satırı yardımcı programı daha sonra örnek için sorgu ve daha sonra devam veya örnek sonlandırmak için kullanılabilir.

## <a name="demonstrates"></a>Gösteriler
 <xref:System.ServiceModel.WorkflowServiceHost>ve Windows İş Akışı Temeli (WF) ile. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>

## <a name="discussion"></a>Tartışma
 Bu örnekte uygulanan komut satırı yardımcı programı, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]'de bulunan SQL örnek deposu uygulamasına özgüdür. Örnek deposunun özel bir uygulaması varsa, örnek mağazanıza özgü `WorkflowInstanceCommand` uygulamalarla örnekteki uygulamaları değiştirerek bu yardımcı programı uyarlayabilirsiniz.

 Sağlanan uygulama, askıya alınan örnekleri listelemek için doğrudan SQL örnek deposuna <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> karşı SQL <xref:System.ServiceModel.WorkflowServiceHost> komutlarını çalıştırıyor ve örnekleri devam ettirmek veya sonlandırmak için eklenen ekine dayanır.

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Bu örnek, aşağıdaki Windows bileşenlerinin etkin olmasını gerektirir:

    1. Microsoft İleti Kuyrukları (MSMQ) Sunucusu

    2. SQL Server Express

2. SQL Server veritabanını ayarlayın.

    1. Visual Studio 2010 komut isteminden, SuspendedInstanceManagement örnek dizininden aşağıdakileri yapan "setup.cmd"yi çalıştırın:

        1. SQL Server Express kullanarak kalıcıbir veritabanı oluşturur. Kalıcılık veritabanı zaten varsa, bırakılır ve yeniden oluşturulur

        2. Veritabanını kalıcılık için ayarlar.

        3. Veritabanını kalıcılık için ayarlarken tanımlanan InstanceStoreUsers rolüne IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\Network Service ekler.

3. Servis sırasını ayarlayın.

    1. Visual Studio 2010'da **SampleWorkflowApp** projesine sağ tıklayın ve **Başlangıç Projesi olarak ayarla'yı**tıklatın.

    2. **F5**tuşuna basarak SampleWorkflowApp'ı derleyip çalıştırın. Bu gerekli sırayı oluşturur.

    3. SampleWorkflowApp'ı durdurmak için **Enter** tuşuna basın.

    4. Compmgmt.msc komut isteminden çalıştırarak Bilgisayar Yönetimi konsolunu açın.

    5. **Hizmet ve Uygulamaları**Genişlet , İleti **Sırası**, **Özel Kuyruklar**.

    6. **ReceiveTx** kuyruğunu sağ tıklatın ve **Özellikler'i**seçin.

    7. **Güvenlik** sekmesini seçin ve **Herkesin** **İleti Alma,** **Gözetleme İletisi**ve **İleti Gönderme**İzni almasına izin verin.

4. Şimdi, örneği çalıştırın.

    1. Visual Studio 2010'da, **Ctrl+F5**tuşuna basarak hata ayıklama yapmadan SampleWorkflowApp projesini tekrar çalıştırın. Konsol penceresine iki uç nokta adresi yazdırılır: biri uygulama bitiş noktası <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>için, diğeri . Daha sonra bir iş akışı örneği oluşturulur ve bu örneğin izleme kayıtları konsol penceresinde görünür. İş akışı örneği, örneğin askıya alınmasına ve iptal edilmesine neden olan bir özel durum oluşturur.

    2. Komut satırı yardımcı programı daha sonra bu örneklerden herhangi biri üzerinde daha fazla eylem yapmak için kullanılabilir. Komut satırı bağımsız değişkenleri için sözdizimi aşağıdaki gibidir:

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         Desteklenen komutlar `Query`şunlardır: `Resume`, `Terminate`, ve .  InstanceId anahtarı yalnızca işlemler `Resume` `Terminate` için gereklidir.

#### <a name="to-cleanup-optional"></a>Temizlemek için (İsteğe Bağlı)

1. Compmgmt.msc komut isteminden çalıştırarak `vs2010` Bilgisayar Yönetimi konsolunu açın.

2. **Hizmet ve Uygulamaları**Genişlet , İleti **Sırası**, **Özel Kuyruklar**.

3. **ReceiveTx** sırasını silin.

4. Kalıcılık veritabanını kaldırmak için cleanup.cmd'yi çalıştırın.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`

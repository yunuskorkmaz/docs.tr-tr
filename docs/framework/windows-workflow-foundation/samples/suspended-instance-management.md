---
title: Askıya Alınmış Örnek Yönetimi
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 620cd2299a3b08ee9330e13830c714c5d0ebb068
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293656"
---
# <a name="suspended-instance-management"></a>Askıya Alınmış Örnek Yönetimi

Bu örnek, askıya alınan iş akışı örneklerinin nasıl yönetileceğini gösterir.  İçin varsayılan eylem <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> `AbandonAndSuspend` . Bu, varsayılan olarak, ' de barındırılan bir iş akışı örneğinden oluşturulan işlenmemiş özel durumların, <xref:System.ServiceModel.WorkflowServiceHost> Örneğin bellekten (terk) ve askıya alınmış olarak işaretlenmesine neden olan örneğinin kalıcı/kalıcı sürümü tarafından atılmasına neden olur. Askıya alınmış bir iş akışı örneği askıya alınana kadar çalıştırılamaz.

 Örnek, askıya alınmış örnekleri sorgulamak için bir komut satırı yardımcı programının nasıl uygulankullanılabileceğini ve kullanıcıya örneği yeniden başlatma veya sonlandırma seçeneği nasıl sunılacağını gösterir. Bu örnekte, bir iş akışı hizmeti kasıtlı olarak bir özel durum oluşturur ve askıya alınmasına neden olur. Daha sonra komut satırı yardımcı programı örneği sorgulamak için kullanılabilir ve ardından örneği sürdürür veya sonlandırır.

## <a name="demonstrates"></a>Gösteriler

 <xref:System.ServiceModel.WorkflowServiceHost><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> WINDOWS Workflow FOUNDATION (WF) ile.

## <a name="discussion"></a>Tartışma

 Bu örnekte uygulanan komut satırı yardımcı programı, içinde yer alan SQL örnek deposu uygulamasına özgüdür [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] . Örnek deposunun özel bir uygulamasına sahipseniz, `WorkflowInstanceCommand` örnekteki uygulamaları örnek deponuza özgü uygulamalarla değiştirerek bu yardımcı programı uyarlayabilirsiniz.

 Belirtilen uygulama, askıya alınmış örnekleri listelemek için doğrudan SQL örneği deposunda SQL komutları çalıştırır ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> <xref:System.ServiceModel.WorkflowServiceHost> örnekleri yeniden başlatmak veya sonlandırmak için öğesine eklenen öğesine bağımlıdır.

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Bu örnek, aşağıdaki Windows bileşenlerinin etkinleştirilmesini gerektirir:

    1. Microsoft Ileti sıraları (MSMQ) sunucusu

    2. SQL Server Express

2. SQL Server veritabanını ayarlayın.

    1. Visual Studio 2010 komut isteminden, SuspendedInstanceManagement örnek dizininden "Setup. cmd" komutunu çalıştırın ve şunları yapın:

        1. SQL Server Express kullanarak bir Kalıcılık veritabanı oluşturur. Kalıcılık veritabanı zaten varsa, bırakılır ve yeniden oluşturulur

        2. Veritabanını kalıcılık için ayarlar.

        3. Veritabanı kalıcılığı için ayarlarken tanımlanmış olan InstanceStoreUsers rolüne IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\Network Service ekler.

3. Hizmet kuyruğunu ayarlayın.

    1. Visual Studio 2010 ' de **SampleWorkflowApp** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' ya tıklayın.

    2. **F5** tuşuna basarak SampleWorkflowApp 'i derleyin ve çalıştırın. Bu işlem gerekli kuyruğu oluşturur.

    3. SampleWorkflowApp 'i durdurmak için **ENTER** tuşuna basın.

    4. Bir komut isteminden compmgmt. msc ' i çalıştırarak Bilgisayar Yönetimi konsolunu açın.

    5. **Hizmet ve uygulamalar**, **Message Queuing**, **özel kuyruklar**' ı genişletin.

    6. **ReceiveTx** kuyruğuna sağ tıklayın ve **Özellikler**' i seçin.

    7. **Güvenlik** sekmesini seçin ve **herkesin** **ileti alma**, **iletiye göz atma** ve **ileti gönderme** izinlerine sahip olmasını sağlar.

4. Şimdi, örneği çalıştırın.

    1. Visual Studio 2010 ' de, SampleWorkflowApp projesini hata ayıklama olmadan yeniden çalıştırarak **CTRL + F5** tuşuna basın. İki uç nokta adresi konsol penceresinde yazdırılır: bir uygulama uç noktası ve sonrasında diğeri <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> . Daha sonra bir iş akışı örneği oluşturulur ve bu örneğe ilişkin izleme kayıtları konsol penceresinde görünür. İş akışı örneği, örneğin askıya alınmasına ve iptal olmasına neden olan bir özel durum oluşturur.

    2. Komut satırı yardımcı programı daha sonra bu örneklerden herhangi birinde daha fazla işlem yapmak için kullanılabilir. Komut satırı bağımsız değişkenlerinin sözdizimi şöyledir::

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         Desteklenen komutlar şunlardır: `Query` , `Resume` , ve `Terminate` .  InstanceId anahtarı yalnızca ve işlemleri için gereklidir `Resume` `Terminate` .

#### <a name="to-cleanup-optional"></a>Temizlemek için (Isteğe bağlı)

1. Bir komut isteminden compmgmt. msc ' i çalıştırarak Bilgisayar Yönetimi konsolunu açın `vs2010` .

2. **Hizmet ve uygulamalar**, **Message Queuing**, **özel kuyruklar**' ı genişletin.

3. **ReceiveTx** kuyruğunu silin.

4. Kalıcılık veritabanını kaldırmak için Cleanup. cmd ' yi çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`

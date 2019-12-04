---
title: Askıya Alınmış Örnek Yönetimi
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 3f1f4f8edcbe0e05067d3ca739ef3d5f4fe4d798
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715938"
---
# <a name="suspended-instance-management"></a>Askıya Alınmış Örnek Yönetimi
Bu örnek, askıya alınan iş akışı örneklerinin nasıl yönetileceğini gösterir.  <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> için varsayılan eylem `AbandonAndSuspend`. Bu, varsayılan olarak, <xref:System.ServiceModel.WorkflowServiceHost> barındırılan bir iş akışı örneğinden oluşturulan işlenmemiş özel durumların, örneğin bellekten (terk) ve askıya alınmış olarak işaretlenmesi için, örneğin, kalıcı/kalıcı hale gelmesine neden olacağı anlamına gelir. Askıya alınmış bir iş akışı örneği askıya alınana kadar çalıştırılamaz.

 Örnek, askıya alınmış örnekleri sorgulamak için bir komut satırı yardımcı programının nasıl uygulankullanılabileceğini ve kullanıcıya örneği yeniden başlatma veya sonlandırma seçeneği nasıl sunılacağını gösterir. Bu örnekte, bir iş akışı hizmeti kasıtlı olarak bir özel durum oluşturur ve askıya alınmasına neden olur. Daha sonra komut satırı yardımcı programı örneği sorgulamak için kullanılabilir ve ardından örneği sürdürür veya sonlandırır.

## <a name="demonstrates"></a>Gösterir
 Windows Workflow Foundation (WF) <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> <xref:System.ServiceModel.WorkflowServiceHost>.

## <a name="discussion"></a>Tartışma
 Bu örnekte uygulanan komut satırı yardımcı programı, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]ile birlikte gelen SQL örnek deposu uygulamasına özgüdür. Örnek deposunun özel bir uygulamasına sahipseniz, örnekteki `WorkflowInstanceCommand` uygulamalarını örnek deponuza özgü uygulamalarla değiştirerek bu yardımcı programı uyarlayabilirsiniz.

 Belirtilen uygulama, askıya alınmış örnekleri listelemek için doğrudan SQL örneği deposunda SQL komutları çalıştırır ve örnekleri yeniden başlatmak veya sonlandırmak için <xref:System.ServiceModel.WorkflowServiceHost> eklenmiş bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> kullanır.

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

    2. **F5**tuşuna basarak SampleWorkflowApp 'i derleyin ve çalıştırın. Bu işlem gerekli kuyruğu oluşturur.

    3. SampleWorkflowApp 'i durdurmak için **ENTER** tuşuna basın.

    4. Bir komut isteminden compmgmt. msc ' i çalıştırarak Bilgisayar Yönetimi konsolunu açın.

    5. **Hizmet ve uygulamalar**, **Message Queuing**, **özel kuyruklar**' ı genişletin.

    6. **ReceiveTx** kuyruğuna sağ tıklayın ve **Özellikler**' i seçin.

    7. **Güvenlik** sekmesini seçin ve **herkesin** **ileti alma**, **iletiye göz atma**ve **ileti gönderme**izinlerine sahip olmasını sağlar.

4. Şimdi, örneği çalıştırın.

    1. Visual Studio 2010 ' de, SampleWorkflowApp projesini hata ayıklama olmadan yeniden çalıştırarak **CTRL + F5**tuşuna basın. İki uç nokta adresi konsol penceresinde yazdırılır: bir uygulama uç noktası ve ardından <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>diğeri. Daha sonra bir iş akışı örneği oluşturulur ve bu örneğe ilişkin izleme kayıtları konsol penceresinde görünür. İş akışı örneği, örneğin askıya alınmasına ve iptal olmasına neden olan bir özel durum oluşturur.

    2. Komut satırı yardımcı programı daha sonra bu örneklerden herhangi birinde daha fazla işlem yapmak için kullanılabilir. Komut satırı bağımsız değişkenlerinin sözdizimi şöyledir::

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         Desteklenen komutlar şunlardır: `Query`, `Resume`ve `Terminate`.  InstanceId anahtarı yalnızca `Resume` ve `Terminate` işlemleri için gereklidir.

#### <a name="to-cleanup-optional"></a>Temizlemek için (Isteğe bağlı)

1. `vs2010` komut isteminden compmgmt. msc ' i çalıştırarak Bilgisayar Yönetimi konsolunu açın.

2. **Hizmet ve uygulamalar**, **Message Queuing**, **özel kuyruklar**' ı genişletin.

3. **ReceiveTx** kuyruğunu silin.

4. Kalıcılık veritabanını kaldırmak için Cleanup. cmd ' yi çalıştırın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`

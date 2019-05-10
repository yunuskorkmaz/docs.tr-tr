---
title: Askıya Alınmış Örnek Yönetimi
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: c23d2dfd48ecb57a3fb418734c916586178986e9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622413"
---
# <a name="suspended-instance-management"></a>Askıya Alınmış Örnek Yönetimi
Bu örnek, askıya alınmış iş akışı örneğini yönetmek nasıl gösterir.  İçin varsayılan eylem <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> olduğu `AbandonAndSuspend`. Varsayılan olarak, bir iş akışı örneğinden oluşturulan yakalanamayan özel durum barındırılan yani <xref:System.ServiceModel.WorkflowServiceHost> örneği (terk) bellekten çıkarılması ve dayanıklı ve kalıcı örneğinin sürümü, askıya alındı olarak işaretlenmesine neden olur. Askıya alınan iş akışı örneği adlı aşana kadar çalıştırmak mümkün olmayacaktır.

 Örnek sorgu askıya alınmış örnekleri için ve nasıl sürdürün veya örneği sonlandırma seçeneği kullanıcıya vermek için bir komut satırı yardımcı programını nasıl uygulanabileceği gösterilmektedir. Bu örnekte, bir iş akışı hizmeti kasıtlı olarak askıya için neden bir özel durum oluşturur. Komut satırı yardımcı programını, ardından örnek için sorgulama ve daha sonra sürdürün veya örneği sonlandırmak için kullanılabilir.

## <a name="demonstrates"></a>Gösteriler
 <xref:System.ServiceModel.WorkflowServiceHost> ile <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> ve <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> içinde Windows Workflow Foundation (WF).

## <a name="discussion"></a>Tartışma
 Bu örnekte uygulanan komut satırı yardımcı programını içinde birlikte gelen SQL örneği mağazası uygulamalarına özeldir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Örnek deposuna bir özel uygulanışı olması durumunda değiştirerek bu yardımcı program uyarlayabilirsiniz `WorkflowInstanceCommand` örnek uygulamalarında, örnek deposuna belirli uygulamaları.

 Sağlanan uygulama doğrudan askıya alınmış örneklerini listelemek için SQL örneği depo SQL komutlarını çalıştırır ve kullanır bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> eklenen <xref:System.ServiceModel.WorkflowServiceHost> sürdürün veya örnekleri sonlandırmak için.

#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1. Bu örnek, aşağıdaki Windows bileşenleri etkin olmasını gerektirir:

    1. Microsoft ileti kuyrukları (MSMQ) sunucusu

    2. SQL Server Express

2. SQL Server veritabanı ayarlama.

    1. Bir Visual Studio 2010 komut isteminden "Setup.cmd'yi" şunları yapar SuspendedInstanceManagement örnek dizinden çalıştırın:

        1. SQL Server Express kullanarak bir Kalıcılık veritabanı oluşturur. Bırakılan ve yeniden oluşturulduğunda Kalıcılık veritabanı zaten varsa

        2. Kalıcılık veritabanı ayarlar.

        3. IIS APPPOOL\DefaultAppPool ve NT AUTHORITY\NETWORK SERVICE Kalıcılık veritabanı ayarlarken tanımlandı InstanceStoreUsers rolüne ekler.

3. Hizmet sırasını ayarlayın.

    1. Visual Studio 2010'da, sağ **SampleWorkflowApp** projesine **başlangıç projesi olarak ayarla**.

    2. Derleme ve tuşlarına basarak SampleWorkflowApp çalıştırma **F5**. Bu gerekli bir kuyruk oluşturur.

    3. Tuşuna **Enter** SampleWorkflowApp durdurmak için.

    4. Bir komut istemi'nden Compmgmt.msc çalıştırarak Bilgisayar Yönetimi konsolunu açın.

    5. Genişletin **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.

    6. Sağ tıklayın **ReceiveTx** seçin ve sıra **özellikleri**.

    7. Seçin **güvenlik** sekmesini ve izin **herkes** izinlerine sahip olmasını **İleti Al**, **iletiye**, ve  **İleti gönderme**.

4. Şimdi, örnek çalıştırın.

    1. Visual Studio 2010'da tuşuna basarak hata ayıklama olmadan SampleWorkflowApp projeyi yeniden çalıştırın. **Ctrl + F5**. İki uç nokta adresleri konsol penceresinde yazdırılır: uygulama uç noktası için bir tane ve gelen diğer <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>. Bir iş akışı örneği sonra oluşturulur ve bu örnek için kayıtları izleme konsol penceresinde görünür. İş akışı örneği askıya ve iptal örneği neden olan bir özel durum oluşturur.

    2. Komut satırı yardımcı programını, ardından Bu örneklerin herhangi birine üzerinde daha fazla eylemi gerçekleştirmek için kullanılabilir. Komut satırı bağımsız değişkenleri için sözdizimi aşağıdaki gibidir:

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         Desteklenen komutlar: `Query`, `Resume`, ve `Terminate`.  InstanceId geçiş için yalnızca gerekli `Resume` ve `Terminate` operations.

#### <a name="to-cleanup-optional"></a>(İsteğe bağlı) temizlemek için

1. Gelen Compmgmt.msc çalıştırarak Bilgisayar Yönetimi konsolunu açın bir `vs2010` komut istemi.

2. Genişletin **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.

3. Silme **ReceiveTx** kuyruk.

4. Kalıcılık veritabanı kaldırmak için cleanup.cmd çalıştırın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`

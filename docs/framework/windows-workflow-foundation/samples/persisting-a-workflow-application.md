---
title: Bir iş akışı uygulamasını kalıcı yapma
ms.date: 03/30/2017
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
ms.openlocfilehash: 0c225a9ed56a742fce0aaff3704bab31dabb0b9a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500010"
---
# <a name="persisting-a-workflow-application"></a>Bir iş akışı uygulamasını kalıcı yapma
Bu örnek nasıl çalıştırılacağını gösterir. bir <xref:System.Activities.WorkflowApplication>boştaki geçtiğinde kaldırın ve sonra yürütülmeye devam etmek için yeniden yükleyin.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 <xref:System.Activities.WorkflowApplication> Basit bir arabirim sağlar ve bazı yaygın barındırma senaryolarını olanak sağlayan bir tek bir iş akışı örneği için bir ana bilgisayardır. Bu tür senaryolardan uzun çalışan iş akışları tarafından Kalıcılık kolaylaştırılan. Kalıcılık konak kontrolü ya da bir Kalıcılık işlemi üzerinde çağırarak gerçekleştirilir <xref:System.Activities.WorkflowApplication>, ya da işlem tarafından bir <xref:System.Activities.WorkflowApplication> olay ve gösteren <xref:System.Activities.WorkflowApplication> kullanmamalısınız.  
  
 Örnek iş akışı bir <xref:System.Activities.Statements.WriteLine> etkinlik için kullanıcıların adı, kullanıcıdan bir `ReadLine` olarak işlemin sürdürülmesini girişini adı almak için etkinlik bir <xref:System.Activities.Bookmark>ve başka bir <xref:System.Activities.Statements.WriteLine> geri kullanıcıya bir karşılama Yankı için. Bir iş akışı giriş bekliyor, bu Kalıcılık için doğal bir nokta sağlar. Bu genellikle olarak adlandırılır bir <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> gelin. <xref:System.Activities.WorkflowApplication> başlatır <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> iş akışı program kalıcı her olay bir yer imi sürdürme üzerinde bekleyen ve başka bir iş gerçekleştirilir. Noktası hemen sonra gelen, bu örneğe ait iş akışında `ReadLine` Etkinlik yürütme başlar.  
  
 A <xref:System.Activities.WorkflowApplication> kalıcılığı ile gerçekleştirilmek üzere ayarlanmış bir <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`. Bu örnekte <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>. <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` Atanmalıdır <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği önce <xref:System.Activities.WorkflowApplication> çalıştırılır.  
  
 Örnek bir işleyici ekler <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> olay. Bu olay işleyicisi ne gösteren <xref:System.Activities.WorkflowApplication> döndürerek yapmanız gereken bir <xref:System.Activities.PersistableIdleAction>. Zaman <xref:System.Activities.PersistableIdleAction.Unload> döndürülecek <xref:System.Activities.WorkflowApplication> kaldırılır.  
  
 Örnek daha sonra kullanıcı girişi kabul eder ve kalıcı iş akışı yeni bir yükler <xref:System.Activities.WorkflowApplication>. Bunu yeni bir oluşturarak yapar <xref:System.Activities.WorkflowApplication>, yeniden oluşturma <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`ve örneği tamamlanan ve kaldırılmış olaylara ilişkilendirme ve ardından arama <xref:System.Activities.WorkflowApplication.Load%2A> , hedef iş akışı örneği tanımlayıcısı. Örnek alınan sonra `ReadLine` etkinliğin yer işareti sürdürüldü. İş akışı içinden yürütme taşıyan `ReadLine` etkinliği ve tamamlanma çalışır. İş akışı tamamlayıp kaldırır, <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` iş akışı silmek için son bir kez çağrılır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
     Bu örnek, varsayılan olarak yüklü SQL Server Express gerektirir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Örnek dizine (\WF\Basic\Persistence\InstancePersistence\CS) gidin ve CreateInstanceStore.cmd çalıştırın.  
  
    > [!CAUTION]
    >  SQL Server 2008 Express varsayılan örneğinde veritabanı oluşturma CreateInstanceStore.cmd betik çalışır. Veritabanını farklı bir örneğinde yüklemek istiyorsanız, bunu yapmak için komut dosyasını değiştirin.  
  
3.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]Persistence.sln çözüm dosyasını açın ve derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
    > [!CAUTION]
    >  Veritabanı bir SQL Server varsayılan olmayan örneğini yüklediyseniz, çözümü ile önce kod bağlantı dizesini güncelleştirin.  
  
4.  Örnek olarak projenin bin dizinine (\WF\Basic\Persistence\InstancePersistence\bin\Debug) giderek yönetici ayrıcalıklarıyla çalıştırın [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], Workflow.exe sağ tıklayıp **yöneticiolarakçalıştır**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Örnek deposu veritabanını kaldırmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
2.  Örnek dizine gidin ve RemoveInstanceStore.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)

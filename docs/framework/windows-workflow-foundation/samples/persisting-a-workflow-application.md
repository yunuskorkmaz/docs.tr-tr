---
title: Bir iş akışı uygulaması kalıcı yapma
ms.date: 03/30/2017
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
ms.openlocfilehash: e5c0cf23dd238c0c5a81519b5e6c415f4ef75f1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="persisting-a-workflow-application"></a>Bir iş akışı uygulaması kalıcı yapma
Bu örnek nasıl çalıştırılacağını gösteren bir <xref:System.Activities.WorkflowApplication>boşta gittiğinde kaldırın ve sonra yürütülmeye devam etmek için yeniden yükleyin.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 <xref:System.Activities.WorkflowApplication> Basit bir arabirim sağlar ve daha yaygın barındırma senaryolarından sağlayan tek bir iş akışı örneği için bir ana bilgisayardır. Böyle bir senaryo uzun çalışan iş akışları tarafından Kalıcılık sayesinde kolaylaşır. Kalıcılık konak denetimini ya da göre sürdürme işlemi çağrılması gerçekleştirilir <xref:System.Activities.WorkflowApplication>, ya da işleme tarafından bir <xref:System.Activities.WorkflowApplication> olay ve belirten <xref:System.Activities.WorkflowApplication> kalıcı olması.  
  
 Örnek iş akışı bir <xref:System.Activities.Statements.WriteLine> etkinlik kendi adı için kullanıcıdan bir `ReadLine` sürdürme aracılığıyla giriş olarak ad alma etkinliği bir <xref:System.Activities.Bookmark>ve başka bir <xref:System.Activities.Statements.WriteLine> geri kullanıcıya Karşılama Yankı için. Bir iş akışı için giriş beklediği sırada bu kalıcılığını doğal noktası sağlar. Bu genellikle olarak adlandırılır bir <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> gelin. <xref:System.Activities.WorkflowApplication> başlatır <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> iş akışı programı kalıcı her olay bir yer işareti sürdürme bekleyen ve başka bir iş gerçekleştirilir. Hemen sonra noktası gelen, bu örneği ait iş akışında `ReadLine` etkinliği başlar yürütülüyor.  
  
 A <xref:System.Activities.WorkflowApplication> Kalıcılık ile gerçekleştirmek için ayarlanmış bir <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`. Bu örnekte <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>. <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` Atanmalıdır <xref:System.Activities.WorkflowApplication.InstanceStore%2A> önce özelliği <xref:System.Activities.WorkflowApplication> çalıştırılır.  
  
 Örnek bir işleyici ekler <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> olay. Bu olay işleyicisi ne gösteren <xref:System.Activities.WorkflowApplication> döndürerek yapmanız gereken bir <xref:System.Activities.PersistableIdleAction>. Zaman <xref:System.Activities.PersistableIdleAction.Unload> döndürülür, <xref:System.Activities.WorkflowApplication> kaldırılır.  
  
 Örnek daha sonra kullanıcı girişi kabul eder ve kalıcı iş akışı yeni bir yükler <xref:System.Activities.WorkflowApplication>. Bunu yeni bir oluşturarak yapar <xref:System.Activities.WorkflowApplication>, yeniden oluşturma <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`ve örnek tamamlanmış ve kaldırılmış olaylara ilişkilendirme ve ardından çağırma <xref:System.Activities.WorkflowApplication.Load%2A> , hedef iş akışı örneği tanımlayıcısı. Örnek edinilen sonra `ReadLine` etkinliğin yer işareti sürdürüldü. İş akışı içinden yürütme üzerinde taşıyan `ReadLine` etkinliği ve tamamlanma çalışır. İş akışı tamamlayıp kaldırır, <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` iş akışı silmek için son bir kez çağrılır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
     Bu örnek varsayılan olarak yüklenen SQL Server Express gerektirir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Örnek dizine (\WF\Basic\Persistence\InstancePersistence\CS) gidin ve CreateInstanceStore.cmd çalıştırın.  
  
    > [!CAUTION]
    >  CreateInstanceStore.cmd komut dosyası, SQL Server 2008 Express varsayılan örneğinde veritabanı oluşturma dener. Veritabanını farklı bir örneğinde yüklemek istiyorsanız, bunu yapmak için komut dosyasını değiştirin.  
  
3.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Persistence.sln çözüm dosyasını açın ve onu oluşturmak için CTRL + SHIFT + B tuşuna basın.  
  
    > [!CAUTION]
    >  Varsayılan olmayan SQL Server örneğinde veritabanı yüklü değilse, bağlantı dizesi çözümü oluşturma önce kodda güncelleştirin.  
  
4.  Örnek, projenin bin dizinine (\WF\Basic\Persistence\InstancePersistence\bin\Debug) giderek yönetici ayrıcalıklarıyla çalıştırın [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], Workflow.exe sağ tıklayıp seçerek **yöneticiolarakçalıştır**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Örnek deposu veritabanı kaldırmak için  
  
1.  Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.  
  
2.  Örnek dizinine gidin ve RemoveInstanceStore.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)

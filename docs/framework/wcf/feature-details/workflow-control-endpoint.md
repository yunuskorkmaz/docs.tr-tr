---
title: İş Akışı Denetim Uç Noktası
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: 40fec2902598daed178e070b02c1067c308507c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929720"
---
# <a name="workflow-control-endpoint"></a>İş Akışı Denetim Uç Noktası
İş akışı denetim uç noktası kullanarak barındırılan iş akışı örnekleri uzaktan denetim için denetim işlemleri çağırmak geliştiricilerinin sağlayan <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bu özellik, programlı olarak askıya alma, sürdürme ve sonlandırma gibi denetim işlemlerini gerçekleştirmek için kullanılabilir.  
  
> [!WARNING]
>  İş akışı denetim uç noktası bir işlem ve denetlenen iş akışı kullanarak içeriyorsa bir <xref:System.Activities.Statements.Persist> etkinliği iş akışı örneği askıda işlem zaman aşımına uğrayana kadar.  
  
## <a name="workflow-instance-management"></a>İş akışı örnek Yönetimi  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] adlı yeni bir sözleşme tanımlayan <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Bu sözleşme tanımlayan bir dizi uzaktan sağlayan işlem tarafından barındırılan iş akışı örnekleri denetim <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> uygulanışı sağlayan standart bir uç nokta <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> sözleşme. <xref:System.ServiceModel.Activities.WorkflowControlClient> denetimi işlemleri için göndermek için kullanılan bir sınıftır <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 İş akışı örnekleri şu durumlardan birinde olabilir:  
  
 Etkin  
 Tamamlanmış duruma ve ne zaman askıya alınmış durumda değil ulaşmadan önce bir iş akışı örneği durumu. Bu durumdayken, iş akışı örneği çalıştırır ve uygulama iletileri işler.  
  
 Askıya alındı  
 Bu durumdayken, çalışan başlamamış olan veya kısmen çalıştıran etkinlikleri olsa bile iş akışı örneği çalıştırmaz.  
  
 Tamamlandı  
 Bir iş akışı örneği son durumu. İş akışı örneği tamamlandı durumuna ulaştıktan sonra çalıştıramazsınız.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Arabirim denetimi işlemleri zaman uyumlu ve zaman uyumsuz sürümlerini kümesini tanımlar. İşlenen sürümleri, hareket algılayan bir bağlama kullanılmasını gerektirir. Aşağıdaki tablo desteklenen denetimi işlemleri listeler.  
  
|Denetimi işlemi|Açıklama|  
|-----------------------|-----------------|  
|Durdurma|Zorla iş akışı örneği yürütülmesini durdurur.|  
|İptal|Etkin veya askıya alınmış durumuna bir iş akışı örneği tamamlandı durumuna geçer.|  
|Çalıştır|Bir iş akışı örneği yürütme olanağı sağlar.|  
|Askıya alma|Etkin duruma bir iş akışı örneği askıya alınma durumuna geçer.|  
|sonlandırma|Etkin veya askıya alınmış durumuna bir iş akışı örneği tamamlandı durumuna geçer.|  
|Uygulamasına yönelik erişimlerini iade|İş akışı örneği askıya alınmış durumundan etkin duruma geçer.|  
|TransactedCancel|(İçinde istemciden aktarılan veya yerel olarak oluşturuldu) bir işlem altında İptal işlemi gerçekleştirir. Sistem iş akışı örneği kalıcı durumunu tutar, bu işlem yürütülürken iş akışı örneği kalıcı gerekir.|  
|TransactedRun|(İçinde istemciden aktarılan veya yerel olarak oluşturuldu) bir işlem altında çalıştırma işlemi gerçekleştirir. Sistem iş akışı örneği kalıcı durumunu tutar, bu işlem yürütülürken iş akışı örneği kalıcı gerekir.|  
|TransactedSuspend|(İçinde istemciden aktarılan veya yerel olarak oluşturuldu) bir işlem altında askıya alma işlemi gerçekleştirir. Sistem iş akışı örneği kalıcı durumunu tutar, bu işlem yürütülürken iş akışı örneği kalıcı gerekir.|  
|TransactedTerminate|(İçinde istemciden aktarılan veya yerel olarak oluşturuldu) bir işlem altında sonlandırma işlemi gerçekleştirir. Sistem iş akışı örneği kalıcı durumunu tutar, bu işlem yürütülürken iş akışı örneği kalıcı gerekir.|  
|TransactedUnsuspend|(İçinde istemciden aktarılan veya yerel olarak oluşturuldu) bir işlem altında erişimi iade et işlemi gerçekleştirir. Sistem iş akışı örneği kalıcı durumunu tutar, bu işlem yürütülürken iş akışı örneği kalıcı gerekir.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Sözleşme yalnızca var olan iş akışı örneğini yönetmek için yeni bir iş akışı örneği oluşturmak için bir yol sağlamaz. Yeni bir iş akışı örneği uzaktan oluşturma hakkında daha fazla bilgi için bkz. [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>workflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> bir standart uç noktası ile sabit bir sözleşme <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Eklenen bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> örnek, bu uç nokta can sonra ana bilgisayar örneği tarafından barındırılan herhangi bir iş akışı örneğine komut işlemlerini göndermek için kullanılması. Standart uç noktaları hakkında daha fazla bilgi için bkz. [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient> Denetim ileti göndermek izin veren bir sınıfı, bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> üzerinde bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Tarafından desteklenen işlemlerin her biri için bir yöntem içerir <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> işlemler dışındaki sözleşme. <xref:System.ServiceModel.Activities.WorkflowControlClient> ortam işlem bir hizmetteki bir işlemi kullanılması gerekip gerekmediğini belirlemek için kullanır.

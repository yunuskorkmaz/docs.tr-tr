---
title: "İş Akışı Denetim Uç Noktası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 676451ac3dce4ff9d328bf4c46809444e0e7cb7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-control-endpoint"></a>İş Akışı Denetim Uç Noktası
İş akışı denetim uç noktası uzaktan kullanarak barındırılan iş akışı örnekleri denetlemek için denetimi işlemleri çağırmak geliştiricilerin sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bu özellik, programlı olarak askıya alma, sürdürme ve sonlandırma gibi denetim işlemleri gerçekleştirmek üzere kullanılabilir.  
  
> [!WARNING]
>  Kullanarak bir işlem ve denetlenen iş akışı içinde iş akışı denetim uç noktası içeriyorsa, bir <xref:System.Activities.Statements.Persist> etkinlik, iş akışı örneği askıda işlem zaman aşımına uğrayana kadar.  
  
## <a name="workflow-instance-management"></a>İş akışı örneği Yönetimi  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]adlı yeni bir sözleşmesini tanımlayan <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Bu sözleşmeyi tanımlayan bir dizi uzaktan izin işlemleri tarafından barındırılan iş akışı örnekleri denetim <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>uygulaması sağlayan standart bir uç nokta <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> sözleşme. <xref:System.ServiceModel.Activities.WorkflowControlClient>denetim işlemleri göndermek için kullanılan bir sınıftır <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 İş akışı örnekleri şu durumlardan birinde olabilir:  
  
 Etkin  
 Tamamlanan durumu ve ne zaman askıya alınmış durumda değil erişmeden önce bir iş akışı örneği durumu. Bu durumundayken, iş akışı örneği çalışır ve uygulama iletileri işler.  
  
 Askıya alındı  
 Bu durumundayken, çalışan başlatılmamış veya kısmen çalıştıran etkinlikleri olsa bile iş akışı örneği çalışmaz.  
  
 Tamamlandı  
 Bir iş akışı örneği son durumu. İş akışı örneği tamamlandı durumuna eriştikten sonra çalıştırılamıyor.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Arabirimi denetimi işlemleri zaman uyumlu ve zaman uyumsuz sürümlerini kümesini tanımlar. İşlenen sürümleri işlem algılayan bir bağlama kullanılmasını gerektirir. Aşağıdaki tabloda, desteklenen denetimi işlemleri listeler.  
  
|Denetim işlemi|Açıklama|  
|-----------------------|-----------------|  
|Durdurma|Zorla iş akışı örneğini yürütmeyi durdurur.|  
|İptal|Bir iş akışı örneğine etkin veya askıya alınmış durumundan tamamlandı durumuna geçiş yapar.|  
|Çalıştır|Bir iş akışı örneği yürütme olanağı sağlar.|  
|Askıya alma|Etkin durumdaki bir iş akışı örneğinden askıya alınmış durumuna geçiş yapar.|  
|Sonlandırma|Bir iş akışı örneğine etkin veya askıya alınmış durumundan tamamlandı durumuna geçiş yapar.|  
|Erişimini iade etme|Bir iş akışı örneği askıya alınmış durumundan etkin duruma geçer.|  
|TransactedCancel|İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında İptal işlemi gerçekleştirir. Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.|  
|TransactedRun|İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında çalıştırma işlemi gerçekleştirir. Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.|  
|TransactedSuspend|İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında askıya alma işlemi gerçekleştirir. Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.|  
|TransactedTerminate|İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında sonlandırma işlemi gerçekleştirir. Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.|  
|TransactedUnsuspend|İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında Unsuspend işlemi gerçekleştirir. Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Sözleşme yalnızca var olan iş akışı örnekleri yönetmek için yeni bir iş akışı örneği oluşturmak için bir yol sağlamaz. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Yeni bir iş akışı örneği uzaktan bkz [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>Standart bir uç nokta sabit bir sözleşme ile <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Eklendiğinde bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> örnek, bu uç nokta can sonra komut işlemleri ana bilgisayar örneği tarafından barındırılan herhangi bir iş akışı örneği göndermek için kullanılır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Standart uç noktaları Bkz [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient>Denetim iletileri göndermenize olanak sağlayan bir sınıf bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> üzerinde bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Tarafından desteklenen işlemler her bir yöntemi içeren <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> hizmetteki işlem dışında sözleşme. <xref:System.ServiceModel.Activities.WorkflowControlClient>uygulaması yapılan işlem kullanılması gerekip gerekmediğini belirlemek için ortam işlem kullanır.

---
title: 'Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 55cc10357e8ae6b5458ca3440e1728cb578208b3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma
İş akışı örneği bir ileti kullanılarak teslim edilebilir beklenirken örneğin bazı dış stimulus tarafından sürdürüldü gerekir bir yer işareti karşılaştığınızda iş akışları boşta Git bir <xref:System.ServiceModel.Activities.Receive> etkinlik. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bir hizmet örneği boşta gittiğinde arasında ve örnek kalıcı ya da kaldırıldığında süreyi belirtmek üzere izin veren bir davranıştır. Bu zaman aralıkları ayarlamanıza olanak tanır iki özellik içerir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> bir iş akışı hizmeti örneği boşta gittiğinde ve ne zaman iş akışı hizmeti örneği kalıcı arasındaki zaman aralığını belirtir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> ne zaman bir iş akışı hizmeti örneği arasında zaman aralığı boşta gider ve iş akışı hizmeti örneği kaldırıldığında, burada unload örnek deposuna örnek kalıcı bellekten kaldırılıyor anlamına gelir ve belirtir. Bu konuda nasıl yapılandırılacağını açıklar <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bir yapılandırma dosyası.  
  
### <a name="to-configure-workflowidlebehavior"></a>WorkflowIdleBehavior yapılandırmak için  
  
1.  Ekleme bir <`workflowIdle`> öğesi <`behavior`> öğesi içinde <`serviceBehaviors`> Aşağıdaki örnekte gösterildiği gibi öğesi.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     `timeToUnload` Özniteliği, bir iş akışı hizmeti örneği boşta gittiğinde ve iş akışı hizmeti kaldırılmış olduğunda arasındaki süreyi belirtir. `timeToPersist` Özniteliği, bir iş akışı hizmeti örneği boşta gittiğinde ve ne zaman iş akışı hizmeti örneği kalıcı arasındaki süreyi belirtir. İçin varsayılan değer `timeToUnload` 1 dakikadır. İçin varsayılan değer `timeToPersist` olan <xref:System.TimeSpan.MaxValue>. Boşta örnekleri bellekte tut ancak bunları için sağlamlık kalıcı hale getirmek istiyorsanız, değerleri ayarlamak için `timeToPersist`  <  `timeToUnload`. Boşta örnekleri bellekten kaldırılan engellemek istiyorsanız, Ayarla `timeToUnload` için <xref:System.TimeSpan.MaxValue>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, bkz: [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    >  Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Kodda boşta davranışı değiştirmek için  
  
-   Aşağıdaki örnek kalıcı yapma ve program aracılığıyla kaldırılması önce beklenecek süreyi değiştirir.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmeti Konak Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)

---
title: 'Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 67be47f97e57792e2f1e14505d3cd121729db33b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185076"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma
İş akışları, örneğin iş akışı örneği bir <xref:System.ServiceModel.Activities.Receive> etkinlik kullanılarak iletinin teslim edilmesini beklerken, bazı dış uyaranlar tarafından başlatılması gereken bir yer işaretiyle karşılaştıklarında boşta kalır. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>bir hizmet örneğinin boşta kalma süresi ile örneğin kalıcı veya boşaltılan saat arasındaki süreyi belirtmenize olanak tanıyan bir davranıştır. Bu zaman aralıklarını ayarlamanızı sağlayan iki özellik içerir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>bir iş akışı hizmeti örneğinin boşta kaldığı zaman ile iş akışı hizmeti örneğinin boşaltılması arasındaki zaman aralığını belirtir, burada boşaltma örneği örnek deposuna devam etmek ve bellekten kaldırmak anlamına gelir. Bu konu, yapılandırma dosyasında nasıl yapılandırılabildiğini <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> açıklar.  
  
### <a name="to-configure-workflowidlebehavior"></a>İş akışını yapılandırmak içinIdleBehavior  
  
1. Aşağıdaki örnekte gösterildiği gibi `behavior` <`serviceBehaviors`> öğesi içinde <> öğesine <`workflowIdle` bir> öğesi ekleyin.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Öznitelik, `timeToUnload` iş akışı hizmeti örneğinin boşta yatması ile iş akışı hizmetinin boşaltılması arasındaki süreyi belirtir. Öznitelik, `timeToPersist` iş akışı hizmeti örneğinin boşta yatması ile iş akışı hizmeti örneğinin kalıcı olması arasındaki süreyi belirtir. Varsayılan değer `timeToUnload` 1 dakikadır. Varsayılan <xref:System.TimeSpan.MaxValue>değer. `timeToPersist` Boşta kalan örnekleri bellekte tutmak, ancak sağlamlık için devam `timeToPersist`  <  `timeToUnload`ettirmek istiyorsanız, değerleri şu şekilde ayarlayın. Boşta kalan örneklerin yüklenmesini önlemek istiyorsanız, <xref:System.TimeSpan.MaxValue>'' olarak ayarlayın `timeToUnload` Hakkında <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>daha fazla bilgi için Bkz. [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > Önceki yapılandırma örneği basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için Bkz. [Basitleştirilmiş Yapılandırma.](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-change-idle-behavior-in-code"></a>Koddaki boşta davranışı değiştirmek için  
  
- Aşağıdaki örnek, kalıcı olarak bekletmeden ve programlı olarak boşaltmadan önce bekleme süresini değiştirir.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)

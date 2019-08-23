---
title: 'Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 57a9e0487ff605e99adc22471b02f5a288fc4a2b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912150"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma
İş akışları, bazı dış Camulus tarafından devam edilmesi gereken bir yer işaretiyle karşılaştıklarında boşta kalır, örneğin, iş akışı örneği bir <xref:System.ServiceModel.Activities.Receive> etkinliği kullanarak bir ileti teslim edilmesini bekliyorsa. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, bir hizmet örneğinin boşta kaldığı ve örneğin kalıcı veya kaldırılmış olduğu zaman arasındaki süreyi belirtmenize olanak tanıyan bir davranıştır. Bu zaman yayılmalarını ayarlamanıza olanak tanıyan iki özellik içerir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmet örneğinin kalıcı olduğu zaman arasındaki süreyi belirtir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmeti örneğinin ne zaman kaldırılabileceği arasındaki süreyi belirtir. burada, kaldırma işlemi örneği örnek deposuna kalıcı hale getiren ve bellekten kaldıran anlamına gelir. Bu konu, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bir yapılandırma dosyasında ' nin nasıl yapılandırılacağını açıklar.  
  
### <a name="to-configure-workflowidlebehavior"></a>WorkflowIdleBehavior yapılandırmak için  
  
1. Aşağıdaki örnekte gösterildiği`workflowIdle`gibi, <`serviceBehaviors`> öğesi`behavior`içindeki < > öğesine bir < > öğesi ekleyin.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     `timeToUnload` Öznitelik, bir iş akışı hizmeti örneğinin boşta kalma süresi ve iş akışı hizmeti kaldırıldığında arasındaki süreyi belirtir. `timeToPersist` Öznitelik, bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmet örneğinin kalıcı olduğu zaman arasındaki süreyi belirtir. İçin `timeToUnload` varsayılan değer 1 dakikadır. `timeToPersist` İçin<xref:System.TimeSpan.MaxValue>varsayılan değer. Boştaki örnekleri bellekte tutmak, ancak bunları sağlamlık için kalıcı hale getirmek istiyorsanız değerlerini `timeToPersist`  <  `timeToUnload`ayarlayın. Boş örneklerin bellekten kaldırılmasını engellemek istiyorsanız, olarak `timeToUnload` <xref:System.TimeSpan.MaxValue>ayarlayın. Hakkında <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>daha fazla bilgi için bkz. [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Koddaki boşta davranışını değiştirmek için  
  
- Aşağıdaki örnek, programlı bir şekilde kalıcı ve kaldırmadan önce beklenecek süreyi değiştirir.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Konak Genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md)
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)

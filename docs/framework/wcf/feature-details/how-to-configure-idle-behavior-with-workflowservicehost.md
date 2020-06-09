---
title: 'Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 8b9fa36408d5f2bc5445ebeccba61f71417935e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599132"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile Boşta Davranışı Yapılandırma
İş akışları, bazı dış Camulus tarafından devam edilmesi gereken bir yer işaretiyle karşılaştıklarında boşta kalır, örneğin, iş akışı örneği bir etkinliği kullanarak bir ileti teslim edilmesini bekliyorsa <xref:System.ServiceModel.Activities.Receive> . <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, bir hizmet örneğinin boşta kaldığı ve örneğin kalıcı veya kaldırılmış olduğu zaman arasındaki süreyi belirtmenize olanak tanıyan bir davranıştır. Bu zaman yayılmalarını ayarlamanıza olanak tanıyan iki özellik içerir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmet örneğinin kalıcı olduğu zaman arasındaki süreyi belirtir. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmeti örneğinin ne zaman kaldırılabileceği arasındaki süreyi belirtir. burada, kaldırma işlemi örneği örnek deposuna kalıcı hale getiren ve bellekten kaldıran anlamına gelir. Bu konu, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bir yapılandırma dosyasında ' nin nasıl yapılandırılacağını açıklar.  
  
### <a name="to-configure-workflowidlebehavior"></a>WorkflowIdleBehavior yapılandırmak için  
  
1. `workflowIdle` `behavior` `serviceBehaviors` Aşağıdaki örnekte gösterildiği gibi, <> öğesi içindeki <> öğesine bir <> öğesi ekleyin.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     `timeToUnload`Öznitelik, bir iş akışı hizmeti örneğinin boşta kalma süresi ve iş akışı hizmeti kaldırıldığında arasındaki süreyi belirtir. `timeToPersist`Öznitelik, bir iş akışı hizmet örneğinin boşta kaldığı ve iş akışı hizmet örneğinin kalıcı olduğu zaman arasındaki süreyi belirtir. İçin varsayılan değer `timeToUnload` 1 dakikadır. İçin varsayılan değer `timeToPersist` <xref:System.TimeSpan.MaxValue> . Boştaki örnekleri bellekte tutmak, ancak bunları sağlamlık için kalıcı hale getirmek istiyorsanız değerlerini ayarlayın `timeToPersist`  <  `timeToUnload` . Boş örneklerin bellekten kaldırılmasını engellemek istiyorsanız, `timeToUnload` olarak ayarlayın <xref:System.TimeSpan.MaxValue> . Hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> bkz. [Iş akışı hizmeti konak genişletilebilirliği](workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Koddaki boşta davranışını değiştirmek için  
  
- Aşağıdaki örnek, programlı bir şekilde kalıcı ve kaldırmadan önce beklenecek süreyi değiştirir.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği](workflow-service-host-extensibility.md)
- [Basitleştirilmiş Yapılandırma](../simplified-configuration.md)
- [İş Akışı Hizmetleri](workflow-services.md)

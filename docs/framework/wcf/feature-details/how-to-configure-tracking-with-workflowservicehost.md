---
title: 'Nasıl yapılır: WorkflowServiceHost ile izlemeyi yapılandırma'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 8ed8775a8eb13a8e69566c1d413dcd2eba6d8b6c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577585"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile izlemeyi yapılandırma
Yapılandırma izleme için bu konu açıklar bir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] barındırılan iş akışı <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bir hizmet davranışını belirterek, bir Web.config dosyası aracılığıyla yapılandırılır.  
  
### <a name="configure-tracking-in-configuration"></a>Yapılandırmada izlemeyi yapılandırma  
  
1.  Ekleme <xref:System.Activities.Tracking.EtwTrackingParticipant> kullanarak <`behavior`> öğesinde aşağıdaki örnekte gösterildiği gibi bir yapılandırma dosyası.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    >  Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Önceki yapılandırma örneği ekler bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ve belirten bir izleme profili adı. İzleme profilleri oluşturulan bir <`trackingProfile`> öğesinde bir <`tracking`> öğesi. İzleme profili çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir. Aşağıdaki örnek, bir izleme profili oluşturma işlemi gösterilmektedir.  
  
    ```xml  
    <system.serviceModel>  
        <tracking>   
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>   
       </tracking>  
    </system.serviceModel>  
    ```  
  
     İzleme profilleri hakkında daha fazla bilgi için bkz. [izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Genel olarak izleme hakkında daha fazla bilgi için bkz. [takip ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Kodda izlemeyi yapılandırma  
  
1.  Ekleme <xref:System.Activities.Tracking.EtwTrackingParticipant> kullanarak <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> kodda, aşağıdaki örnekte gösterildiği gibi davranış.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Yukarıdaki kod örneğinde ekler bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ve belirten bir izleme profili adı. İzleme profilleri oluşturulan bir <`trackingProfile`> öğesinde bir <`tracking`> önceki bölümde gösterildiği gibi bir öğe.  
  
     İzleme profilleri hakkında daha fazla bilgi için bkz. [izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Genel olarak izleme hakkında daha fazla bilgi için bkz. [takip ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Program aracılığıyla izleme yapılandırma örneği için bkz. [yapılandırma izleme için bir iş akışı](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmetleri için Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İzleme Profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

---
title: 'Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 5781878270272f5ef894c68dc23b9433029e1d41
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968501"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma
Bu konu başlığında [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışı için izlemenin nasıl yapılandırılacağı açıklanmaktadır. Bir hizmet davranışı belirtilerek bir Web. config dosyası aracılığıyla yapılandırılır.  
  
### <a name="configure-tracking-in-configuration"></a>Yapılandırmada Izlemeyi Yapılandır  
  
1. Aşağıdaki örnekte gösterildiği gibi,`behavior`bir yapılandırma dosyasında < > öğesini kullanarakekleyin.<xref:System.Activities.Tracking.EtwTrackingParticipant>  
  
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
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Önceki yapılandırma örneği bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ekler ve bir izleme profili adı belirtir. İzleme profilleri, bir <`trackingProfile``tracking`> öğesi içindeki bir < > öğesinde oluşturulur. İzleme profili, çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir. Aşağıdaki örnek, bir izleme profilinin nasıl oluşturulacağını gösterir.  
  
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
  
     İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Genel olarak izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Kodda Izlemeyi Yapılandır  
  
1. Aşağıdaki örnekte gösterildiği gibi <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> , koddaki davranışı kullanarakekleyin.<xref:System.Activities.Tracking.EtwTrackingParticipant>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Önceki kod örneği bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ekler ve bir izleme profili adı belirtir. İzleme profilleri, önceki bölümde gösterildiği gibi`trackingProfile`bir <`tracking`> öğesi içindeki bir < > öğesinde oluşturulur.  
  
     İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Genel olarak izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Program aracılığıyla izlemeyi yapılandırmaya yönelik bir örnek için bkz. [bir Iş akışı Için Izlemeyi yapılandırma](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmetleri için Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İzleme Profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

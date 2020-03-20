---
title: 'Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 962dfda9fc5780cc3ac7211464bb3a9be8b7fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185064"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma
Bu konu, 'de [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırılan bir iş akışı için izlemeyi nasıl yapılandırılabildiğini açıklar. Bir hizmet davranışı belirterek bir Web.config dosyası üzerinden yapılandırılır.  
  
### <a name="configure-tracking-in-configuration"></a>Yapılandırmada İzlemeyi Yapılandırma  
  
1. Aşağıdaki <xref:System.Activities.Tracking.EtwTrackingParticipant> örnekte `behavior` gösterildiği gibi, yapılandırma dosyasında <> öğesini kullanarak ekleyin.  
  
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
    > Önceki yapılandırma örneği basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için Bkz. [Basitleştirilmiş Yapılandırma.](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Önceki yapılandırma örneği bir <xref:System.Activities.Tracking.EtwTrackingParticipant> izleme profili adı ekler ve belirtir. İzleme profilleri, <`trackingProfile` `tracking`> öğesi içinde <bir> öğesi nde oluşturulur. İzleme profili, bir izleme katılımcısının çalışma zamanında iş akışı örneği durumu değiştiğinde yayılan iş akışı olaylarına abone olmasını sağlayan izleme sorguları içerir. Aşağıdaki örnekte, izleme profilinin nasıl oluşturuluşu gösterilmektedir.  
  
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
  
     İzleme profilleri hakkında daha fazla bilgi için Izleme [Profilleri'ne](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)bakın.  
  
     Genel olarak izleme hakkında daha fazla bilgi için [İş Akışı İzleme ve İzleme'ye](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)bakın.  
  
### <a name="configure-tracking-in-code"></a>Kodda İzlemeyi Yapılandırma  
  
1. Aşağıdaki <xref:System.Activities.Tracking.EtwTrackingParticipant> örnekte <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> gösterildiği gibi, koddaki davranışı kullanma ekleme.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Önceki kod örneği a <xref:System.Activities.Tracking.EtwTrackingParticipant> ekler ve bir izleme profili adı belirtir. İzleme profilleri, önceki bölümde `trackingProfile` gösterildiği gibi `tracking` <> öğesi içindeki <bir> öğesinde oluşturulur.  
  
     İzleme profilleri hakkında daha fazla bilgi için Izleme [Profilleri'ne](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)bakın.  
  
     Genel olarak izleme hakkında daha fazla bilgi için [İş Akışı İzleme ve İzleme'ye](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)bakın. İzlemeyi yapılandırma örneği için [bkz.](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmetleri için Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [İzleme Profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

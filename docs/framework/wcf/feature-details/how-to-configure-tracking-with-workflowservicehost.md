---
title: 'Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 54594a8f464e77062c658606db6bc941e319f71d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599106"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma
Bu konu başlığında barındırılan bir iş akışı için izlemenin nasıl yapılandırılacağı açıklanmaktadır [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Bir hizmet davranışı belirtilerek bir Web. config dosyası aracılığıyla yapılandırılır.  
  
### <a name="configure-tracking-in-configuration"></a>Yapılandırmada Izlemeyi Yapılandır  
  
1. <xref:System.Activities.Tracking.EtwTrackingParticipant> `behavior` Aşağıdaki örnekte gösterildiği gibi, bir yapılandırma dosyasında <> öğesini kullanarak ekleyin.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. Daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../simplified-configuration.md).  
  
     Önceki yapılandırma örneği bir ekler <xref:System.Activities.Tracking.EtwTrackingParticipant> ve bir izleme profili adı belirtir. İzleme profilleri, bir `trackingProfile` <> öğesi içindeki bir <> öğesinde oluşturulur `tracking` . İzleme profili, çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir. Aşağıdaki örnek, bir izleme profilinin nasıl oluşturulacağını gösterir.  
  
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
  
     İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../windows-workflow-foundation/tracking-profiles.md).  
  
     Genel olarak izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Kodda Izlemeyi Yapılandır  
  
1. <xref:System.Activities.Tracking.EtwTrackingParticipant> <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> Aşağıdaki örnekte gösterildiği gibi, koddaki davranışı kullanarak ekleyin.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Önceki kod örneği bir ekler <xref:System.Activities.Tracking.EtwTrackingParticipant> ve bir izleme profili adı belirtir. İzleme profilleri, `trackingProfile` `tracking` önceki bölümde gösterildiği gibi bir <> öğesi içindeki bir <> öğesinde oluşturulur.  
  
     İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../windows-workflow-foundation/tracking-profiles.md).  
  
     Genel olarak izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../windows-workflow-foundation/workflow-tracking-and-tracing.md). Program aracılığıyla izlemeyi yapılandırmaya yönelik bir örnek için bkz. [bir Iş akışı Için Izlemeyi yapılandırma](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmetleri için Basitleştirilmiş Yapılandırma](../samples/simplified-configuration-for-wcf-services.md)
- [İş Akışı Hizmetleri](workflow-services.md)
- [İzleme Profilleri](../../windows-workflow-foundation/tracking-profiles.md)

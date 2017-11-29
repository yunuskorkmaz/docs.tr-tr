---
title: "Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a237be3f6e4d59cbaa2d3c0144eaeb4369748ecd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Nasıl yapılır: WorkflowServiceHost ile İzlemeyi Yapılandırma
Bu konuda, izleme için yapılandırmak açıklanmaktadır bir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] iş akışı içinde barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bir hizmet davranışı belirterek, bir Web.config dosyası aracılığıyla yapılandırılır.  
  
### <a name="configure-tracking-in-configuration"></a>İzleme yapılandırmasını  
  
1.  Ekleme <xref:System.Activities.Tracking.EtwTrackingParticipant> kullanarak <`behavior`> öğesi aşağıdaki örnekte gösterildiği gibi bir yapılandırma dosyası.  
  
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
    >  Önceki yapılandırma örneği Basitleştirilmiş yapılandırma kullanıyor. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Önceki yapılandırma örneği ekler bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ve bir izleme belirtir profil adı. İzleme profilleri oluşturulan bir <`trackingProfile`> öğesinde bir <`tracking`> öğesi. İzleme profili çalışma zamanında bir iş akışı örneğinin durumu değiştiğinde, gösterilen iş akışı olayları abone olmak için izleme katılımcı izin izleme sorgularını içerir. Aşağıdaki örnekte bir izleme profilinin nasıl oluşturulacağını gösterir.  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]profilleri izleme, bkz: [izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Genel olarak, izleme Bkz [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>İzleme Yapılandırma  
  
1.  Ekleme <xref:System.Activities.Tracking.EtwTrackingParticipant> kullanarak <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> kodda, aşağıdaki örnekte gösterildiği gibi davranış.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Yukarıdaki kod örneğinde ekler bir <xref:System.Activities.Tracking.EtwTrackingParticipant> ve bir izleme belirtir profil adı. İzleme profilleri oluşturulan bir <`trackingProfile`> öğesinde bir <`tracking`> önceki bölümde gösterildiği gibi öğesi.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]profilleri izleme, bkz: [izleme profilleri](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Genel olarak, izleme Bkz [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Program aracılığıyla izleme yapılandırma örneği için bkz: [yapılandırma izleme iş akışı için](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [İş akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Profillerini izleme](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

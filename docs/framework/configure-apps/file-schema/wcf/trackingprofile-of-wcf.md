---
title: WFC &lt;trackingProfile&gt;
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: a11086ef07a2a605f3889bc4077d25e0b7748e5e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087667"
---
# <a name="lttrackingprofilegt-of-wcf"></a>WFC &lt;trackingProfile&gt;
İş akışı izleme katılımcı kayıtlarında izleme aboneliği oluşturmak için bir yapılandırma bölümünü temsil eder. Bir izleme profili çalışma zamanında bir iş akışı örneği durumu değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir. Tanımlanan sorguları izleme profilinde bölümü abonelik tarafından döndürülen olayları tür tanımlamak.  
  
 İş akışı izleme ve kendi yapılandırmasını daha fazla bilgi için bkz: [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
 \<system.serviceModel>  
\<İzleme >  
\<trackingProfile>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String"/>
              </arguments>
              <states>
                <state name="String"/>
              </states>
              <variables>
                <variable name="String"/>
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String" 
                                   faultHandlerActivityName="String"/>
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|İzleme profilinin adını belirten dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İzleme >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|Bir iş akışı hizmeti için izleme ayarları tanımlamak için bir yapılandırma bölümünü temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 İzleme profilleri bir iş akışı örneğinin durumunu çalışma zamanında değiştiğinde yayılan iş akışı olayları abone olmak için izleme katılımcı izin izleme sorguları içerir. Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur. Buna karşılık, elde edilen ayarlanmış olayları ayrıntılı yürütme akışı daha sonra yeniden oluşturmak için zengin bir çok özel profil oluşturabilir.  
  
 İzleme profilleri belirli izleme kayıtları için iş akışı çalışma zamanı sorgulamaya izin kayıtları izleme için bildirim abonelikleri olarak yapılandırılmıştır. Birkaç farklı sınıfları için abone izin sorgu türleri vardır <xref:System.Activities.Tracking.TrackingRecord> nesneleri. Sorguları tam listesi için bkz. [ \<katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) ve [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).
  
Aşağıdaki örnek, abone olmak izleme katılımcı izin veren bir yapılandırma dosyasında bir izleme profili gösterir. `Started` ve `Completed` iş akışı olayları.  
  
```xml
<system.serviceModel>
  <tracking>
    <profiles>
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
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
- <xref:System.Activities.Tracking.TrackingProfile>  
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

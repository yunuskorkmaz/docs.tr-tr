---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 968cfa8e5402458afd6f13545ed999a472adf2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151916"
---
# <a name="tracking"></a>\<izleme>
İş akışı hizmeti için izleme ayarlarını tanımlamak için bir yapılandırma bölümünü temsil eder.  
  
 İş akışı izleme ve yapılandırmasında daha fazla bilgi için [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md) [bkz.](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<izleme>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
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
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<katılımcılar>](participants.md)|İzleme kayıtlarına abone olan katılımcıları tanımlayan yapılandırma öğeleri koleksiyonu. İzleme katılımcıları, izleme kayıtlarından yükü işlemek için gereken mantığı içerir (örneğin, bir dosyaya yazmayı seçebilirler).|  
|[\<izlemeProfil>](trackingprofile.md)|İş akışı örneğinden yayılan izleme kayıtlarını filtrelemek için izleme profili.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Sistem.ServiceModel|Tüm iş akışı yapılandırma öğelerinin kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 İzleme, iş akışının yürütülmesini inceleme olanağı sağlar. İş akışı izleme altyapısı, yürütme sırasında ki önemli olayları yansıtan kayıtları yayacak bir iş akışı sağlar. Örneğin, bir iş akışı örneği başlatıldığında veya izleme kayıtlarını tamamladığında yayımlanır. İzleme, iş akışı değişkenleriyle ilişkili iş ile ilgili verileri de ayıklayabilir. Örneğin, iş akışı bir sipariş işleme sistemini temsil ediyorsa, sipariş kimliği izleme kaydıyla birlikte ayıklanabilir. Genel olarak, WF izlemeyi etkinleştirmek, iş akışı yürütmesi üzerinden tanılamayı veya iş analitiğini kolaylaştırır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)

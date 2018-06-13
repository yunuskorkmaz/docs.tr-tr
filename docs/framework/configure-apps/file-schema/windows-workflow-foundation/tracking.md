---
title: '&lt;İzleme&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 38c765c52a7578ed9972cd6fdd8e01440a4d9594
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756689"
---
# <a name="lttrackinggt"></a>&lt;İzleme&gt;
Bir iş akışı hizmeti izleme ayarlarını tanımlamak için yapılandırma bölümünü temsil eder.  
  
 İş akışı izleme ve yapılandırmasını daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [yapılandırma izleme iş akışı için](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
\<system.serviceModel>  
\<İzleme >  
  
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
|[\<Katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Kayıtları İzleme için abone katılımcılara tanımlama yapılandırma öğeleri koleksiyonu. İzleme katılımcıları izleme kayıtları yükü işlemek için mantığı içerir (örneğin, bir dosyaya yazmak tercih ettikleri).|  
|[\<trackingProfile >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|Bir iş akışı örneğinden yayılan filtre izleme kayıtları için bir izleme profili.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Sistem.ServiceModel|Tüm iş akışı yapılandırma öğelerinin kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 İzleme, bir iş akışının yürütülmesini inceleyin olanağı sağlar. İş akışı izleme altyapısı, bir iş akışı yürütme sırasında anahtar olayları yansıtma kayıtları yayma Instruments. Örneğin, bir iş akışı örneği başlatıldığında veya tamamlandıktan izleme kayıtları gösterilen. İzleme, iş akışı değişkenleri ile ilişkili iş ilgili veriler ayrıca ayıklayabilirsiniz. Örneğin, iş akışı işleme sistemi sipariş temsil ediyorsa düzeni kimliği ile birlikte izleme kaydı ayıklanabilir. Genel olarak, izleme WF etkinleştirme Tanılama veya İş analizi bir iş akışının yürütülmesini kolaylaştırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>       
 [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)

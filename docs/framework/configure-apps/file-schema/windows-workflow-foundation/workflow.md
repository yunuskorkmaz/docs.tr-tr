---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151864"
---
# <a name="workflow"></a>\<iş akışı>
Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> özelliği.  
  
 İş akışı izleme ve yapılandırmasında daha fazla bilgi için [İş Akışı İzleme ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) ve İzleme [Profilleri'ne](../../../windows-workflow-foundation/tracking-profiles.md)bakın.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<iş akışı>**  
  
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
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|activityDefinitionId|İzlenen iş akışının etkinlik tanım kimliğini belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<etkinlikPlanlanmışSorgular>](activityscheduledqueries.md)|Bir üst etkinlik tarafından yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgukoleksiyonunu temsil eder. Sorgu, bir izleme katılımcısının etkinlik zamanlanan kayıtlara abone olması için gereklidir.|  
|[\<etkinlikStateQueries>](activitystatequeries.md)|İş akışı örneğini oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan sorgu koleksiyonunu temsil eder. Örneğin, "E-Posta Gönder" etkinliği bir iş akışı örneği içinde her tamamlandığında izlemek isteyebilirsiniz. Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesneleri abone olması için gereklidir. Abone olmak için kullanılabilir durumları ActivityStates belirtilir.|  
|[\<yer imiDevamıSorgular>](bookmarkresumptionqueries.md)|İş akışı örneği içinde yer işaretinin yeniden başlatılmasını izlemek için kullanılan sorgukoleksiyonunu temsil eder. Sorgu, bir izleme katılımcısının devam kayıtlarını yer imine abone olması için gereklidir.|  
|[\<cancelRequestedQueries>](cancelrequestedqueries.md)|Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan sorgukoleksiyonunu temsil eder. Sorgu, bir izleme katılımcısının istek kayıt nesnelerini iptal etmek için abone olması için gereklidir.|  
|[\<customTrackingQueries>](customtrackingqueries.md)|Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder. Sorgu, bir izleme katılımcısının özel izleme kayıtlarına abone olması için gereklidir.|  
|[\<hata YayılımSorgular>](faultpropagationqueries.md)|Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan sorgukoleksiyonunu temsil eder.  Bu olay, bir Hata Handler bir hatayı her işlerde oluşur. Bir etkinlik içinde oluşan hataların işlenmesini izlemek için bu tür sorguyu kullanmalısınız. Sorgu, bir izleme katılımcısının hata yayma kayıtlarına abone olması için gereklidir.|  
|[\<iş akışıInstanceQueries>](workflowinstancequeries.md)|Başlatılan veya tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen yapılandırma öğeleri koleksiyonunu temsil eder.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<izlemeProfil>](trackingprofile.md)|İzleme katılımcısında iş akışı izleme kayıtlarına abonelik oluşturmak için bir yapılandırma bölümünü temsil eder. İzleme profili, bir izleme katılımcısının çalışma zamanında iş akışı örneği durumu değiştiğinde yayılan iş akışı olaylarına abone olmasını sağlayan izleme sorguları içerir. İzleme profili bölümünde tanımlanan sorgular, abonelik tarafından döndürülen olay türlerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 İzleme profilleri, belirli bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayılan iş akışı olaylarına abone olmak için izleme katılımcısının izin veren izleme sorguları içerir. İzlenen iş akışı örneği bu yapılandırma öğesi tarafından tanımlanır.  
  
 Çok kaba bir profili yazabilirsiniz izleme gereksinimlerinize bağlı olarak, bir iş akışı üzerinde üst düzey durum değişikliklerini küçük bir kümesi için abone olur. Tersine, ortaya çıkan olaylar daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok özel bir profil oluşturabilirsiniz.  
  
 İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanıza olanak tanıyan kayıtları izlemek için bildirimsel abonelikler olarak yapılandırılır. Farklı izleme kayıtları sınıflarına abone olsanız sağlayan bir avuç sorgu türü vardır. Sorguların tam listesi için, bu konunun alt öğe öğesi listesine ve [İzleme Profilleri'ne](../../../windows-workflow-foundation/tracking-profiles.md)bakın.  
  
 Aşağıdaki örnek, bir yapılandırma dosyasındaki bir izleme katılımcısının iş `Started` `Completed` akışı olaylarına abone olmasını sağlayan bir izleme profilini gösterir.  
  
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
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [İş Akışı Takip ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../windows-workflow-foundation/tracking-profiles.md)

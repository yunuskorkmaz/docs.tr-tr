---
title: <activityStateQuery>WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: ce7505896b9c5bb605bb0f67d735cb324f4fd493
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926907"
---
# <a name="activitystatequery-of-wcf"></a>\<WCF > activityStateQuery

Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorguyu temsil eder. Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz. Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir. Abone olmak için kullanılabilir durumları ActivityStates belirtilir.  
  
Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).

\<System. ServiceModel > \<izleme >  
\<> \<TrackingProfile > profilleri  
\<iş akışı >  
\<activityStateQueries >  
\<activityStateQuery >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|activityName|Örnekleri filtreleyecek <xref:System.Activities.Tracking.ActivityStateRecord> etkinliğin adını belirten bir dize.|  
  
### <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağımsız değişkenler >](../windows-workflow-foundation/arguments.md)|Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.|  
|[\<durumlar >](../windows-workflow-foundation/states.md)|Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.|  
|[\<durumlar >](../windows-workflow-foundation/states.md)|Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<faultPropagationQuery >](../windows-workflow-foundation/faultpropagationquery.md)|Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan yapılandırma öğelerinin listesini temsil eder. Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.|  
  
## <a name="remarks"></a>Açıklamalar

Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir. Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar. Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](../windows-workflow-foundation/states.md) ve [ \<durumlar >](../windows-workflow-foundation/states.md) öğeleri için [ \<bağımsız değişkenleri](../windows-workflow-foundation/arguments.md)kullanabilirsiniz. Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir. Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](../windows-workflow-foundation/activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [İş Akışı Takip ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../windows-workflow-foundation/tracking-profiles.md)

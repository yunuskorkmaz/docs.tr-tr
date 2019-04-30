---
title: <activityScheduledQueries> WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 1c9c292080016d7a2d0014ed07be371c0e247621
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701131"
---
# <a name="activityscheduledqueries-of-wcf"></a>\<activityScheduledQueries > WCF
Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder. Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.  
  
Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<İzleme >  
\<profilleri >  
\<trackingProfile>  
\<İş akışı >  
\<activityScheduledQueries >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

Yok.  
  
### <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<activityScheduledQuery >](activityscheduledquery-of-wcf.md)|Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İş akışı >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

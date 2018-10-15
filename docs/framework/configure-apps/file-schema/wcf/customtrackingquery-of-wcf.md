---
title: WCF &lt;customTrackingQuery&gt;
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: e13064afbd9f5dbc8d7216eb384001e1e005785c
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316239"
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a>WCF &lt;customTrackingQuery&gt;

Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan bir sorgu temsil eder. Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.

Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<İzleme >  
\<profilleri >  
\<trackingProfile>  
\<İş akışı >  
\<customTrackingQueries >  
\<customTrackingQuery >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
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
|`activityName`|İzleme kayıt oluşturulan etkinliğin adını belirten dize.|  
|`name`|Yayılan özel izleme kayıt adını belirten dize.|  
  
### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<customTrackingQueries >](customtrackingqueries-of-wcf.md)|Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.|
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

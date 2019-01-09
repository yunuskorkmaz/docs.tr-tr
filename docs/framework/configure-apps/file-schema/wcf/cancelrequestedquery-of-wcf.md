---
title: WCF &lt;cancelRequestedQuery&gt;
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 6b41721dcc0c489377c59bfccdd0b1a617f551b0
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149078"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a>WCF &lt;cancelRequestedQuery&gt;

Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir sorgu temsil eder. Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.  
  
Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).
  
\<system.serviceModel>  
\<İzleme >  
\<profilleri >  
\<trackingProfile>  
\<İş akışı >  
\<cancelRequestedQueries >  
\<cancelRequestedQuery >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
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
|`activityName`|İptal isteyen etkinliğin adını belirten dize.|  
|`childActivityName`|Kendisi için İptal istendi alt etkinliğin adını belirten dize.|  
  
### <a name="child-elements"></a>Alt öğeleri

Yok.
  
### <a name="parent-elements"></a>Üst öğeler
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cancelRequestedQueries >](cancelrequestedqueries-of-wcf.md)|Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan sorguları koleksiyonunu temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

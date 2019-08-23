---
title: <cancelRequestedQuery>WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 7952520edbf799e5fab6864e50962c6ec2860928
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919642"
---
# <a name="cancelrequestedquery-of-wcf"></a>\<WCF için cancelRequestedQuery >

Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder. Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.  
  
Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).
  
\<system.serviceModel>  
\<İzleme >  
\<Profiller >  
\<trackingProfile>  
\<iş akışı >  
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
|`activityName`|İptali isteyen etkinliğin adını belirten bir dize.|  
|`childActivityName`|İptalin istendiği alt etkinliğin adını belirten bir dize.|  
  
### <a name="child-elements"></a>Alt öğeleri

Yok.
  
### <a name="parent-elements"></a>Üst öğeler
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cancelRequestedQueries >](cancelrequestedqueries-of-wcf.md)|Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../windows-workflow-foundation/tracking-profiles.md)

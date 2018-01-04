---
title: '&lt;activityScheduledQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51db0762c10459d67929867a0fe44908dc7ec750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledquerygt"></a>&lt;activityScheduledQuery&gt;
Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder. Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.  
  
 Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel >  
\<İzleme >  
\<trackingProfile >  
\<İş akışı >  
\<activityScheduledQueries >  
\<activityScheduledQuery >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|activityName|İptal isteyen etkinliğin adını belirten dize.|  
|childActivityName|İptal istendi alt etkinliğin adını belirten dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<activityScheduledQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

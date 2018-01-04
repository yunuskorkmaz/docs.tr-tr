---
title: '&lt;cancelRequestedQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c9ad0f766256d6507775c2cca1b9d54b474abc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt"></a>&lt;cancelRequestedQuery&gt;
Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu temsil eder. Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.  
  
 Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
\<system.serviceModel >  
\<İzleme >  
\<trackingProfile >  
\<İş akışı >  
\<cancelRequestedQueries >  
\<cancelRequestedQuery >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
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
|[\<faultPropagationQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder. Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>       
 [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

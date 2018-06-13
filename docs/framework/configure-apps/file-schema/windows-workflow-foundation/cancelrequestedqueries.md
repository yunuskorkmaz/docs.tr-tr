---
title: '&lt;cancelRequestedQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 2abb2dc05bfec4419ca49d1517084ebc208e81e4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757027"
---
# <a name="ltcancelrequestedqueriesgt"></a>&lt;cancelRequestedQueries&gt;
Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan sorgu koleksiyonunu temsil eder. Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.  
  
 Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<İzleme >  
\<trackingProfile>  
\<İş akışı >  
\<cancelRequestedQueries >  
  
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
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cancelRequestedQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İş akışı >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

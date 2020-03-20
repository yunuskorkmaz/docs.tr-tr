---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152215"
---
# <a name="customtrackingquery"></a>\<customTrackingQuery>
Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder. Sorgu, bir izleme katılımcısının özel izleme kayıtlarına abone olması için gereklidir.  
  
 Profil sorgularını izleme hakkında daha fazla bilgi için [bkz.](../../../windows-workflow-foundation/tracking-profiles.md)  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<izlemeProfil>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışı>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|activityName|İzleme kaydını oluşturan etkinliğin adını belirten dize.|  
|ad|Yayılan özel izleme kaydının adını belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../windows-workflow-foundation/tracking-profiles.md)

---
title: <faultPropagationQueries>WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855270"
---
# <a name="faultpropagationqueries-of-wcf"></a>\<faultPropagationQueries>WCF

Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.  Bu olay, bir FaultHandler hata her işlediğinde oluşur. Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir. Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.  
  
Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
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
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.  Bu olay, bir FaultHandler hata her işlediğinde oluşur.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../windows-workflow-foundation/tracking-profiles.md)

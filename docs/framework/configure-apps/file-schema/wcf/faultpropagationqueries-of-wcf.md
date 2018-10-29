---
title: WCF &lt;faultPropagationQueries&gt;
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 1db99a8d80fad5c0eca93777d87047b43371d048
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202126"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a>WCF &lt;faultPropagationQueries&gt;

Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorguları koleksiyonunu temsil eder.  Bu olay bir FaultHandler bir hata her işlediğinde oluşur. Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir. Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.  
  
Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
\<system.serviceModel>  
\<İzleme >  
\<profilleri >  
\<trackingProfile>  
\<İş akışı >  
\<faultPropagationQueries >  
  
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
|[\<faultPropagationQuery >](faultpropagationquery-of-wcf.md)|Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorgu.  Bu olay bir FaultHandler bir hata her işlediğinde oluşur.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İş akışı >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

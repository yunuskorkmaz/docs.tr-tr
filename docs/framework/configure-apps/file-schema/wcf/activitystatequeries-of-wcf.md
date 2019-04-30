---
title: <activityStateQueries> WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: c9c78b6929b4550204a22fe2e2786891b516a818
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701092"
---
# <a name="activitystatequeries-of-wcf"></a>\<activityStateQueries > WCF

Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için kullanılan sorguları koleksiyonunu temsil eder. Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz. Bu sorgu, etkinlik durumu kayıt nesnelerine abone olmak izleme Katılımcısı için gereklidir. Abone olmak için kullanılabilir durumları ActivityStates belirtilir.

Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).

\<system.serviceModel>  
\<İzleme >  
\<profilleri >  
\<trackingProfile>  
\<İş akışı >  
\<activityStateQueries >  

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
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
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorgu.  Bu olay bir FaultHandler bir hata her işlediğinde oluşur.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<İş akışı >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

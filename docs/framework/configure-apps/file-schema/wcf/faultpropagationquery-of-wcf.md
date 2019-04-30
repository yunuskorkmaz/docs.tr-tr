---
title: <faultPropagationQuery> WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: e5793852d49a052d05f6cb2f4efbe166d67afc62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701053"
---
# <a name="faultpropagationquery-of-wcf"></a>\<faultPropagationQuery > WCF

Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan bir sorgu temsil eder.  Bu olay bir FaultHandler bir hata her işlediğinde oluşur. Bir etkinlik içinde oluşan hataların işlenmesi izlemek için böyle bir sorgu kullanmanız gerekir. Sorgu hata yayma kayıtlara abone olmak izleme Katılımcısı için gereklidir.

Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).

\<system.serviceModel > \
\<İzleme > \
\<profilleri > \
\<trackingProfile > \
\<İş akışı > \
\<faultPropagationQueries > \
\<faultPropagationQuery >

## <a name="syntax"></a>Sözdizimi

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
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
|`faultSourceActivityName`|Hata aktarılacaktır hata işleyicisi etkinliğin adını belirten dize. Varsayılan \*, tüm etkinlikler için hata yayma kayıtları döndürüldüğünü gösterir.|
|`faultHandlerActivityName`|Hata kaynağı olan etkinliğin adını belirten dize.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<faultPropagationQueries >](faultpropagationqueries-of-wcf.md)|Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan yapılandırma öğeleri listesini temsil eder.  Bu olay bir FaultHandler bir hata her işlediğinde oluşur.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

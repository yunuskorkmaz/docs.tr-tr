---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 018ea20342475de40a8392a9272724e37902ecb9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257726"
---
# <a name="states"></a>\<durumları >
İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.  
  
 Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<İzleme >  
\<trackingProfile>  
\<İş akışı >  
\<Workflowınstancequeries >  
\<Workflowınstancequery >  
\<durumları >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
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
|[\<Durum >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Workflowınstancequery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|Başlatılmamış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen sorgu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu koleksiyondaki durumları tarafından döndürülen kayıtları filTRe uygulanır.  
  
 Olası durum değerleri aşağıdaki tabloda açıklanan.  
  
|Durum|Açıklama|  
|-----------|-----------------|  
|İptal edildi|İş akışı örneği iptal edildi.|  
|Tamamlandı|İş akışı örneği tamamlandı.|  
|Silindi|İş akışı örneği silinir.|  
|Boş|İş akışı örneği boş.|  
|Kalıcı|İş akışı örneği kalıcıdır.|  
|Sürdürülüyor|İş akışı örneği işlemi devam etti.|  
|Başlatıldı|İş akışı örneği başlatıldı.|  
|UnhandledException|İş akışı örneği işlenmeyen bir özel durumla karşılaştı.|  
|Kaldırıldı|İş akışı örneği kaldırılır.|  
|İptal edildi|İş akışı örneği iptal edildi.|  
|Askıya alındı|İş akışı örneği askıya alınır.|  
|Sona erdi|İş akışı örneği sonlandırıldı.|  
|Unsuspended|İş akışı örneği unsuspended.|  
  
## <a name="example"></a>Örnek  
 İş akışı örnek düzeyi kayıtları için izleme için aşağıdaki yapılandırma abone `Started` bu sorguyu kullanarak örnek durumu.  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

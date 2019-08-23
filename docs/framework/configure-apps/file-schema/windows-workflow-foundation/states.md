---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fd0b57d7d08cf77ba7792e079b7abd2ff8f2839e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947402"
---
# <a name="states"></a>\<durumlar >
İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumlar koleksiyonunu temsil eder.  
  
 Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<İzleme >  
\<trackingProfile>  
\<iş akışı >  
\<WorkflowInstanceQueries >  
\<WorkflowInstanceQuery >  
\<durumlar >  
  
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
|[\<durum >](states.md)|İzleme kaydı oluşturulduğunda izlenen iş akışı örneğinden abone olunan bir durum.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<WorkflowInstanceQuery >](workflowinstancequery.md)|Başlatılmış veya tamamlanmış olay gibi iş akışı örneği yaşam döngüsü değişikliklerini izleyen bir sorgu.|  
  
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
 Aşağıdaki yapılandırma bu sorguyu kullanarak `Started` örnek durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olur.  
  
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
- [İş Akışı Takip ve İzleme](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../windows-workflow-foundation/tracking-profiles.md)

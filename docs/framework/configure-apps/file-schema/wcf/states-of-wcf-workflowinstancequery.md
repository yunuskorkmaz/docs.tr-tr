---
title: WCF &lt;durumları&gt;, &lt;workflowInstanceQuery&gt;
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: a6c54f0903f30b5a7c3147cf4b874516a766c2b8
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121950"
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a>WCF &lt;durumları&gt;, &lt;workflowInstanceQuery&gt;

İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone olunan durumları koleksiyonunu temsil eder.  
  
Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel > \<İzleme >  
\<profilleri >  
\<trackingProfile>  
\<İş akışı >  
\<Workflowınstancequeries >  
\<Workflowınstancequery >  
\<durumları >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<tracking>
  <profiles>
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
|[\<durumları >](state-of-wcf-workflowinstancequery.md)|İzleme kayıt oluşturulduğunda izlenen iş akışı örneğinin abone olunan bir durumdan.|  
  
### <a name="parent-elements"></a>Üst öğeler  
  
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

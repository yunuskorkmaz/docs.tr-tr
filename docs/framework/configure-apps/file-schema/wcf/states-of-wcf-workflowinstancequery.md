---
title: "WCF &lt;durumları&gt;, &lt;workflowInstanceQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65573b72c91eab41bd3167552ff1f42552f40f6b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a>WCF &lt;durumları&gt;, &lt;workflowInstanceQuery&gt;
İzleme kayıtları oluşturulduğunda izlenen iş akışı örneğinden abone durumlar koleksiyonunu temsil eder.  
  
 Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
 \<system.serviceModel >  
\<İzleme >  
\<trackingProfile >  
\<İş akışı >  
\<Workflowınstancequeries >  
\<Workflowınstancequery >  
\<durumları >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|İzleme kayıt oluşturulduğunda izlenen iş akışı örneği abone durumundan.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Workflowınstancequery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|Başlatılan ya da tamamlanan olay gibi iş akışı örneği yaşam döngüsü değişiklikleri izleyen bir sorgu.|  
  
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
 Aşağıdaki yapılandırma iş akışı örneği düzeyi kayıtları için izleme abone `Started` bu sorguyu kullanarak örnek durumu.  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [İzleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: c2f5e33eff4fdc6dfa85bcc10b59a7c1436cabb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519411"
---
# <a name="ltendtoendtracinggt"></a>&lt;endToEndTracing&gt;
Enable ve disable uçtan uca izleme hizmet uygulamasının çalışması sırasında farklı yönlerini olanak tanıyan bir yapılandırma öğesi.  
  
 \<system.ServiceModel>  
\<Tanılama >  
\<endToEndTracing >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`activityTracing`|Aktivite izlemenin etkin olup olmadığını belirten bir Boole değeri.|  
|`messageFlowTracing`|İleti akışı izlemenin etkin olup olmadığını belirten bir Boole değeri.|  
|`propagateActivity`|Yayma özniteliğinin ayarlanmış olup olmadığını belirten bir Boole değeri true.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|WCF ayarları için çalışma zamanı incelemesi ve denetimi yöneticisi için tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [Uçtan Uca İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)

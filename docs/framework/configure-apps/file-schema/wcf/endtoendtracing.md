---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a>&lt;endToEndTracing&gt;
Etkinleştirme ve devre dışı uçtan uca izleme bir hizmet uygulaması çalışması sırasında farklı yönlerini olanak sağlayan bir yapılandırma öğesi.  
  
 \<Sistem. ServiceModel >  
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
|`activityTracing`|Etkinlik izlemenin etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri.|  
|`messageFlowTracing`|İleti akışı içinde izleme etkin olup olmadığını belirten bir Boole değeri.|  
|`propagateActivity`|Propagate özniteliği ayarlanmış olup olmadığını belirten bir Boole değeri true.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Çalışma zamanı İnceleme için WCF ayarlarını ve yönetici için Denetim tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [Uçtan uca izleme](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)

---
title: '&lt;discoveryClient&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c9cbdb61152a5315aaf919e3a3c58d9329449e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdiscoveryclientgt"></a>&lt;discoveryClient&gt;
Bir özel, bağlama oluşturmak için bir yapılandırma öğesi otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlar.  
  
\<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<discoveryClient >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<discoveryClient discoveryEndpoint="String" >
  <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String" namespace="String" />
    <contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|discoveryEndpoint|Otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlayan bulma uç noktanın adını içeren bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi. Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>

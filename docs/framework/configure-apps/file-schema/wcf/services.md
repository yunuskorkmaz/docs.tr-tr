---
title: '&lt;Hizmetleri&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a2e0d810068db6409bc7b0fd1443a41c3d3ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicesgt"></a>&lt;Hizmetleri&gt;
Hizmetleri tanımlanmış `services` yapılandırma dosyasının. Her hizmetin kendi vardır `service` yapılandırma bölümü.  
  
 \<Sistem. ServiceModel >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Hizmet >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Hizmet sözleşmesi, davranış ve belirli bir hizmet uç noktalarına tanımlayın.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServicesSection>

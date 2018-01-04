---
title: "&lt;appDomainResourceMonitoring&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58caa7458d96ca7bb9088b607a83b2d6be667cae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltappdomainresourcemonitoringgt-element"></a>&lt;appDomainResourceMonitoring&gt; öğesi
İşlem ömrü için işlemdeki tüm uygulama etki alanları istatistikleri toplamak için çalışma zamanı bildirir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<appDomainResourceMonitoring >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı uygulama etki alanı kaynak izleme istatistiklerini toplayıp toplamayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|Uygulama etki alanı kaynak izleme istatistiklerini toplanır.|  
|`false`|Uygulama etki alanı kaynak izleme istatistiklerini toplanmadı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanı kaynak izleme kullanılabilir barındırma yönetilen uygulama etki alanı sınıfı [Iclrappdomainresourcemonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) arabirimi ve olay izleme için Windows (ETW). İzleme etkinleştirildiğinde, istatistikleri işlem ömrü için işlemdeki tüm uygulama etki alanları için toplanır.  
  
 Yönetilen koddan izlemeyi etkinleştirmek için kullanın <xref:System.AppDomain.MonitoringIsEnabled%2A> özelliği.  
  
 Bu yapılandırma öğesi yalnızca kullanılabilir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, uygulama etki alanı kaynak izleme etkinleştirmek gösterilmiştir.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)

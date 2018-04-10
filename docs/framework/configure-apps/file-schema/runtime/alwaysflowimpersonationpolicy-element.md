---
title: '&lt;alwaysFlowImpersonationPolicy&gt; Element'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e32274c6371a73b882f5494c7093945a84d67adf
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a>&lt;alwaysFlowImpersonationPolicy&gt; Element
Windows Identity her zaman kimliğe bürünme nasıl gerçekleştirildiği bağımsız olarak zaman uyumsuz noktaları arasında akan olduğunu belirtir.  
  
 \<Yapılandırma >  
\<runtime>  
\<alwaysFlowImpersonationPolicy>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Windows kimliğini zaman uyumsuz noktaları arasında akan olup olmadığını gösterir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Kimlik akan zaman uyumsuz noktaları arasında kimliğe bürünme üzerinden gerçekleştirilir sürece Windows yöntemleri gibi yönetilen <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Bu varsayılandır.|  
|`true`|Windows Identity her zaman kimliğe bürünme nasıl gerçekleştirildiği bağımsız olarak zaman uyumsuz noktaları arasında akar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 1.0 ve 1.1, Windows kimliğini zaman uyumsuz noktaları arasında geçmez. .NET Framework sürüm 2. 0'da, var olan bir <xref:System.Threading.ExecutionContext> şu anda yürütülen iş parçacığı hakkında bilgi içerir ve uygulama etki alanı içinde zaman uyumsuz noktaları arasında akan nesnesi. <xref:System.Security.Principal.WindowsIdentity> Da akışları kullanarak kimliğe bürünme ulaşılmıştı sağlanan, zaman uyumsuz noktaları arasında akan bilgilerinin bir parçası olarak yönetilen yöntemleri gibi <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> ve platform gibi diğer yollarla üzerinden değil yerel yöntemleri çağırır. Bu öğe, Windows kimlik kimliğe bürünme nasıl ulaşılmıştı bağımsız olarak zaman uyumsuz noktaları arasında akan belirtmek için kullanılır.  
  
 Diğer iki yolla bu varsayılan davranışı değiştirebilirsiniz:  
  
1.  İş parçacığı başına temelinde yönetilen kodu.  
  
     İş parçacığı başına temelinde akış değiştirerek gizleyebilirsiniz <xref:System.Threading.ExecutionContext> ve <xref:System.Security.SecurityContext> kullanarak ayarları <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi.  
  
2.  Ortak dil çalışma zamanı (CLR) yüklemek için çağrısında yönetilmeyen barındırma arabirimi.  
  
     Yönetilmeyen bir barındırma arabirimi (yerine basit Yönetilen yürütülebilir) CLR yüklemek için kullanılırsa, çağrısında özel bayrağa belirtebilirsiniz [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevi. Tüm işlem için Uyumluluk modunu etkinleştirmek için ayarlanmış `flags` parametresi için [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) için `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bir .NET Framework uygulamasında bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulaması için kimliğe bürünme akış bulunan aspnet.config dosyasında yapılandırılabilir \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizin.  
  
 Varsayılan olarak ASP.NET kimliğe bürünme akış aspnet.config dosyasında aşağıdaki yapılandırma ayarları kullanarak devre dışı bırakır:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 ASP.NET, bunun yerine, kimliğe bürünme akışını izin vermek istiyorsanız aşağıdaki yapılandırma ayarları açıkça kullanmalısınız:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kimliğe bürünme araçlarla yönetilen yöntemleri dışında bile elde yüklendiğinde Windows kimliğini zaman uyumsuz noktaları arasında akar belirtin gösterilmektedir.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<Legacyımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)

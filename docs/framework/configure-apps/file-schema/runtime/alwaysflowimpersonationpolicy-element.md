---
title: '&lt;Alwaysflowımpersonationpolicy&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfdc2d434b61d1c1e16ebfdcc2ea423f96254be5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187838"
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a>&lt;Alwaysflowımpersonationpolicy&gt; öğesi
Windows kimlik her zaman arasında nasıl kimliğe bürünme gerçekleştirilip gerçekleştirilmediğine bakılmaksızın zaman uyumsuz noktalar, akışları olduğunu belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<Alwaysflowımpersonationpolicy >  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Windows kimliği zaman uyumsuz noktalar arasında akan olup olmadığını gösterir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Kimlik değil bürünmelerin zaman uyumsuz noktalar arasında kimliğe bürünme üzerinden gerçekleştirilen sürece Windows yöntemleri gibi yönetilen <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Bu varsayılandır.|  
|`true`|Windows kimliği her zaman nasıl kimliğe bürünme gerçekleştirilip gerçekleştirilmediğine bakılmaksızın zaman uyumsuz noktalar arasında akar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 1.0 ve 1.1, Windows kimliği zaman uyumsuz noktalar ötesine geçmeyen. .NET Framework sürüm 2. 0'da, var olan bir <xref:System.Threading.ExecutionContext> yürütülmekte olan iş parçacığını hakkında bilgiler içerir ve uygulama etki alanı içinde zaman uyumsuz noktalar arasında akar. <xref:System.Security.Principal.WindowsIdentity> Ayrıca akışları kullanarak kimliğe bürünme ulaşılmıştı sağlanan zaman uyumsuz noktalar arasında akan bilgileri bir parçası olarak yönetilen yöntemleri gibi <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> ve platform gibi başka bir yolla üzerinden değil yerel yöntemlerini çağırın. Bu öğe, Windows kimlik arasında nasıl kimliğe bürünme elde edilen bağımsız olarak zaman uyumsuz noktalar, akış belirtmek için kullanılır.  
  
 Bu varsayılan davranışı başka iki şekilde değiştirebilirsiniz:  
  
1.  İş parçacığı başına temelinde yönetilen kodda.  
  
     İş parçacığı başına temelinde akışını değiştirerek gösterilmemesini sağlayabilirsiniz <xref:System.Threading.ExecutionContext> ve <xref:System.Security.SecurityContext> kullanarak ayarları <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi.  
  
2.  Ortak dil çalışma zamanı (CLR) yüklemeye çağrısında yönetilmeyen barındırma arabirimi.  
  
     CLR'yi yüklemek için yönetilmeyen bir barındırma arabiriminin (yerine basit yönetilen bir yürütülebilir dosya) kullandıysanız çağrısında bir özel bayrağa belirtebilirsiniz [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevi. İşlemin tümünü Uyumluluk modunu etkinleştirmek için `flags` parametresi için [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) için `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bir .NET Framework uygulamasında bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulaması için kimliğe bürünme akışı bulunan aspnet.config dosyasında yapılandırılabilir \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizin.  
  
 Varsayılan olarak ASP.NET kimliğe bürünme akışı aspnet.config dosyasında aşağıdaki yapılandırma ayarlarını kullanarak devre dışı bırakır:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 ASP.NET'te, kimliğe bürünme akışını bunun yerine, izin vermek istiyorsanız aşağıdaki yapılandırma ayarları açıkça kullanmalısınız:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Windows kimlik kimliğe bürünme yönetilen yöntemleri dışındaki araçlarla bile sağlanır, zaman uyumsuz noktalar arasında akan belirtmek gösterilmektedir.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [\<Legacyımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)

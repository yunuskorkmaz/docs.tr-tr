---
title: "&lt;Legacyımpersonationpolicy&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caeede11d8128af00beb5b1b3426e8c4a5406520
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltlegacyimpersonationpolicygt-element"></a>&lt;Legacyımpersonationpolicy&gt; öğesi
Windows Identity geçerli iş parçacığı üzerinde yürütme bağlamı akış ayarlarına bakılmaksızın zaman uyumsuz noktaları arasında akışını değil belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<Legacyımpersonationpolicy >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Belirleyen <xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktaları arasında bağımsız olarak, akış değil <xref:System.Threading.ExecutionContext> akış geçerli iş parçacığının ayarlar.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>akışları bağlı olarak zaman uyumsuz noktaları arasında <xref:System.Threading.ExecutionContext> akış geçerli iş parçacığı için ayarları. Bu varsayılandır.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>zaman uyumsuz noktaları arasında bağımsız olarak, akış değil <xref:System.Threading.ExecutionContext> akış geçerli iş parçacığının ayarlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürüm 1.0 ve 1.1 <xref:System.Security.Principal.WindowsIdentity> tüm kullanıcı tanımlı zaman uyumsuz noktaları arasında akış değil. .NET Framework sürüm 2.0 ile başlayarak, var olan bir <xref:System.Threading.ExecutionContext> şu anda yürütülen iş parçacığı ve hakkında bilgi içeren nesne uygulama etki alanı içinde zaman uyumsuz noktaları arasında akar. <xref:System.Security.Principal.WindowsIdentity> Bu yürütme bağlamı içinde bulunur ve bu nedenle de zaman uyumsuz noktaları arasında bir kimliğe bürünme bağlamı zaten varsa, bu da akar, yani akar.  
  
 .NET Framework 2.0 ile başlayarak, kullanabilirsiniz `<legacyImpersonationPolicy>` belirtmek için öğesi <xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktaları arasında akış değil.  
  
> [!NOTE]
>  Ortak dil çalışma zamanı (CLR), yönetilmeyen kod veya Win32 işlevleri için doğrudan çağrılar aracılığıyla değil platformu ile gibi yönetilen kod dışında gerçekleştirilen kimliğe bürünme yalnızca yönetilen kodu kullanarak gerçekleştirilen işlemler çağırma kimliğe bürünme bilmektedir. Yalnızca yönetilen <xref:System.Security.Principal.WindowsIdentity> sürece, nesneleri zaman uyumsuz noktaları arasında akış `alwaysFlowImpersonationPolicy` öğesini ayarlamak true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Ayarı `alwaysFlowImpersonationPolicy` öğesi true belirtir Windows kimliği her zaman kimliğe bürünme nasıl gerçekleştirildiği bağımsız olarak zaman uyumsuz noktaları arasında akan olduğunu. Daha fazla bilgi için zaman uyumsuz noktaları arasında akan bilgi yönetilmeyen kimliğe bürünme için bkz: [ \<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
 Diğer iki yolla bu varsayılan davranışı değiştirebilirsiniz:  
  
1.  İş parçacığı başına temelinde yönetilen kodu.  
  
     İş parçacığı başına temelinde akış değiştirerek gizleyebilirsiniz <xref:System.Threading.ExecutionContext> ve <xref:System.Security.SecurityContext> kullanarak ayarları <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi.  
  
2.  Ortak dil çalışma zamanı (CLR) yüklemek için çağrısında yönetilmeyen barındırma arabirimi.  
  
     Yönetilmeyen bir barındırma arabirimi (yerine basit Yönetilen yürütülebilir) CLR yüklemek için kullanılırsa, çağrısında özel bayrağa belirtebilirsiniz [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevi. Tüm işlem için Uyumluluk modunu etkinleştirmek için ayarlanmış `flags` parametresi için [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) STARTUP_LEGACY_IMPERSONATION için.  
  
 Daha fazla bilgi için bkz: [ \<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bir .NET Framework uygulamasında bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulaması için kimliğe bürünme akış bulunan aspnet.config dosyasında yapılandırılabilir \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizin.  
  
 Varsayılan olarak ASP.NET kimliğe bürünme akış aspnet.config dosyasında aşağıdaki yapılandırma ayarları kullanarak devre dışı bırakır:  
  
```  
configuration>  
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
 Aşağıdaki örnek Windows kimliğini zaman uyumsuz noktaları arasında akış olmayan eski davranışı belirtmek nasıl gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)

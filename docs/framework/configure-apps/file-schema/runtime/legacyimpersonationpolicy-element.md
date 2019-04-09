---
title: <legacyImpersonationPolicy> Öğe
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fa6b9aa2b2c427c86da5204a446cc60eadd1bb7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201019"
---
# <a name="legacyimpersonationpolicy-element"></a>\<Legacyımpersonationpolicy > öğesi
Windows kimliği, geçerli iş parçacığı üzerindeki yürütme içeriği için akış ayarlarından bağımsız olarak zaman uyumsuz noktalar arasında geçmeyen belirtir.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Belirten <xref:System.Security.Principal.WindowsIdentity> bağımsız olarak, zaman uyumsuz noktalar ötesine geçmeyen <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı üzerinde akış.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> bağlı olarak zaman uyumsuz noktalar arasındaki akış <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı için akış. Bu varsayılandır.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> bağımsız olarak, zaman uyumsuz noktalar ötesine geçmeyen <xref:System.Threading.ExecutionContext> ayarlar geçerli iş parçacığı üzerinde akış.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürümleri 1.0 ve 1.1 içinde <xref:System.Security.Principal.WindowsIdentity> tüm kullanıcı tanımlı zaman uyumsuz noktalar ötesine geçmeyen. .NET Framework sürüm 2.0 ile başlayarak, bir <xref:System.Threading.ExecutionContext> yürütülmekte olan iş parçacığını ve hakkında bilgi içeren nesne akışları uygulama etki alanı içinde zaman uyumsuz noktalar arasında. <xref:System.Security.Principal.WindowsIdentity> Bu yürütme bağlamında bulunur ve bu nedenle de zaman uyumsuz noktalar arasında bir kimliğe bürünülmüş bağlamdaki varsa, bu da akar, yani akar.  
  
 Kullanabileceğiniz .NET Framework 2.0 ile başlayarak, `<legacyImpersonationPolicy>` belirtmek için öğe <xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktalar ötesine geçmeyen.  
  
> [!NOTE]
>  Ortak dil çalışma zamanı (CLR), yönetilmeyen kod veya Win32 işlevlere doğrudan çağrılar aracılığıyla değil gibi platform yönetilen kod dışında gerçekleştirilen kimliğe bürünme, yalnızca yönetilen kod kullanarak gerçekleştirilen işlemleri çağırmak kimliğe bürünme farkındadır. Yalnızca yönetilen <xref:System.Security.Principal.WindowsIdentity> sürece, nesneler zaman uyumsuz noktalar arasında akış `alwaysFlowImpersonationPolicy` öğe kümesi true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Ayar `alwaysFlowImpersonationPolicy` öğesi true belirtir Windows kimliği her zaman arasında nasıl kimliğe bürünme gerçekleştirilip gerçekleştirilmediğine bakılmaksızın zaman uyumsuz noktalar, geçen. Daha fazla bilgi için bkz: zaman uyumsuz noktalar arasında akan bilgi yönetilmeyen kimliğe bürünme [ \<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
 Bu varsayılan davranışı başka iki şekilde değiştirebilirsiniz:  
  
1.  İş parçacığı başına temelinde yönetilen kodda.  
  
     İş parçacığı başına temelinde akışını değiştirerek gösterilmemesini sağlayabilirsiniz <xref:System.Threading.ExecutionContext> ve <xref:System.Security.SecurityContext> kullanarak ayarları <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi.  
  
2.  Ortak dil çalışma zamanı (CLR) yüklemeye çağrısında yönetilmeyen barındırma arabirimi.  
  
     CLR'yi yüklemek için yönetilmeyen bir barındırma arabiriminin (yerine basit yönetilen bir yürütülebilir dosya) kullandıysanız çağrısında bir özel bayrağa belirtebilirsiniz [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevi. İşlemin tümünü Uyumluluk modunu etkinleştirmek için `flags` parametresi için [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) STARTUP_LEGACY_IMPERSONATION için.  
  
 Daha fazla bilgi için [ \<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bir .NET Framework uygulamasında bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulaması için kimliğe bürünme akışı bulunan aspnet.config dosyasında yapılandırılabilir \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizin.  
  
 Varsayılan olarak ASP.NET kimliğe bürünme akışı aspnet.config dosyasında aşağıdaki yapılandırma ayarlarını kullanarak devre dışı bırakır:  
  
``` xml
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
 Aşağıdaki örnek, Windows kimliği zaman uyumsuz noktalar ötesine geçmeyen eski davranışını belirtmek gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<Alwaysflowımpersonationpolicy > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)

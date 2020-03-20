---
title: <alwaysFlowImpersonationPolicy> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154489"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> Öğesi
Kimliğe bürünme nasıl gerçekleştirildiği ne olursa olsun, Windows kimliğinin her zaman eşzamanlı noktalar arasında aktığını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolitika>**\  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Windows kimliğinin eşzamanlı noktalar arasında akıp akmadığını gösterir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Windows kimliği, kimliğe bürünme gibi <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>yönetilen yöntemlerle yapılmadığı sürece, eşzamanlı noktalar arasında akmaz. Bu varsayılandır.|  
|`true`|Windows kimliği, kimliğe bürünme nasıl gerçekleştirildiği ne olursa olsun, her zaman eşzamanlı noktalar arasında akar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 1.0 ve 1.1 sürümlerinde, Windows kimliği eşzamanlı noktalar arasında akmaz. .NET Framework sürüm 2.0'da, <xref:System.Threading.ExecutionContext> şu anda çalıştırılabilen iş parçacığı hakkında bilgi içeren ve bunu bir uygulama etki alanı içindeki eşzamanlı noktalar arasında akan bir nesne vardır. Ayrıca, <xref:System.Security.Principal.WindowsIdentity> eşzamanlı noktalar arasında akan bilgilerin bir parçası olarak akar, örneğin platform gibi diğer <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> yöntemlerle değil, yerel yöntemlere çağrılması gibi yönetilen yöntemler kullanılarak elde edildi. Bu öğe, kimliğe bürünme nasıl elde edildiklerine bakılmaksızın, Windows kimliğinin eşzamanlı noktalar arasında aktığını belirtmek için kullanılır.  
  
 Bu varsayılan davranışı iki şekilde değiştirebilirsiniz:  
  
1. İş parçacığı başına olarak yönetilen kodda.  
  
     İş parçacığı başına <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>akışı, ", <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>" veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi kullanarak ve ayarları değiştirerek bastırabilirsiniz.  
  
2. Ortak dil çalışma süresini (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.  
  
     CLR'yi yüklemek için yönetilmeyen bir barındırma arabirimi (basit yönetilen çalıştırılabilir lik yerine) kullanılırsa, [CorBindToRuntimeEx Fonksiyonu](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz. Tüm işlem için uyumluluk modunu etkinleştirmek `flags` için [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Fonksiyonu `STARTUP_ALWAYSFLOW_IMPERSONATION`için parametreyi .  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bir .NET Framework uygulamasında, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulama için, kimliğe bürünme akışı \<Windows Klasörü>\Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan aspnet.config dosyasında yapılandırılabilir.  
  
 ASP.NET varsayılan olarak aşağıdaki yapılandırma ayarlarını kullanarak aspnet.config dosyasındaki kimliğe bürünme akışını devre dışı bırakabilirsiniz:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 ASP.NET, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kimliğe bürünme yönetilen yöntemler dışında araçlarla elde edilse bile, Windows kimliğinin eşzamanlı noktalar arasında aktığını nasıl belirteceğimiz gösterilmektedir.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [\<legacyImpersonationPolicy> Öğesi](legacyimpersonationpolicy-element.md)

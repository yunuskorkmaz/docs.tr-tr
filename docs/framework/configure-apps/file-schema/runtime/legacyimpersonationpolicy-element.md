---
title: <legacyImpersonationPolicy> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154110"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy> Öğesi
Geçerli iş parçacığı üzerindeki yürütme bağlamının akış ayarlarına bakılmaksızın, Windows kimliğinin eşzamanlı noktalar arasında akmadığını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Geçerli iş parçacığındaki <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> akış ayarlarından bağımsız olarak, asenkron noktalar arasında akmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>geçerli iş parçacığının akış ayarlarına <xref:System.Threading.ExecutionContext> bağlı olarak asynchronous noktaları boyunca akar. Bu varsayılandır.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>geçerli iş parçacığındaki <xref:System.Threading.ExecutionContext> akış ayarlarına bakılmaksızın, eşzamanlı noktalar arasında akmaz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürümleri 1.0 ve 1.1'de kullanıcı <xref:System.Security.Principal.WindowsIdentity> tanımlı eşsenkronize noktalar arasında akmaz. .NET Framework sürüm 2.0 ile başlayarak, şu anda çalıştırılabilen iş parçacığı hakkında bilgi içeren bir <xref:System.Threading.ExecutionContext> nesne vardır ve bir uygulama etki alanı içinde eşzamanlı noktalar arasında akar. Bu <xref:System.Security.Principal.WindowsIdentity> yürütme bağlamında dahil edilir ve bu nedenle de asynchronous noktaları arasında akar, yani bir kimliğe bürünme bağlamı varsa, o da akacak.  
  
 .NET Framework 2.0 ile başlayarak, `<legacyImpersonationPolicy>` eşzamanlı noktalar <xref:System.Security.Principal.WindowsIdentity> arasında akmayan belirtme öğesini kullanabilirsiniz.  
  
> [!NOTE]
> Ortak dil çalışma süresi (CLR), yönetilen koda platform çağırma veya Win32 işlevlerine doğrudan çağrılar yoluyla gerçekleştirilen işlevler gibi yönetilen kod dışında gerçekleştirilen kimliğe bürünme işlemleri değil, yalnızca yönetilen kod kullanılarak gerçekleştirilen kimliğe bürünme işlemlerinin farkındadır. Yalnızca <xref:System.Security.Principal.WindowsIdentity> yönetilen nesneler, öğe doğru olarak ayarlanmadıkça, eşzamanlı noktalar`<alwaysFlowImpersonationPolicy enabled="true"/>`arasında akabilir ( ). `alwaysFlowImpersonationPolicy` Öğeyi `alwaysFlowImpersonationPolicy` doğru olarak ayarlamak, kimliğe bürünme nasıl gerçekleştirildiğini niçin olursa olsun, Windows kimliğinin her zaman eşzamanlı noktalar arasında aktığını belirtir. Eşzamanlı noktalar arasında yönetilmeyen kimliğe bürünme hakkında daha fazla bilgi [ \<için, her zamanFlowImpersonationPolicy> Öğesi'ne](alwaysflowimpersonationpolicy-element.md)bakın.  
  
 Bu varsayılan davranışı iki şekilde değiştirebilirsiniz:  
  
1. İş parçacığı başına olarak yönetilen kodda.  
  
     İş parçacığı başına <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>akışı, (veya <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemi) kullanarak ve ayarları değiştirerek bastırabilirsiniz.  
  
2. Ortak dil çalışma süresini (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.  
  
     CLR'yi yüklemek için yönetilmeyen bir barındırma arabirimi (basit yönetilen çalıştırılabilir lik yerine) kullanılırsa, [CorBindToRuntimeEx Fonksiyonu](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz. Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx Fonksiyonu](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) nun parametresini STARTUP_LEGACY_IMPERSONATION ayarlayın.  
  
 Daha fazla bilgi için [ \<alwaysFlowImpersonationPolicy> Öğesi'ne](alwaysflowimpersonationpolicy-element.md)bakın.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bir .NET Framework uygulamasında, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulama için, kimliğe bürünme akışı \<Windows Klasörü>\Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan aspnet.config dosyasında yapılandırılabilir.  
  
 ASP.NET varsayılan olarak aşağıdaki yapılandırma ayarlarını kullanarak aspnet.config dosyasındaki kimliğe bürünme akışını devre dışı bırakabilirsiniz:  
  
``` xml
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
 Aşağıdaki örnek, Windows kimliğini niçin asynchronous noktaları arasında akmayacak eski davranışın nasıl belirtilen olduğunu gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [\<alwaysFlowImpersonationPolicy> Öğesi](alwaysflowimpersonationpolicy-element.md)

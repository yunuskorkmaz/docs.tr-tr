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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154110"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy> Öğesi
Geçerli iş parçacığında yürütme bağlamı için akış ayarlarından bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akış yapmaz.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
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
|`enabled`|Gerekli öznitelik.<br /><br /> <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> Geçerli iş parçacığındaki akış ayarlarından bağımsız olarak, öğesinin zaman uyumsuz noktalarda akış yapmaz.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>geçerli iş parçacığının akış ayarlarına bağlı olarak zaman uyumsuz noktalara akar <xref:System.Threading.ExecutionContext> . Bu varsayılandır.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>, <xref:System.Threading.ExecutionContext> geçerli iş parçacığındaki akış ayarlarından bağımsız olarak, zaman uyumsuz noktalarda akış yapmaz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 1,0 ve 1,1 .NET Framework sürümlerinde, <xref:System.Security.Principal.WindowsIdentity> Kullanıcı tanımlı zaman uyumsuz noktalarda akış yapmaz. .NET Framework sürüm 2,0 ' den başlayarak, <xref:System.Threading.ExecutionContext> Şu anda yürütülmekte olan iş parçacığı hakkında bilgi içeren bir nesne vardır ve bir uygulama etki alanı içindeki zaman uyumsuz noktalara akar. , <xref:System.Security.Principal.WindowsIdentity> Bu yürütme bağlamına dahil edilmiştir ve bu nedenle zaman uyumsuz noktalara akar, yani bir kimliğe bürünme bağlamı varsa, bu da akacaktır.  
  
 .NET Framework 2,0 ' den başlayarak, `<legacyImpersonationPolicy>` <xref:System.Security.Principal.WindowsIdentity> zaman uyumsuz noktalarda akış yapmaz öğesini belirtmek için öğesini kullanabilirsiniz.  
  
> [!NOTE]
> Ortak dil çalışma zamanı (CLR), yönetilen kod kullanılarak gerçekleştirilen kimliğe bürünme işlemlerinden, yönetilmeyen koda platform çağırma veya doğrudan Win32 işlevlerine yapılan çağrılar aracılığıyla yapılan kimliğe bürünme işlemlerinden haberdar olur. <xref:System.Security.Principal.WindowsIdentity> `alwaysFlowImpersonationPolicy` Öğe true () olarak ayarlanmadığı takdirde, yalnızca yönetilen nesneler zaman uyumsuz noktalara akabilir `<alwaysFlowImpersonationPolicy enabled="true"/>` . `alwaysFlowImpersonationPolicy`Öğesinin true olarak ayarlanması, kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir. Zaman uyumsuz noktalarda yönetilmeyen kimliğe bürünme ile akan hakkında daha fazla bilgi için bkz. [ \<alwaysFlowImpersonationPolicy> öğesi](alwaysflowimpersonationpolicy-element.md).  
  
 Bu varsayılan davranışı iki farklı şekilde değiştirebilirsiniz:  
  
1. Yönetilen kodda iş parçacığı başına temelinde.  
  
     <xref:System.Threading.ExecutionContext>Ve <xref:System.Security.SecurityContext> ayarlarını <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> , <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemini kullanarak değiştirerek iş parçacığı başına temelinde akışı gizleyebilirsiniz.  
  
2. Ortak dil çalışma zamanını (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.  
  
     CLR yüklemek için yönetilmeyen bir barındırma arabirimi (basit bir yönetilen yürütülebilir dosya yerine) kullanılırsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz. Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx işlevinin](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) parametresini STARTUP_LEGACY_IMPERSONATION olarak ayarlayın.  
  
 Daha fazla bilgi için, bkz. [ \<alwaysFlowImpersonationPolicy> öğesi](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 .NET Framework bir uygulamada, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulaması için, kimliğe bürünme akışı \Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan Aspnet. config dosyasında yapılandırılabilir \<Windows Folder> .  
  
 ASP.NET tarafından varsayılan olarak, aşağıdaki yapılandırma ayarlarını kullanarak ASPNET. config dosyasındaki kimliğe bürünme akışını devre dışı bırakır:  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 ASP.NET ' de, bunun yerine kimliğe bürünme akışına izin vermek istiyorsanız, aşağıdaki yapılandırma ayarlarını açıkça kullanmanız gerekir:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, zaman uyumsuz noktalarda Windows kimliğini Flow olmayan eski davranışın nasıl ekleneceğini gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [\<alwaysFlowImpersonationPolicy>Dosyalarında](alwaysflowimpersonationpolicy-element.md)

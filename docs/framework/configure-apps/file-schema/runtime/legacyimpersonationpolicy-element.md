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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd09598800b74c4807163bc921806f5b470e0d24
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252491"
---
# <a name="legacyimpersonationpolicy-element"></a>\<Legacyımpersonationpolicy > öğesi
Geçerli iş parçacığında yürütme bağlamı için akış ayarlarından bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akış yapmaz.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<Legacyımpersonationpolicy >**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Geçerli iş parçacığındaki <xref:System.Security.Principal.WindowsIdentity> <xref:System.Threading.ExecutionContext> akış ayarlarından bağımsız olarak, öğesinin zaman uyumsuz noktalarda akış yapmaz.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>geçerli iş parçacığının <xref:System.Threading.ExecutionContext> akış ayarlarına bağlı olarak zaman uyumsuz noktalara akar. Bu varsayılandır.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>, geçerli iş parçacığındaki <xref:System.Threading.ExecutionContext> akış ayarlarından bağımsız olarak, zaman uyumsuz noktalarda akış yapmaz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 1,0 ve 1,1 <xref:System.Security.Principal.WindowsIdentity> .NET Framework sürümlerinde, Kullanıcı tanımlı zaman uyumsuz noktalarda akış yapmaz. .NET Framework sürüm 2,0 ' den başlayarak, şu anda yürütülmekte <xref:System.Threading.ExecutionContext> olan iş parçacığı hakkında bilgi içeren bir nesne vardır ve bir uygulama etki alanı içindeki zaman uyumsuz noktalara akar. , <xref:System.Security.Principal.WindowsIdentity> Bu yürütme bağlamına dahil edilmiştir ve bu nedenle zaman uyumsuz noktalara akar, yani bir kimliğe bürünme bağlamı varsa, bu da akacaktır.  
  
 .NET Framework 2,0 ' den başlayarak, zaman uyumsuz noktalarda akış `<legacyImpersonationPolicy>` yapmaz öğesini <xref:System.Security.Principal.WindowsIdentity> belirtmek için öğesini kullanabilirsiniz.  
  
> [!NOTE]
> Ortak dil çalışma zamanı (CLR), yönetilen kod kullanılarak gerçekleştirilen kimliğe bürünme işlemlerinden, yönetilmeyen koda platform çağırma veya doğrudan Win32 işlevlerine yapılan çağrılar aracılığıyla yapılan kimliğe bürünme işlemlerinden haberdar olur. Öğe true <xref:System.Security.Principal.WindowsIdentity> (`<alwaysFlowImpersonationPolicy enabled="true"/>`) olarak ayarlanmadığı takdirde, yalnızca yönetilen nesneler zaman uyumsuz noktalara `alwaysFlowImpersonationPolicy` akabilir. `alwaysFlowImpersonationPolicy` Öğesinin true olarak ayarlanması, kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir. Zaman uyumsuz noktalarda yönetilmeyen kimliğe bürünme ile akan hakkında daha fazla bilgi için bkz [ \<. alwaysFlowImpersonationPolicy > öğesi](alwaysflowimpersonationpolicy-element.md).  
  
 Bu varsayılan davranışı iki farklı şekilde değiştirebilirsiniz:  
  
1. Yönetilen kodda iş parçacığı başına temelinde.  
  
     <xref:System.Threading.ExecutionContext> <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>Ve ayarlarını,<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya yönteminikullanarakdeğiştirerekişparçacığıbaşınatemelindeakışıgizleyebilirsiniz<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>. <xref:System.Security.SecurityContext>  
  
2. Ortak dil çalışma zamanını (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.  
  
     CLR yüklemek için yönetilmeyen bir barındırma arabirimi (basit bir yönetilen yürütülebilir dosya yerine) kullanılırsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz. Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) parametresini STARTUP_LEGACY_IMPERSONATION olarak ayarlayın.  
  
 Daha fazla bilgi için bkz [ \<. alwaysFlowImpersonationPolicy > öğesi](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 .NET Framework bir uygulamada, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulaması için, kimliğe bürünme akışı \<Windows klasörü > \Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan Aspnet. config dosyasında yapılandırılabilir.  
  
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

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [\<alwaysFlowImpersonationPolicy > öğesi](alwaysflowimpersonationpolicy-element.md)

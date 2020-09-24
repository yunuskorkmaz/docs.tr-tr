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
ms.openlocfilehash: 9316f026a807b6ad36014157061f67bdbd7d3d18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149445"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> Öğesi

Kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Windows kimliğinin zaman uyumsuz noktalarda akış yapılıp yapılmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Kimliğe bürünme, gibi yönetilen yöntemler aracılığıyla gerçekleştirilmediği sürece, Windows kimliği zaman uyumsuz noktalarda akış yapmaz <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> . Bu varsayılan seçenektir.|  
|`true`|Windows kimliği, kimliğe bürünme işlemi ne olursa olsun, her zaman zaman uyumsuz noktalara akar.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 .NET Framework sürüm 1,0 ve 1,1 ' de, Windows kimliği zaman uyumsuz noktalarda akış yapmaz. .NET Framework sürüm 2,0 ' de, <xref:System.Threading.ExecutionContext> yürütülmekte olan iş parçacığı hakkında bilgi içeren bir nesne vardır ve bir uygulama etki alanı içindeki zaman uyumsuz noktalara akar. <xref:System.Security.Principal.WindowsIdentity>Aynı zamanda, kimliğe bürünmeyi <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> Yerel yöntemlere yönelik platform Invoke gibi diğer yollarla değil, gibi yönetilen yöntemler kullanılarak elde edildiği zaman uyumsuz noktalarda akan bilgilerin bir parçası olarak da akar. Bu öğe, kimliğe bürünme 'nin nasıl elde edildiğini bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akmasını belirtmek için kullanılır.  
  
 Bu varsayılan davranışı iki farklı şekilde değiştirebilirsiniz:  
  
1. Yönetilen kodda iş parçacığı başına temelinde.  
  
     <xref:System.Threading.ExecutionContext>Ve <xref:System.Security.SecurityContext> ayarlarını <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> ,, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> veya <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> yöntemini kullanarak değiştirerek iş parçacığı başına temelinde akışı gizleyebilirsiniz.  
  
2. Ortak dil çalışma zamanını (CLR) yüklemek için yönetilmeyen barındırma arabirimine yapılan çağrıda.  
  
     CLR yüklemek için yönetilmeyen bir barındırma arabirimi (basit bir yönetilen yürütülebilir dosya yerine) kullanılırsa, [CorBindToRuntimeEx işlevi](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan çağrıda özel bir bayrak belirtebilirsiniz. Tüm işlemin uyumluluk modunu etkinleştirmek için `flags` [CorBindToRuntimeEx işlevinin](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) parametresini olarak ayarlayın `STARTUP_ALWAYSFLOW_IMPERSONATION` .  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  

 .NET Framework bir uygulamada, bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.  
  
 Bir ASP.NET uygulaması için, kimliğe bürünme akışı \Microsoft.NET\Framework\vx.x.xxxx dizininde bulunan aspnet.config dosyasında yapılandırılabilir \<Windows Folder> .  
  
 ASP.NET tarafından varsayılan olarak, aşağıdaki yapılandırma ayarlarını kullanarak aspnet.config dosyasındaki kimliğe bürünme akışını devre dışı bırakır:  
  
```xml
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

 Aşağıdaki örnek, kimliğe bürünme, yönetilen yöntemlerin dışında bir şekilde elde edildiğinde, Windows kimliğinin zaman uyumsuz noktalarda akışa nasıl ekleneceğini gösterir.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [\<legacyImpersonationPolicy> Dosyalarında](legacyimpersonationpolicy-element.md)

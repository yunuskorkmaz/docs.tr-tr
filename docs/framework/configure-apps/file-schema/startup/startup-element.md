---
title: "&lt;Başlangıç&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4a502cb309bce3a1a2fb55c9e5477b7a6a395960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstartupgt-element"></a>&lt;Başlangıç&gt; öğesi
Ortak dil çalışma zamanı başlangıç bilgileri belirtir.  
  
 \<Yapılandırma >  
\<Başlangıç >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|İsteğe bağlı öznitelik.<br /><br /> Etkinleştirilip etkinleştirilmeyeceğini belirtir [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] çalışma zamanı etkinleştirme İlkesi kullanmak için veya [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] etkinleştirme ilkesi.|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|Etkinleştirme [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] eski çalışma zamanı etkinleştirme teknikleri bağlamak için seçilen çalışma için çalışma zamanı etkinleştirme İlkesi (gibi [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) yerine yapılandırma dosyasından seçilen çalışma zamanı bunları CLR Version 2.0 sürümü capping. Bu nedenle, CLR sürüm 4 veya sonrası yapılandırma dosyasından seçilirse, .NET Framework'ün önceki sürümleriyle oluşturulan karma mod derlemeleri ile seçilen CLR sürümü yüklenir. Bu değer ayarlandığında CLR sürüm 1.1 veya CLR Version 2.0 sürümü etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma aynı işlemine yüklenmesini engeller.|  
|`false`|Etkinleştirme için varsayılan bir ilke kullanmak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra eski çalışma zamanı etkinleştirme teknikleri CLR sürüm 1.1 veya 2.0 yükleme işlemine izin vermek için. Bu değer ayarlandığında, karma mod derlemeleri .NET Framework 4 veya sonraki sürümüyle oluşturulmuş sürece yüklenmesini .NET Framework 4 veya sonraki engeller. Bu varsayılan değerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Uygulamanın yalnızca sürüm 1.0 ortak dil çalışma zamanı desteklediğini belirtir. Çalışma zamanı sürüm 1.1 veya üstünün ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.|  
|[\<supportedRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
  **\<SupportedRuntime >** öğesi sürüm 1.1 veya üstünün çalışma zamanının kullanılarak oluşturulan tüm uygulamalar tarafından kullanılmalıdır. Yalnızca sürüm 1.0 çalışma zamanının desteklemek için oluşturulan uygulamaların kullanmalıdır  **\<requiredRuntime >** öğesi.  
  
 Microsoft Internet Explorer'da barındırılan bir uygulama için başlangıç kodu yoksayar  **\<başlangıç >** öğesi ve kendi alt öğelerini.  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy özniteliği  
 Bu öznitelik, uygulamanız eski etkinleştirme yolları gibi kullanıyorsa yararlıdır [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), ve önceki bir sürümünü yerine CLR sürüm 4 etkinleştirmek için bu yollar istediğiniz veya uygulamanız ise ile oluşturulan [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ancak bir bağımlılığa sahip .NET Framework'ün önceki bir sürümüyle oluşturulmuş bir karma mod derleme üzerinde. Bu senaryolarda, öznitelik kümesine `true`.  
  
> [!NOTE]
>  Öznitelik ayarını `true` CLR sürüm 1.1 veya CLR Version 2.0 sürümü aynı işlemine etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma yüklenmesini engeller (bkz [COM birlikte çalışma için yan yana yürütme](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çalışma zamanı sürümü bir yapılandırma dosyası belirtmek nasıl gösterir.  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [COM birlikte çalışma için yan yana yürütme](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [İşlem İçi Yan Yana Yürütme](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)

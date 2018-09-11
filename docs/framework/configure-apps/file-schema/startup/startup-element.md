---
title: '&lt;Başlangıç&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4d39dc28082fbed932a60228ac216f2f700c2e9f
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44366065"
---
# <a name="ltstartupgt-element"></a>&lt;Başlangıç&gt; öğesi
Ortak dil çalışma zamanı başlatma bilgileri belirtir.  
  
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
|`useLegacyV2RuntimeActivationPolicy`|İsteğe bağlı öznitelik.<br /><br /> Etkinleştirilip etkinleştirilmeyeceğini belirtir [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] çalışma zamanı etkinleştirme İlkesi mi kullanılacağını [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] etkinleştirme ilkesi.|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|Etkinleştirme [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] eski çalışma zamanını etkinleştirme teknikleri bağlama için olan seçilen çalışma zamanı, çalışma zamanı etkinleştirme İlkesi (gibi [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) yerine yapılandırma dosyasından seçilen çalışma zamanı bunları CLR Version 2.0 sürümü capping. Bu nedenle, CLR 4 veya sonraki bir sürümü yapılandırma dosyasından seçilirse, .NET Framework'ün önceki sürümleriyle oluşturulmuş karışık mod derlemeleri seçilen CLR sürümü ile yüklenir. Bu değer ayarlandığında CLR sürüm 1.1 veya CLR Version 2.0 sürümü ile aynı işleme etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma, yükleme engeller.|  
|`false`|İçin varsayılan etkinleştirme ilkeyi [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ve daha sonra eski çalışma zamanını etkinleştirme teknikleri'CLR sürüm 1.1 veya 2.0 işleme yüklemek izin vermek için. Bu değeri ayarlamak, karma mod derlemeler .NET Framework 4 veya sonraki sürümüyle oluşturulmuş karşılamadıkça .NET Framework 4 veya daha sonra yüklemeyi engeller. Bu varsayılan değerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir. Çalışma zamanı sürüm 1.1 veya üzeri ile oluşturulan uygulamaların kullanması gereken  **\<supportedRuntime >** öğesi.|  
|[\<supportedRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Uygulamanın hangi ortak dil çalışma zamanı sürümünü desteklediğini belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 **\<SupportedRuntime >** öğesi sürüm 1.1 veya daha sonraki çalışma zamanı sürümü kullanılarak oluşturulan tüm uygulamalar tarafından kullanılması gerekir. Yalnızca sürüm 1.0 çalışma zamanını desteklemek için oluşturulan uygulamalar kullanmalıdır  **\<requiredRuntime >** öğesi.  
  
 Microsoft Internet Explorer'da barındırılan bir uygulama için başlatma kodunun yoksayar  **\<başlangıç >** öğesi ve onun alt öğeleri.  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy özniteliği  
 Bu uygulamanız gibi eski etkinleştirme yollarını kullanıyorsa yararlı bir özniteliktir [CorBindToRuntimeEx işlevi](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), ve daha önceki bir sürümü yerine CLR'nin sürüm 4 etkinleştirmek için bu yollar istediğiniz veya uygulamanız ise ile oluşturulmuş [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ancak bağımlıdır .NET Framework'ün önceki bir sürümüyle oluşturulmuş bir karma mod derleme. Bu senaryolarda, öznitelik ayarlanmış `true`.  
  
> [!NOTE]
>  Özniteliğini `true` CLR sürüm 1.1 veya CLR Version 2.0 sürümü ile aynı işleme, etkili bir şekilde işlem içi yan yana özelliğini devre dışı bırakma yüklenmesini engeller (bkz [COM birlikte çalışma için yan yana yürütme](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümü belirtmek gösterilmektedir.  
  
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
 [\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [COM birlikte çalışma için yan yana yürütme](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [İşlem İçi Yan Yana Yürütme](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)

---
title: '&lt;requiredRuntime&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac1e1f7bc36d8d2b12b99de2794bb0ba31ddbd7a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398738"
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime&gt; öğesi
Uygulama yalnızca sürüm 1.0 ortak dil çalışma zamanının desteklediğini belirtir. Bu öğe, kullanım dışı ve artık kullanılmalıdır. [ `supportedRuntime` ](supportedruntime-element.md) Öğesi bunun yerine kullanılmalıdır.
  
 \<Yapılandırma >  
\<Başlangıç >  
\<requiredRuntime >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`version`|İsteğe bağlı öznitelik.<br /><br /> Bu uygulamanın desteklediği .NET Framework sürümünü belirten bir dize değeri. Dize değeri, .NET Framework yükleme kökü altında bulunan dizin adı eşleşmelidir. Dize değeri içeriğini çözümlenmemiş.|  
|`safemode`|İsteğe bağlı öznitelik.<br /><br /> Çalışma zamanı başlatma kodunu çalışma zamanı sürümünü belirlemek için kayıt defterini arayıp aramayacağını belirtir.|  
  
## <a name="safemode-attribute"></a>safemode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı başlatma kodunu kayıt defterinde arar. Varsayılan değer budur.|  
|`true`|Çalışma zamanı başlatma kodunu kayıt defterinde aramaz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`startup`|İçeren `<requiredRuntime>` öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca sürüm 1.0 çalışma zamanını desteklemek için oluşturulan uygulamalar kullanmalıdır `<requiredRuntime>` öğesi. Sürüm 1.1 veya daha sonraki çalışma zamanı sürümü kullanılarak oluşturulan uygulamalar kullanmalıdır `<supportedRuntime>` öğesi.  
  
> [!NOTE]
>  Kullanırsanız [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) yapılandırma dosyasını belirtmek için işlev, kullanmanız gereken `<requiredRuntime>` çalışma zamanının tüm sürümleri için öğesi. `<supportedRuntime>` Öğesi yok sayıldı kullandığınızda [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 `version` Öznitelik dizesini belirtilen .NET Framework sürümü için yükleme klasör adıyla eşleşmelidir. Bu dize yorumlanmaz. Çalışma zamanı başlatma kodunu eşleşen bir klasör bulamazsa, çalışma zamanı yüklenmedi; Başlangıç kodu, hata iletisi gösterir ve sonlandırılır.  
  
> [!NOTE]
>  Microsoft Internet Explorer'da barındırılan bir uygulama için başlatma kodunun yoksayar `<requiredRuntime>` öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yapılandırma dosyasında çalışma zamanı sürümü belirtmek gösterilmektedir.  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)

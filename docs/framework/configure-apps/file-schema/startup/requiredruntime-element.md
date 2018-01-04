---
title: "&lt;requiredRuntime&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 12be2350cb123407b2f71d1f5f07e836ccddb9c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime&gt; öğesi
Uygulamanın yalnızca sürüm 1.0 ortak dil çalışma zamanı desteklediğini belirtir. Bu öğe kullanım dışıdır ve artık kullanılmalıdır. [ `supportedRuntime` ](supportedruntime-element.md) Öğesi bunun yerine kullanılmalıdır.
  
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
|`version`|İsteğe bağlı öznitelik.<br /><br /> Bu uygulama destekleyen .NET Framework sürümünü belirten bir dize değeri. Dize değeri, .NET Framework yükleme kök altında bulunan dizin adı eşleşmelidir. Dize değeri içeriğini çözümlenmemiş.|  
|`safemode`|İsteğe bağlı öznitelik.<br /><br /> Çalışma zamanı başlatma kodunu çalışma zamanı sürümü belirlemek üzere kayıt defterini aramayacağını belirtir.|  
  
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
 Yalnızca sürüm 1.0 çalışma zamanının desteklemek için oluşturulan uygulamaların kullanmalıdır `<requiredRuntime>` öğesi. Sürüm 1.1 veya üstünün çalışma zamanı ile oluşturulan uygulamaların kullanmalıdır `<supportedRuntime>` öğesi.  
  
> [!NOTE]
>  Kullanırsanız [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) yapılandırma dosyası belirtmek için işlev, kullanmalısınız `<requiredRuntime>` öğesi çalışma zamanının tüm sürümler için. `<supportedRuntime>` Öğesi göz ardı edilir kullandığınızda [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 `version` Öznitelik dizesini belirtilen .NET Framework sürümü için yükleme klasör adı eşleşmelidir. Bu dize yorumlanmaz. Çalışma zamanı başlatma kodunu eşleşen bir klasörü bulamazsa, çalışma zamanının yüklü değil; Başlangıç kodu bir hata iletisi gösterir ve sonlandırılıyor.  
  
> [!NOTE]
>  Microsoft Internet Explorer'da barındırılan bir uygulama için başlangıç kodu yoksayar `<requiredRuntime>` öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çalışma zamanı sürümü bir yapılandırma dosyası belirtmek nasıl gösterir.  
  
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
 [\<PaveOver > hangi çalışma zamanı sürümünün kullanılacağını belirtme](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)

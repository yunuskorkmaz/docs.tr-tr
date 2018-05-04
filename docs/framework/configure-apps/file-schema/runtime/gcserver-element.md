---
title: '&lt;gcServer&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027176bdff644a6ff3314df7484ed88ace93001b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltgcservergt-element"></a>&lt;gcServer&gt; öğesi
Ortak dil çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<gcServer>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Sunucu çöp toplama çalışmaz. Bu varsayılandır.|  
|`true`|Sunucu çöp toplama çalışır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) çöp toplama iki türlerini destekler: tüm sistemlerde kullanılabilir iş istasyonu çöp toplama ve çok işlemcili sistemlerde kullanılabilir sunucu çöp toplama. Kullandığınız `<gcServer>` çöp toplama CLR türünü denetlemek için öğesi gerçekleştirir. Kullanım <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> sunucu çöp toplama etkin olup olmadığını belirlemek için özellik.  
  
 Tek işlemcili bilgisayarlar için varsayılan iş istasyonu çöp toplama en hızlı seçeneği olmalıdır. İş istasyonu veya sunucu iki işlemcili bilgisayarlar için kullanılabilir. Sunucu çöp toplama ikiden fazla işlemci için en hızlı seçeneği olmalıdır.  
  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yoksayılır.  
  
> [!NOTE]
>  Sunucu çöp toplama etkin değilse .NET Framework 4 ve önceki sürümlerinde eşzamanlı atık toplama kullanılamaz. İle başlayarak [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], sunucu çöp toplama eşzamanlı. Eşzamanlı olmayan sunucu çöp toplama kullanmak üzere ayarlanmış `<gcServer>` öğesine `true` ve [ \<gcConcurrent > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) için `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, sunucu çöp toplama sağlar.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Nasıl yapılır: eş zamanlı çöp toplama devre dışı bırak](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)

---
title: '&lt;gcConcurrent&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee00c3a307523d2cae831274630ad6828cd9daf6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745844"
---
# <a name="ltgcconcurrentgt-element"></a>&lt;gcConcurrent&gt; öğesi
Ortak dil çalışma zamanı ayrı bir iş parçacığı üzerinde çöp toplama çalışıp çalışmayacağını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<gcConcurrent >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma Zamanı Modülü çöp toplama eşzamanlı olarak çalışıp çalışmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çöp toplama eşzamanlı olarak çalışmaz.|  
|`true`|Çöp toplama eşzamanlı olarak çalışır. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 önce iş istasyonu çöp toplama ayrı bir iş parçacığı üzerinde arka planda çöp toplama gerçekleştirilen eşzamanlı atık toplama desteklenir. .NET Framework 4'te eşzamanlı atık toplama, arka plan çöp toplama ayrı bir iş parçacığı üzerinde arka planda de gerçekleştirir GC tarafından değiştirildi. .NET Framework 4. 5'ile başlayarak, arka plan toplama sunucu çöp toplama içinde kullanılabilir hale geldi. `<gcConcurrent>` Öğesi denetimleri çalışma zamanı ya da eşzamanlı gerçekleştirip gerçekleştirmediğini veya varsa veya ön planda çöp toplama gerçekleştiğini atık toplama, arka plan.  
  
> [!WARNING]
>  .NET Framework 4 ile başlayarak, eşzamanlı atık toplama arka plan atık toplama işlemi tarafından değiştirilir. Koşulları *eşzamanlı* ve *arka plan* .NET Framework belgelerinde birbirlerinin yerine kullanılır. Arka plan çöp toplama devre dışı bırakmak için `<gcConcurrent>` bu makalede anlatıldığı gibi öğesi.  
  
 Varsayılan, eş zamanlı çalışma zamanı kullanır veya arka plan çöp toplama, hangi gecikmesi için optimize edilmiştir. Uygulamanızı ağır kullanıcı etkileşimi gerektiriyorsa, eşzamanlı atık toplama çöp toplama gerçekleştirmek için uygulamanın Duraklat süresini en aza indirmek için etkin bırakın. Ayarlarsanız `enabled` özniteliği `<gcConcurrent>` öğesine `false`, üretilen iş için en iyi duruma getirilmiş eşzamansız atık toplama çalışma zamanı kullanır. Aşağıdaki yapılandırma dosyası arka plan çöp toplama devre dışı bırakır.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Varsa bir `<gcConcurrentSetting>` makine yapılandırma dosyasında ayarlama, tüm .NET Framework uygulamaları için varsayılan değer tanımlar. Makine yapılandırma dosyası ayarı uygulama yapılandırma dosyası ayarını geçersiz kılar.  
  
 Daha fazla eşzamanlı hakkında bilgi ve arka plan çöp toplama için "eşzamanlı atık toplama" bölümüne bakın [çöp toplama Temelleri](../../../../../docs/standard/garbage-collection/fundamentals.md) konu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek eşzamanlı atık toplama etkinleştirir.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Atık Toplamanın Temelleri](../../../../../docs/standard/garbage-collection/fundamentals.md)

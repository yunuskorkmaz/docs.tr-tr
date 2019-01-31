---
title: <gcConcurrent> Öğesi
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
ms.openlocfilehash: ae20e33f610acf77f2039b94803a19d371b771c0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265993"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent > öğesi
Ortak dil çalışma zamanının atık toplama ayrı bir iş parçacığı üzerinde çalışıp çalışmayacağını belirtir.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının atık toplama eşzamanlı olarak çalışıp çalışmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çöp toplama, eşzamanlı olarak çalıştırmaz.|  
|`true`|Atık toplama eşzamanlı olarak çalışır. Bu varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Önce .NET Framework 4, atık toplama arka planda ayrı bir iş parçacığı üzerinde gerçekleştirilen eşzamanlı atık toplama, iş istasyonu çöp toplama desteklenir. .NET Framework 4'te, eş zamanlı çöp toplama, arka plan da ayrı bir iş parçacığı üzerinde arka planda atık toplama gerçekleştirir GC, tarafından değiştirildi. .NET Framework 4.5 ile başlayarak, arka plan koleksiyonu sunucu çöp toplamada kullanıma sunulmuştur. `<gcConcurrent>` Öğesi, çalışma zamanı ya da eşzamanlı gerçekleştirip gerçekleştirmediğini kontrol eder veya varsa veya ön planda atık toplama gerçekleştiğini plan çöp toplama.  
  
> [!WARNING]
>  .NET Framework 4 ile başlayarak, eşzamanlı atık toplama arka plan atık toplama işlemi tarafından değiştirilir. Koşulları *eşzamanlı* ve *arka plan* .NET Framework belgelerinde birbirinin yerine kullanılır. Arka plan çöp toplama devre dışı bırakmak için `<gcConcurrent>` bu makalede ele alınan öğesi.  
  
 Varsayılan, çalışma zamanı kullanan eş zamanlı veya arka plan çöp toplama, hangi gecikme süresi için optimize edilmiştir. Uygulamanız yoğun bir kullanıcı etkileşimi gerektiriyorsa, eşzamanlı çöp toplama atık toplama işini gerçekleştirmek için uygulamanın duraklatma süresi en aza indirmek için etkin bırakın. Ayarlarsanız `enabled` özniteliği `<gcConcurrent>` öğesine `false`, aktarım hızı için en iyi duruma getirilmiş eşzamanlı olmayan çöp toplama, çalışma zamanı kullanır. Şu yapılandırma dosyasını arka plan çöp toplama devre dışı bırakır.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Varsa bir `<gcConcurrentSetting>` makine yapılandırma dosyasında ayarı, tüm .NET Framework uygulamaları için varsayılan değer tanımlar. Makine yapılandırma dosyası ayarı, uygulama yapılandırma dosyası ayarı geçersiz kılar.  
  
 Daha fazla eşzamanlı hakkında bilgi ve arka plan çöp toplama için "eş zamanlı çöp toplama" bölümüne bakın. [çöp toplamanın Temelleri](../../../../../docs/standard/garbage-collection/fundamentals.md) konu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, eş zamanlı çöp toplama sağlar.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Atık Toplamanın Temelleri](../../../../../docs/standard/garbage-collection/fundamentals.md)

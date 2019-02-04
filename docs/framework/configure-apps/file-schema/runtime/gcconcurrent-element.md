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
ms.openlocfilehash: 0e2be4d9384f1e1ef73ce6064184aa2621a517a8
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674600"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent > öğesi

Ortak dil çalışma zamanının atık toplama ayrı bir iş parçacığı üzerinde çalışıp çalışmayacağını belirtir.

\<Yapılandırma > \
\<çalışma zamanı > \
\<gcConcurrent >

## <a name="syntax"></a>Sözdizimi

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının atık toplama eşzamanlı olarak çalışıp çalışmayacağını belirtir.|

## <a name="enabled-attribute"></a>Etkin öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çöp toplama, eşzamanlı olarak çalıştırılmaz.|
|`true`|Atık toplama eşzamanlı olarak çalışır. Bu varsayılandır.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Önce .NET Framework 4, atık toplama arka planda ayrı bir iş parçacığı üzerinde gerçekleştirilen eşzamanlı atık toplama, iş istasyonu çöp toplama desteklenir. .NET Framework 4'te, eş zamanlı çöp toplama, arka plan da ayrı bir iş parçacığı üzerinde arka planda atık toplama gerçekleştirir GC, tarafından değiştirildi. .NET Framework 4.5 ile başlayarak, arka plan koleksiyonu sunucu çöp toplamada kullanıma sunulmuştur. `<gcConcurrent>` Öğesi, çalışma zamanı ya da eşzamanlı gerçekleştirip gerçekleştirmediğini kontrol eder veya varsa veya ön planda atık toplama gerçekleştiğini plan çöp toplama.

### <a name="to-disable-background-garbage-collection"></a>Arka plan çöp toplama devre dışı bırakmak için

> [!WARNING]
> .NET Framework 4 ile başlayarak, eşzamanlı atık toplama arka plan atık toplama işlemi tarafından değiştirilir. Koşulları *eşzamanlı* ve *arka plan* .NET Framework belgelerinde birbirinin yerine kullanılır. Arka plan çöp toplama devre dışı bırakmak için `<gcConcurrent>` bu makalede ele alınan öğesi.

Varsayılan, çalışma zamanı kullanan eş zamanlı veya arka plan çöp toplama, hangi gecikme süresi için optimize edilmiştir. Uygulamanız yoğun bir kullanıcı etkileşimi gerektiriyorsa, eşzamanlı çöp toplama atık toplama işini gerçekleştirmek için uygulamanın duraklatma süresi en aza indirmek için etkin bırakın. Ayarlarsanız `enabled` özniteliği `<gcConcurrent>` öğesine `false`, aktarım hızı için en iyi duruma getirilmiş eşzamanlı olmayan çöp toplama, çalışma zamanı kullanır. Şu yapılandırma dosyasını arka plan çöp toplama devre dışı bırakır.

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 Varsa bir `<gcConcurrentSetting>` makine yapılandırma dosyasında ayarı, tüm .NET Framework uygulamaları için varsayılan değer tanımlar. Makine yapılandırma dosyası ayarı, uygulama yapılandırma dosyası ayarı geçersiz kılar.

 Daha fazla eşzamanlı hakkında bilgi ve arka plan çöp toplama için bkz: [eş zamanlı çöp toplama](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) konusundaki [çöp toplamanın Temelleri](../../../../standard/garbage-collection/fundamentals.md) makalesi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, eş zamanlı çöp toplama sağlar:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Atık Toplamanın Temelleri](../../../../standard/garbage-collection/fundamentals.md)

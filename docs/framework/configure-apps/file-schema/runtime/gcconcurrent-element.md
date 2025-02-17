---
description: 'Daha fazla bilgi edinin: <gcConcurrent> öğesi'
title: gcConcurrent öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: dff8b073977c007a132cfbd685724a02ba37684b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787012"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent> öğesi

Ortak dil çalışma zamanının ayrı bir iş parçacığında çöp toplama işlemi yapıp yapmadığını belirtir.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a>Syntax

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br />Çalışma zamanının çöp toplamayı eşzamanlı olarak çalıştırmasını belirtir.|

#### <a name="enabled-attribute"></a>enabled özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çöp toplamayı eşzamanlı olarak çalıştırmaz.|
|`true`|Çöp toplamayı eşzamanlı olarak çalıştırır. Bu varsayılan seçenektir.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

.NET Framework 4 ' ten önce iş istasyonu atık toplama, farklı bir iş parçacığında arka planda çöp toplamayı gerçekleştiren eşzamanlı çöp toplama işlemini destekliyordu. .NET Framework 4 ' te, eşzamanlı atık toplama, arka plan GC ile değiştirilmiştir ve bu da ayrı bir iş parçacığında arka planda çöp toplama işlemi gerçekleştirir. .NET Framework 4,5 ' den başlayarak, arka plan koleksiyonu sunucu atık toplamada kullanılabilir duruma geldi. **GcConcurrent** öğesi, çalışma zamanının, varsa veya ön planda çöp toplama gerçekleştirip gerçekleştirmediğini kontrol eder.

### <a name="to-disable-background-garbage-collection"></a>Arka plan atık toplamayı devre dışı bırakmak için

> [!WARNING]
> .NET Framework 4 ' ten itibaren, eşzamanlı atık toplama, arka plan atık toplama ile değiştirilmiştir. *Eşzamanlı* ve *arka plan* terimleri .NET Framework belgelerde birbirinin yerine kullanılır. Arka plan atık toplamayı devre dışı bırakmak için, bu makalede anlatıldığı gibi **gcConcurrent** öğesini kullanın.

Varsayılan olarak, çalışma zamanı, gecikme süresi için en iyi duruma getirilmiş olan eşzamanlı veya arka plan çöp toplamayı kullanır. Uygulamanız ağır Kullanıcı etkileşimi içeriyorsa, çöp toplama işlemini gerçekleştirmek için uygulamanın duraklatma süresini en aza indirmek için eşzamanlı çöp toplamayı etkin bırakın. `enabled` **GcConcurrent** öğesinin özniteliğini olarak ayarlarsanız `false` , çalışma zamanı, aktarım hızı için iyileştirilmiş, eşzamanlı olmayan çöp toplamayı kullanır.

Aşağıdaki yapılandırma dosyası arka plan atık toplamayı devre dışı bırakır:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

Makine yapılandırma dosyasında bir **gcConcurrentSetting** ayarı varsa, tüm .NET Framework uygulamalar için varsayılan değeri tanımlar. Makine yapılandırma dosyası ayarı, uygulama yapılandırma dosyası ayarını geçersiz kılar.

Eşzamanlı ve arka plan atık toplama hakkında daha fazla bilgi için bkz. [arka plan atık toplama](../../../../standard/garbage-collection/background-gc.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, arka plan atık toplamayı mümkün bir şekilde sunar:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Atık Toplamanın Temelleri](../../../../standard/garbage-collection/fundamentals.md)

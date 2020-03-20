---
title: gcEşzamanlı Eleman
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400045"
---
# <a name="gcconcurrent-element"></a>\<gcEşzamanlı> elemanı

Ortak dil çalışma zamanının çöp toplamayı ayrı bir iş parçacığı üzerinde çalıştırıp çalıştırmadığını belirtir.

[\<yapılandırma>](../configuration-element.md)\
&nbsp;&nbsp;[\<çalışma zamanı>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcEşzamanlı>

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
|`enabled`|Gerekli öznitelik.<br /><br />Çalışma zamanının çöp toplamayı aynı anda çalıştırıp çalıştırmadığını belirtir.|

#### <a name="enabled-attribute"></a>etkin öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çöp toplamayı aynı anda çalıştırmıyor.|
|`true`|Çöp toplamayı aynı anda çalıştırın. Bu varsayılandır.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

.NET Framework 4'ten önce, iş istasyonu çöp toplama, arka planda ayrı bir iş parçacığı üzerinde çöp toplama işlemini gerçekleştiren eşzamanlı çöp toplamayı destekler. .NET Framework 4'te, eşzamanlı çöp toplama, arka planda ayrı bir iş parçacığı üzerinde çöp toplama da gerçekleştiren arka plan GC ile değiştirildi. .NET Framework 4.5 ile başlayarak, arka plan koleksiyonu sunucu çöp toplama kullanılabilir hale geldi. **gcConcurrent** öğesi, çalışma zamanının eşzamanlı veya arka plan çöp toplama gerçekleştirip gerçekleştirmediğini, kullanılabilir olup olmadığını veya ön planda çöp toplama yı gerçekleştirip gerçekleştirmediğini denetler.

### <a name="to-disable-background-garbage-collection"></a>Arka plan çöp koleksiyonunu devre dışı atmak için

> [!WARNING]
> .NET Framework 4 ile başlayarak, eşzamanlı çöp toplama arka plan çöp toplama ile değiştirilir. *Eşzamanlı* ve *arka plan* terimleri .NET Framework belgelerinde birbirinin yerine kullanılır. Arka plan çöp koleksiyonunu devre dışı katmak için, bu makalede belirtildiği gibi **gcConcurrent** öğesini kullanın.

Varsayılan olarak, çalışma süresi gecikme süresi için en iyi duruma getirilmiş eşzamanlı veya arka plan çöp toplama kullanır. Uygulamanız ağır kullanıcı etkileşimi içeriyorsa, eşzamanlı çöp toplamayı, uygulamanın çöp toplama gerçekleştirme süresini en aza indirmek için etkin bırakın. `enabled` **GcConcurrent** öğesinin özniteliğini `false`, çalışma zamanı, iş için en iyi duruma getirilmiş eşzamanlı olmayan çöp toplama yı kullanır.

Aşağıdaki yapılandırma dosyası arka plan çöp toplama devre dışı kalmaktadır:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

Makine yapılandırma dosyasında **gcConcurrentSetting** ayarı varsa, tüm .NET Framework uygulamaları için varsayılan değeri tanımlar. Makine yapılandırma dosyası ayarı uygulama yapılandırma dosya ayarını geçersiz kılar.

Eşzamanlı ve arka plan çöp toplama hakkında daha fazla bilgi için, [Eşzamanlı çöp toplama,](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) [Arka plan iş istasyonu çöp toplama](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)ve Çöp Toplama [makalesinin Temelleri'ndeki](../../../../standard/garbage-collection/fundamentals.md) [Arka plan sunucusu çöp toplama](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) bölümlerine bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, arka plan çöp toplama sağlar:

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

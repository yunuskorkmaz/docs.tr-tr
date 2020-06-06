---
title: gcServer öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968942"
---
# <a name="gcserver-element"></a>\<gcServer> öğesi

Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a>Sözdizimi

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br />Çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.|

#### <a name="enabled-attribute"></a>enabled özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Sunucu çöp toplamayı çalıştırmaz. Bu varsayılandır.|
|`true`|Sunucu çöp toplamayı çalıştırır.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Ortak dil çalışma zamanı (CLR) iki tür çöp toplamayı destekler: tüm sistemlerde kullanılabilen iş istasyonu çöp toplama ve çok işlemcili sistemlerde bulunan sunucu çöp toplama. CLR 'nin gerçekleştirdiği çöp toplamanın türünü denetlemek için **gcServer** öğesini kullanın. <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>Sunucu çöp toplamanın etkinleştirilip etkinleştirilmediğini anlamak için özelliğini kullanın.

Tek işlemcili bilgisayarlar için varsayılan iş istasyonu atık toplama en hızlı seçenek olmalıdır. İki işlemcili bilgisayarlar için iş istasyonu veya sunucu kullanılabilir. Sunucu çöp toplama, ikiden fazla işlemci için en hızlı seçenek olmalıdır. En yaygın olarak, çok işlemcili sunucu sistemleri sunucu GC 'yi devre dışı bırakır ve bir sunucu uygulamasının birçok örneği aynı makinede çalıştığında bunun yerine Workstation GC kullanır.

Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yok sayılır.

> [!NOTE]
> .NET Framework 4 ve önceki sürümlerde, sunucu çöp toplama etkinleştirildiğinde eşzamanlı çöp toplama kullanılamaz. 4,5 .NET Framework başlayarak, sunucu çöp toplama işlemi eşzamanlı olur. Eş zamanlı olmayan sunucu çöp toplamayı kullanmak için **gcServer** öğesini `true` ve [gcConcurrent öğesini](gcconcurrent-element.md) olarak ayarlayın `false` .

.NET Framework 4.6.2 ile başlayarak, sunucu GC 'yi yapılandırmak için aşağıdaki öğeleri de kullanabilirsiniz:

- [GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC yığınlarını ve işlemcileri arasında bir benzeşim olup olmadığını belirtir. Varsayılan olarak, her işlemci için bir sunucu GC yığını vardır.

- Bir işlem tarafından kullanılan Heap sayısını sınırlayan [Gcheapcount](gcheapcount-element.md).

- Kullanılabilir sunucu GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlayan [Gcheapaffinitizemask](gcheapaffinitizemask-element.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, sunucu çöp toplamayı mümkün bir şekilde sunar:

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Eşzamanlı atık toplamayı devre dışı bırakmak için](gcconcurrent-element.md#to-disable-background-garbage-collection)

---
title: GCHeapAffinitizeMask öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978384"
---
# <a name="gcheapaffinitizemask-element"></a>\<GCHeapAffinitizeMask> öğesi

GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlar.

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a>Sözdizimi

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br />GC yığınlarını ve tek tek işlemciler arasındaki benzeşimi belirtir. |

#### <a name="enabled-attribute"></a>enabled özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`nnnn`|Sunucu GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlayan bir bit maskesini oluşturan ondalık bir değer. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, sunucu GC iş parçacıkları, her işlemci için bir GC yığını, bir sunucu GC iş parçacığı ve bir arka plan sunucusu GC iş parçacığı olmak üzere kendi CPU 'SU ile sabit olarak belirlenir. .NET Framework 4.6.2 ile başlayarak, Heap sayısı **Gcheapcount** öğesiyle sınırlı olduğunda, sunucu GC yığınlarını ve işlemcileri arasındaki benzeşimi denetlemek Için **Gcheapaffinitizemask** öğesini kullanabilirsiniz.

**Gcheapaffinitizemask** genellikle iki diğer bayraklı birlikte kullanılır:

- [GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC iş parçacıklarının/yığınların CPU 'lara uygulanıp gösterilmeyeceğini denetler. `enabled` [GCNoAffinitize](gcnoaffinitize-element.md) öğesinin özniteliği, `false` kullanılacak **Gcheapaffinitizemask** ayarı için olmalıdır (varsayılan değer).

- [Gcheapcount](gcheapcount-element.md), sunucu GC için işlem tarafından kullanılan heçlerin sayısını sınırlar. Varsayılan olarak, her işlemci için bir yığın vardır.

**nnnn** , ondalık değer olarak ifade edilen bir bit maskesidir. 0 baytlık bit 0 işlemci 0 ' ı temsil eder, bayt 0 ' ın bit 1 ' i ve bu şekilde devam eder. Örneğin:

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

1023 değeri 0x3FF veya 0011 1111 1111b şeklindedir. İşlem, işlemci 0 ' dan işlemci 9 ' a kadar 10 işlemci kullanır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir uygulamanın 10 Heap/iş parçacığı ile sunucu GC kullandığını gösterir. Bu yığınların sistemde çalışan diğer uygulamalardan Heap 'lerle örtüşmesini istemediğiniz için, işlemin 0 ile 9 arasında CPU kullanması gerektiğini belirtmek için **Gcheapaffinitizemask** kullanın.

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [GCNoAffinitize öğesi](gcnoaffinitize-element.md)
- [GCHeapCount öğesi](gcheapcount-element.md)
- [Çöp toplamanın temelleri](../../../../standard/garbage-collection/fundamentals.md)
- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)

---
title: GCNoAffinitize öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978377"
---
# <a name="gcnoaffinitize-element"></a>\<GCNoAffinitize > öğesi

Sunucu GC iş parçacıklarının CPU 'Lara yapılıp yapılmayacağını belirtir.

\<Yapılandırma > \
&nbsp;&nbsp;\<çalışma zamanı > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize >

## <a name="syntax"></a>Sözdizimi

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br />Sunucu GC iş parçacıklarının/yığınların makinede bulunan işlemcilerle birlikte çalışıp çalışmadığını belirtir.|

#### <a name="enabled-attribute"></a>enabled özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Sunucu GC iş parçacıklarını CPU 'Lara göre sıralar. Bu varsayılandır.|
|`true`|, Sunucu GC iş parçacıklarını CPU 'Lar ile göstermez.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, sunucu GC iş parçacıkları ilgili CPU 'Ları ile birlikte zordur. Sistemin kullanılabilir işlemcilerin her birinin kendi GC yığını ve iş parçacığı vardır. Bu, genellikle, önbellek kullanımını optimize eden tercih edilen ayardır. .NET Framework 4.6.2 ile başlayarak, **GCNoAffinitize** öğesinin `enabled` özniteliğini `false`olarak ayarlayarak, sunucu GC iş parçacıklarının ve CPU 'ların sıkı bir şekilde bağlı olmaması gerektiğini belirtebilirsiniz.

**GCNoAffinitize** yapılandırma öğesini CPU Ile Sunucu GC iş parçacıklarını hiçbir şekilde yok etmek için tek başına belirtebilirsiniz. Ayrıca, bir uygulama tarafından kullanılan GC yığınlarının ve iş parçacıklarının sayısını denetlemek için [Gcheapcount](gcheapcount-element.md) öğesiyle birlikte da kullanabilirsiniz.

**GCNoAffinitize** öğesinin `enabled` özniteliği `false` (varsayılan değeri) ise, GC iş parçacıklarının ve yığınların hangi işlemcileri belirlemek Için [Gcheapaffinitizemask](gcheapaffinitizemask-element.md) öğesiyle birlikte GC iş parçacıklarının ve yığınların sayısını belirtmek Için [gcheapcount](gcheapcount-element.md) öğesini de kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, sunucu GC iş parçacıklarını sabit olarak göstermez:

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

Aşağıdaki örnek, sunucu GC iş parçacıklarını göstermez ve GC Heap/iş parçacığı sayısını 10 ' a kısıtlar:

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [GCHeapAffinitizeMask öğesi](gcheapaffinitizemask-element.md)
- [GCHeapCount öğesi](gcheapcount-element.md)
- [Çöp toplamanın temelleri](../../../../standard/garbage-collection/fundamentals.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)

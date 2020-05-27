---
title: GCNoAffinitize öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004744"
---
# <a name="gcnoaffinitize-element"></a>\<GCNoAffinitize> öğesi

Sunucu GC iş parçacıklarının CPU 'Lara yapılıp yapılmayacağını belirtir.

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

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

Varsayılan olarak, sunucu GC iş parçacıkları ilgili CPU 'Ları ile birlikte zordur. Sistemin kullanılabilir işlemcilerin her birinin kendi GC yığını ve iş parçacığı vardır. Bu, genellikle, önbellek kullanımını optimize eden tercih edilen ayardır. .NET Framework 4.6.2 ile başlayarak, **GCNoAffinitize** öğesinin özniteliğini olarak ayarlayarak, `enabled` `true` Sunucu GC iş parçacıklarının ve CPU 'ların sıkı bir şekilde bağlı olmaması gerektiğini belirtebilirsiniz.

**GCNoAffinitize** yapılandırma öğesini CPU Ile Sunucu GC iş parçacıklarını hiçbir şekilde yok etmek için tek başına belirtebilirsiniz. Ayrıca, bir uygulama tarafından kullanılan GC yığınlarının ve iş parçacıklarının sayısını denetlemek için [Gcheapcount](gcheapcount-element.md) öğesiyle birlikte da kullanabilirsiniz.

`enabled` **GCNoAffinitize** öğesinin özniteliği `false` (varsayılan değeri) Ise, [gcheapcount](gcheapcount-element.md) öğesini Ayrıca, GC iş parçacıklarının ve yığınların hangi Işlemcilerin kullanılacağını belirtmek Için [Gcheapaffinitizemask](gcheapaffinitizemask-element.md) öğesiyle birlikte GC iş parçacıkları ve yığınların sayısını belirtmek için de kullanabilirsiniz.

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
- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)

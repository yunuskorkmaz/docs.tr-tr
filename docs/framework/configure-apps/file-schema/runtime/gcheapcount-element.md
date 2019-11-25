---
title: GCHeapCount öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283077"
---
# <a name="gcheapcount-element"></a>\<GCHeapCount > öğesi

Sunucu atık toplama için kullanılacak Heap/iş parçacığı sayısını belirtir.

\<Yapılandırma > \
&nbsp;&nbsp;\<çalışma zamanı > \
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount >

## <a name="syntax"></a>Sözdizimi

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br />Sunucu çöp toplama için kullanılacak Heap sayısını belirtir. Heap sayısının gerçek sayısı, belirttiğiniz yığınlara ve işleminizin izin verilen işlemci sayısına göre en düşük gerekliliktir. |

#### <a name="enabled-attribute"></a>enabled özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`nn`|Sunucu GC için kullanılacak Heap sayısı.|

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, sunucu GC iş parçacıkları, her işlemci için bir GC yığını, bir sunucu GC iş parçacığı ve bir arka plan sunucusu GC iş parçacığı olmak üzere kendi CPU 'SU ile sabit olarak belirlenir. .NET Framework 4.6.2 ' den başlayarak, **Gcheapcount** öğesini kullanarak, uygulamanız tarafından sunucu GC için kullanılan yığınlarınızın sayısını sınırlayabilirsiniz. Sunucu GC için kullanılan Heap sayısını kısıtlamak, özellikle bir sunucu uygulamasının birden çok örneğini çalıştıran sistemler için yararlıdır.

**Gcheapcount** genellikle iki diğer bayraklı birlikte kullanılır:

- [GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC iş parçacıklarının/yığınların CPU 'lara uygulanıp gösterilmeyeceğini denetler.

- [Gcheapaffinitizemask](gcheapaffinitizemask-element.md), bu, CPU 'larla GC iş parçacıklarının/yığınların benzeşimini denetler.

**Gcheapcount** ayarlanır ve **GCNoAffinitize** devre dışıysa (varsayılan ayarı), *nn* GC iş parçacıkları/heçileri ve ilk *nn* işlemci arasında bir benzeşim vardır. İşlemin sunucu GC yığınlarında hangi işlemcilerin kullanıldığını belirtmek için **Gcheapaffinitizemask** öğesini kullanabilirsiniz. Aksi halde, bir sistemde birden çok sunucu işlemi çalışıyorsa, işlemci kullanımı çakışacaktır.

**Gcheapcount** ayarlanır ve **GCNoAffinitize** etkinleştirilmişse, atık toplayıcı sunucu GC için kullanılan işlemcilerin SAYıSıNı sınırlar, ancak GC yığınlarını ve işlemcileri göstermez.

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

Aşağıdaki örnek, sunucu GC iş parçacıklarını göstermez ve GC Heap/iş parçacığı sayısını 10 ' a kısıtlar.

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
- [GCNoAffinitize öğesi](gcnoaffinitize-element.md)
- [GCHeapAffinitizeMask öğesi](gcheapaffinitizemask-element.md)
- [Çöp toplamanın temelleri](../../../../standard/garbage-collection/fundamentals.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)

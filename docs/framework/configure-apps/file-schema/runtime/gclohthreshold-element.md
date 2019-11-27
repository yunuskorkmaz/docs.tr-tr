---
title: GCLOHThreshold öğesi
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451222"
---
# <a name="gclohthreshold-element"></a>GCLOHThreshold öğesi

Çöp toplayıcısının nesneleri büyük nesne yığınına (LOH) yerleştirmesine neden olan eşik boyutunu bayt cinsinden belirtir.

[\<yapılandırma >](../configuration-element.md)\
&nbsp;&nbsp;[\<çalışma zamanı >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold >

## <a name="syntax"></a>Sözdizimi

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br />Nesnelerin büyük nesne yığınında geçmesine neden olan eşik boyutunu belirtir.|

### <a name="enabled-attribute"></a>enabled özniteliği

|Value|Açıklama|
|-----------|-----------------|
|`nnnn`|Büyük nesne yığınında nesnelerin gitmesini sağlayan bayt cinsinden eşik boyutu.|

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Bu ayar .NET Framework 4,8 ' de tanıtılmıştı.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Çöp toplamanın temelleri](../../../../standard/garbage-collection/fundamentals.md)
- [GC için NET Core çalışma zamanı yapılandırma seçenekleri](../../../../core/run-time-config/garbage-collector.md)

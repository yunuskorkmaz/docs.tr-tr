---
description: 'Daha fazla bilgi edinin: GCLOHThreshold öğesi'
title: GCLOHThreshold öğesi
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: 5d4ef4e6aaf44642c2307dc27ac2e99e966d3ad0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652815"
---
# <a name="gclohthreshold-element"></a>GCLOHThreshold öğesi

Çöp toplayıcısının nesneleri büyük nesne yığınına (LOH) yerleştirmesine neden olan eşik boyutunu bayt cinsinden belirtir.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a>Syntax

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br />Nesnelerin büyük nesne yığınında geçmesine neden olan eşik boyutunu belirtir.|

### <a name="enabled-attribute"></a>enabled özniteliği

|Değer|Açıklama|
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

---
description: 'Hakkında daha fazla bilgi edinin: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> öğesi'
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: ca4099d3bf812cb25e6a611b9b51b3752b1ad361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782292"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Öğesi

Çalışma zamanının, yöntemin karma kodlarını hesaplamak için sabit miktarda bellek kullanıp kullanmadığını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a>Syntax

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br /> Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|0|Ortak dil çalışma zamanı, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak için yöntemi için değişken miktarda bellek ayırır. Bu varsayılan seçenektir.|
|1|Ortak dil çalışma zamanı, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak için yöntemi için sabit miktarda bellek ayırır.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, ortak dil çalışma zamanı yöntemi için değişken miktarda bellek ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> ve <xref:System.ArgumentException> yöntemi çok büyük dizelerin karma kodunu (birkaç milyon karakter uzunluğunda) hesaplamaya çalıştığında oluşturulabilir. Bu öğeyi bir uygulama yapılandırma dosyasına ekleyerek ve `enabled` özniteliğini "1" olarak ayarlayarak, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemin karma kodların hesaplaması için sabit miktarda bellek ayıran alternatif bir algoritma kullanmasını belirtebilirsiniz.

> [!IMPORTANT]
> `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Öğesi, Windows 8 ve sonraki sürümlerde kullanılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)

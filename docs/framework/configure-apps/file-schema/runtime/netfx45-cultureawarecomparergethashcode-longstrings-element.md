---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802117"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>\<NetFx45_CultureAwareComparerGetHashCode_LongStrings > öğesi

Çalışma zamanının <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi için karma kodları hesaplamak üzere sabit miktarda bellek kullanıp kullanmadığını belirtir.

[ **\<yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >**  

## <a name="syntax"></a>Sözdizimi

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br /> Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|0|Ortak dil çalışma zamanı, karma kodları hesaplamak için <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi için değişken miktarda bellek ayırır. Bu varsayılandır.|
|1\.|Ortak dil çalışma zamanı, karma kodları hesaplamak için <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi için sabit miktarda bellek ayırır.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Varsayılan olarak, ortak dil çalışma zamanı <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi için değişken miktarda bellek ayırır ve yöntem çok büyük dizelerin karma kodunu (birkaç milyon karakter uzunluğunda) hesaplamaya çalıştığında bir <xref:System.ArgumentException> oluşturulabilir. Bu öğeyi bir uygulama yapılandırma dosyasına ekleyip `enabled` özniteliğini "1" olarak ayarlayarak, <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yönteminin karma kodların hesaplaması için sabit miktarda bellek ayıran alternatif bir algoritma kullanmasını belirtebilirsiniz.

> [!IMPORTANT]
> `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` öğesi Windows 8 ve sonraki sürümlerde kullanılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)

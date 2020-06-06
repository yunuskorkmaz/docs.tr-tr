---
title: <performanceCounters> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697147"
---
# <a name="performancecounters-element"></a>\<performanceCounters> Öğesi

Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a>Sözdizimi

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|dosya mappingsize|Gerekli öznitelik.<br /><br /> Performans sayaçları tarafından paylaşılan genel belleğin bayt cinsinden boyutunu belirtir. Varsayılan değer 524288 ' dir.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`Configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`system.diagnostics`|ASP.NET yapılandırma bölümünün kök öğesini belirtir.|

## <a name="remarks"></a>Açıklamalar

Performans sayaçları, performans verilerini yayınlamak için bellek eşlemeli bir dosya veya paylaşılan bellek kullanır.  Paylaşılan belleğin boyutu, aynı anda kaç örnek kullanılabileceğini belirler.  İki tür paylaşılan bellek vardır: genel paylaşılan bellek ve ayrı paylaşılan bellek.  Genel paylaşılan bellek, 1,0 veya 1,1 .NET Framework sürümleriyle yüklenen tüm performans sayacı kategorileri tarafından kullanılır.  .NET Framework sürüm 2,0 ile yüklenen performans sayacı kategorileri, her bir performans sayacı kategorisiyle kendi belleği bulunan ayrı paylaşılan bellek kullanır.

Genel paylaşılan belleğin boyutu yalnızca bir yapılandırma dosyası ile ayarlanabilir.  Varsayılan boyut 524.288 bEvet, en büyük boyut 33.554.432 bayttır ve en küçük boyut 32.768 bayttır.  Genel paylaşılan bellek tüm süreçler ve kategoriler tarafından paylaşıldığından, ilk Oluşturucu boyutu belirtir.  Uygulama yapılandırma dosyanızda boyutu tanımlarsanız, bu boyut yalnızca uygulamanız, performans sayaçlarının yürütülmesine neden olan ilk uygulama ise kullanılır.  Bu nedenle, değeri belirtmek için doğru konum `filemappingsize` Machine. config dosyasıdır.  Genel paylaşılan bellekteki bellek ayrı performans sayaçları tarafından yayınlanamaz, bu nedenle farklı adlara sahip çok sayıda performans sayacı örneği oluşturulursa, genel paylaşılan bellek tükenir.

Ayrı paylaşılan belleğin boyutu için, kayıt defteri anahtarındaki DWORD FileMappingSize değeri önce \SYSTEM\CurrentControlSet\Services \Performance HKEY_LOCAL_MACHINE, \\ *\<category name>* ardından yapılandırma dosyasında genel paylaşılan bellek için belirtilen değer tarafından başvurulur. FileMappingSize değeri yoksa, ayrı paylaşılan bellek boyutu yapılandırma dosyasındaki genel ayarı bir dördüncü (1/4) olarak ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>

---
title: <TimeSpan_LegacyFormatMode> Öğesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f16a2bbd2470b4aec9e95ab67ccb0e736c4c6d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920684"
---
# <a name="timespan_legacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode > öğesi

Çalışma zamanının, değerleri olan <xref:System.TimeSpan?displayProperty=nameWithType> biçimlendirme işlemlerinde eski davranışı koruyamayacağını belirler.

\<Yapılandırma > \
\<çalışma zamanı > \
\<TimeSpan_LegacyFormatMode >

## <a name="syntax"></a>Sözdizimi

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının <xref:System.TimeSpan?displayProperty=nameWithType> değerlerle eski biçimlendirme davranışı kullanıp kullanmadığını belirtir.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çalışma zamanı eski biçimlendirme davranışını geri yüklemez.|
|`true`|Çalışma zamanı eski biçimlendirme davranışını geri yükler.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

.NET Framework 4 ' te başlayarak, <xref:System.TimeSpan?displayProperty=nameWithType> yapı <xref:System.IFormattable> arabirimini uygular ve standart ve özel biçim dizeleriyle biçimlendirme işlemlerini destekler. Bir ayrıştırma yöntemi desteklenmeyen bir biçim belirticisi veya biçim dizesiyle karşılaşırsa, bir <xref:System.FormatException>oluşturur.

.NET Framework önceki sürümlerinde, <xref:System.TimeSpan> yapı uygulamadı <xref:System.IFormattable> ve biçim dizelerini desteklemiyor. Ancak birçok geliştirici yanlışlıkla <xref:System.TimeSpan> bir dizi biçim dizesini destekledikleri ve bunları gibi <xref:System.String.Format%2A?displayProperty=nameWithType>yöntemlerle [Bileşik biçimlendirme işlemlerinde](../../../../standard/base-types/composite-formatting.md) kullandık. Genellikle, bir tür, biçim <xref:System.IFormattable> dizelerini uygular ve destekliyorsa, desteklenmeyen biçim dizelerine sahip biçimlendirme yöntemlerine yapılan çağrılar genellikle bir <xref:System.FormatException>oluşturur. Ancak, <xref:System.TimeSpan> uygulamadığından <xref:System.IFormattable>, çalışma zamanı biçim <xref:System.TimeSpan.ToString?displayProperty=nameWithType> dizesini yoksaydı ve bunun yerine yöntemi çağırılır. Bu, biçim dizelerinin biçimlendirme işlemi üzerinde hiçbir etkisi olmamasına karşın, varlığı bir <xref:System.FormatException>ile sonuçlanmamasıdır.

Eski kodun bir bileşik biçimlendirme yöntemini ve geçersiz biçim dizesini geçirdiğini ve kodun yeniden derlenmesi durumunda, eski `<TimeSpan_LegacyFormatMode>` <xref:System.TimeSpan> davranışı geri yüklemek için öğesini kullanabilirsiniz. `enabled` Bu öğenin <xref:System.FormatException> özniteliğini olarak `true`ayarladığınızda, bileşik biçimlendirme yöntemi <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, yerine öğesine <xref:System.TimeSpan.ToString?displayProperty=nameWithType> çağrı ile sonuçlanır ve bir oluşturulmaz.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir <xref:System.TimeSpan> nesnesi oluşturur ve desteklenmeyen bir standart biçim dizesi kullanarak <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> yöntemi ile biçimlendirmeye çalışır.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Örneği .NET Framework 3,5 veya önceki bir sürümde çalıştırdığınızda aşağıdaki çıktıyı görüntüler:

```
12:30:45
```

Bu, örneği .NET Framework 4 veya sonraki bir sürümde çalıştırırsanız, çıktının dışında da farklılık gösterir:

```
Invalid Format
```

Ancak, aşağıdaki yapılandırma dosyasını örnek dizinine ekler ve sonra örneği .NET Framework 4 veya sonraki bir sürümde çalıştırırsanız, çıkış, .NET Framework 3,5 üzerinde çalıştırıldığında örnek tarafından oluşturulan ile aynıdır.

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)

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
ms.openlocfilehash: c835e1bcef7bbfdc990c8db177eafed4ec6bb30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115209"
---
# <a name="timespan_legacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode > öğesi

Çalışma zamanının, <xref:System.TimeSpan?displayProperty=nameWithType> değerleriyle biçimlendirme işlemlerinde eski davranışı koruyamayacağını belirler.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**  

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

.NET Framework 4 ' te başlayarak, <xref:System.TimeSpan?displayProperty=nameWithType> yapısı <xref:System.IFormattable> arabirimini uygular ve standart ve özel biçim dizeleriyle biçimlendirme işlemlerini destekler. Bir ayrıştırma yöntemi desteklenmeyen bir biçim belirticisi veya biçim dizesiyle karşılaşırsa, bir <xref:System.FormatException>oluşturur.

.NET Framework önceki sürümlerinde, <xref:System.TimeSpan> yapısı <xref:System.IFormattable> gerçekleştirmedi ve biçim dizelerini desteklemiyor. Ancak pek çok geliştirici, <xref:System.TimeSpan> bir dizi biçim dizesini destekledikleri ve bunları <xref:System.String.Format%2A?displayProperty=nameWithType>gibi yöntemlerle [Bileşik biçimlendirme işlemlerinde](../../../../standard/base-types/composite-formatting.md) kullanmışın yanlışlıkla kabul ediyor. Genellikle, bir tür <xref:System.IFormattable> uygular ve biçim dizelerini destekliyorsa, desteklenmeyen biçim dizelerine sahip biçimlendirme yöntemlerine yapılan çağrılar genellikle bir <xref:System.FormatException>oluşturur. Ancak <xref:System.TimeSpan> <xref:System.IFormattable>uygulamadığından, çalışma zamanı biçim dizesini yoksaydı ve bunun yerine <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi çağırılır. Bu, biçim dizelerinin biçimlendirme işlemi üzerinde hiçbir etkisi olmamasına karşın, varlığı <xref:System.FormatException>neden olmadı.

Eski kodun bir bileşik biçimlendirme yöntemini ve geçersiz biçim dizesini geçirdiğini ve kodun yeniden derlenmesi durumunda, eski <xref:System.TimeSpan> davranışını geri yüklemek için `<TimeSpan_LegacyFormatMode>` öğesini kullanabilirsiniz. Bu öğenin `enabled` özniteliğini `true`olarak ayarladığınızda, bileşik biçimlendirme yöntemi <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>yerine <xref:System.TimeSpan.ToString?displayProperty=nameWithType> çağrısıyla sonuçlanır ve bir <xref:System.FormatException> oluşturulmaz.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir <xref:System.TimeSpan> nesnesini örnekleyerek, desteklenmeyen bir standart biçim dizesi kullanarak onu <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> yöntemiyle biçimlendirmeye çalışır.

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

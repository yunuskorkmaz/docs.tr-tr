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
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968903"
---
# <a name="timespan_legacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode> Öğesi

Çalışma zamanının, değerleri olan biçimlendirme işlemlerinde eski davranışı koruyamayacağını belirler <xref:System.TimeSpan?displayProperty=nameWithType> .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının değerlerle eski biçimlendirme davranışı kullanıp kullanmadığını belirtir <xref:System.TimeSpan?displayProperty=nameWithType> .|

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

.NET Framework 4 ' te başlayarak, <xref:System.TimeSpan?displayProperty=nameWithType> Yapı <xref:System.IFormattable> arabirimini uygular ve standart ve özel biçim dizeleriyle biçimlendirme işlemlerini destekler. Bir ayrıştırma yöntemi desteklenmeyen bir biçim belirticisi veya biçim dizesiyle karşılaşırsa, bir oluşturur <xref:System.FormatException> .

.NET Framework önceki sürümlerinde, <xref:System.TimeSpan> Yapı uygulamadı <xref:System.IFormattable> ve biçim dizelerini desteklemiyor. Ancak birçok geliştirici yanlışlıkla <xref:System.TimeSpan> bir dizi biçim dizesini destekledikleri ve bunları gibi yöntemlerle [Bileşik biçimlendirme işlemlerinde](../../../../standard/base-types/composite-formatting.md) kullandık <xref:System.String.Format%2A?displayProperty=nameWithType> . Genellikle, bir tür, <xref:System.IFormattable> Biçim dizelerini uygular ve destekliyorsa, desteklenmeyen biçim dizelerine sahip biçimlendirme yöntemlerine yapılan çağrılar genellikle bir oluşturur <xref:System.FormatException> . Ancak, <xref:System.TimeSpan> uygulamadığından, <xref:System.IFormattable> çalışma zamanı biçim dizesini yoksaydı ve bunun yerine <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi çağırılır. Bu, biçim dizelerinin biçimlendirme işlemi üzerinde hiçbir etkisi olmamasına karşın, varlığı bir ile sonuçlanmamasıdır <xref:System.FormatException> .

Eski kodun bir bileşik biçimlendirme yöntemini ve geçersiz biçim dizesini geçirdiğini ve kodun yeniden derlenmesi durumunda, `<TimeSpan_LegacyFormatMode>` eski davranışı geri yüklemek için öğesini kullanabilirsiniz <xref:System.TimeSpan> . `enabled`Bu öğenin özniteliğini olarak ayarladığınızda `true` , bileşik biçimlendirme yöntemi, yerine öğesine çağrı ile sonuçlanır <xref:System.TimeSpan.ToString?displayProperty=nameWithType> <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve bir oluşturulmaz <xref:System.FormatException> .

## <a name="example"></a>Örnek

Aşağıdaki örnek bir nesnesi oluşturur <xref:System.TimeSpan> ve <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> Desteklenmeyen bir standart biçim dizesi kullanarak yöntemi ile biçimlendirmeye çalışır.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Örneği .NET Framework 3,5 veya önceki bir sürümde çalıştırdığınızda aşağıdaki çıktıyı görüntüler:

```console
12:30:45
```

Bu, örneği .NET Framework 4 veya sonraki bir sürümde çalıştırırsanız, çıktının dışında da farklılık gösterir:

```console
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

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)

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
ms.openlocfilehash: 4e265fd1de6047cd53b0f8d1c20c8a9e87b3e813
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689673"
---
# <a name="timespanlegacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode > öğesi

Çalışma zamanı işlemleriyle biçimlendirmede eski davranışı korur olup olmadığını belirler <xref:System.TimeSpan?displayProperty=nameWithType> değerleri.

\<Yapılandırma > \
\<çalışma zamanı > \
\<TimeSpan_LegacyFormatMode>

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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı ile eski biçimlendirme davranışını kullanıp kullanmayacağını belirtir <xref:System.TimeSpan?displayProperty=nameWithType> değerleri.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çalışma zamanı biçimlendirme eski davranışı geri yüklemez.|
|`true`|Çalışma zamanı, eski biçimlendirme davranışını geri yükler.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

.NET Framework 4 ile başlayarak <xref:System.TimeSpan?displayProperty=nameWithType> Implements yapısı <xref:System.IFormattable> arabirimi ve biçimlendirme işlemleri ile standart ve özel biçim dizeleri destekler. Bir ayrıştırma yönteminin bir desteklenmeyen biçim belirticisi veya biçim dizesi karşılaşırsa, oluşturur bir <xref:System.FormatException>.

.NET Framework'ün önceki sürümlerindeki <xref:System.TimeSpan> uygulamaz yapısı <xref:System.IFormattable> ve biçim dizeleri desteklemiyor. Ancak, birçok geliştiricinin yanlışlıkla kabul eden <xref:System.TimeSpan> bir dizi biçim dizesini desteklemediği ve kullanılan [bileşik biçimlendirme işlemleri](../../../../../docs/standard/base-types/composite-formatting.md) gibi yöntemlerle <xref:System.String.Format%2A?displayProperty=nameWithType>. Normalde, bir tür uyguluyorsa <xref:System.IFormattable> ve destekler biçim dizeleri, biçimlendirme yöntemlerine desteklenmeyen bir biçimde çağrı dizeler genellikle throw bir <xref:System.FormatException>. Ancak, çünkü <xref:System.TimeSpan> uygulamaz <xref:System.IFormattable>, çalışma zamanı biçim dizesi yoksayıldı ve bunun yerine adlı <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi. Biçim dizeleri, biçimlendirme işlemi üzerinde hiçbir etkisi olmasına rağmen varlıklarını neden değil, yani bir <xref:System.FormatException>.

Eski kod bir bileşik biçimlendirme yöntemi ve geçersiz bir biçim dizesi geçirir ve kod yeniden çalışmaları için kullanabileceğiniz `<TimeSpan_LegacyFormatMode>` eski geri yükleme öğesi <xref:System.TimeSpan> davranışı. Ayarladığınızda `enabled` özniteliği bu öğenin `true`, bileşik biçimlendirme yöntemi çağrısı sonuçlarında <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yerine <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>ve <xref:System.FormatException> değil oluşturulur.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir <xref:System.TimeSpan> nesne ve ile biçimlendirmeniz girişimleri <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> desteklenmeyen standart biçim dizesi kullanarak yöntemi.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

.NET Framework 3.5 veya daha önceki bir sürümü örneği çalıştırdığınızda, aşağıdaki çıkışı görüntüler:

```
12:30:45
```

.NET Framework 4 veya sonraki bir sürümü örneği çalıştırırsanız bu çıkışı ile farklıdır:

```
Invalid Format
```

Örneğin dizinine şu yapılandırma dosyasını ekleyin ve ardından örnek .NET Framework 4 veya sonraki bir sürümünü çalıştırın, ancak çıktı, .NET Framework 3.5 üzerinde çalıştırıldığında örnek tarafından oluşturulanla aynıdır.

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)

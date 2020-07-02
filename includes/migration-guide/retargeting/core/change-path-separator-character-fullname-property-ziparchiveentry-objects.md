---
ms.openlocfilehash: 148312743dd274728b178951548889dc3a680528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614691"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a>ZipArchiveEntry nesnelerinin FullName özelliğindeki yol ayırıcı karakterinde değişiklik

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.1 ve sonraki sürümlerini hedefleyen uygulamalar için yol ayırıcı karakteri, \" <xref:System.IO.Compression.ZipArchiveEntry.FullName> <xref:System.IO.Compression.ZipArchiveEntry> yöntemin aşırı yüklemeleri tarafından oluşturulan nesnelerin özelliğindeki ters eğik çizgiden (") eğik çizgiyle ("/") değiştirilmiştir <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> . Bu değişiklik, .NET uygulamasını konusunun Bölüm 4.4.17.1 ile uyum sağlar [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve izin verir. ZIP arşivleri Windows dışı sistemlerde açılacak.<br />Macintosh gibi Windows dışı işletim sistemlerinde .NET Framework önceki bir sürümünü hedefleyen bir uygulama tarafından oluşturulan bir ZIP dosyasını açma işlemi, dizin yapısını koruyamaz. Örneğin, Macintosh üzerinde, dosya adı dizin yolunu, herhangi bir ters eğik çizgi ("") karakteri ve dosya adıyla birleştiren bir dosya kümesi oluşturur. Sonuç olarak, açılan dosyaların dizin yapısı korunmaz.

#### <a name="suggestion"></a>Öneri

Bu değişikliğin üzerinde etkisi. Windows işletim sisteminde .NET Framework ad alanındaki API 'Ler tarafından açılan ZIP dosyaları <xref:System.IO?displayProperty=nameWithType> en az olmalıdır. Bu API 'ler \" yol ayırıcı karakteri olarak eğik çizgi ("/") veya ters eğik çizgi (") sorunsuzca işleyebilir.<br />Bu değişiklik istenmeyen ise, [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümüne bir yapılandırma ayarı ekleyerek bunu devre dışı bırakabilirsiniz. Aşağıdaki örnek hem `<runtime>` bölümünü hem de geri `Switch.System.IO.Compression.ZipFile.UseBackslash` çevirme anahtarını gösterir:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 ve sonraki sürümlerde çalışan uygulamalar, [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının bölümüne bir yapılandırma ayarı ekleyerek bu davranışı kabul edebilir. Aşağıda hem `<runtime>` bölümü hem de `Switch.System.IO.Compression.ZipFile.UseBackslash` kabul etme anahtarı gösterilmektedir.

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>

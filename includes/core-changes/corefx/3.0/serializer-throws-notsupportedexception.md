---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568184"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>JSON serileştirici özel durum türü `JsonException` `NotSupportedException` olarak değiştirildi

.NET Core 3,0 Preview 6 ile 8 ' de, seri hale getirici desteklenmeyen bir türetilmiş koleksiyon türüyle karşılaştığı zaman bir <xref:System.Text.Json.JsonException> oluşturur. .NET Core 3,0 Preview 9 ' dan başlayarak, serileştirici bunun yerine bir <xref:System.NotSupportedException> oluşturur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 6 ' da Preview 8 ' de, seri hale getirici desteklenmeyen bir türetilen koleksiyon türüyle karşılaşıldığında bir <xref:System.Text.Json.JsonException> oluşturur. *Desteklenmeyen bir türetilmiş koleksiyon türü* , aşağıdaki türlerden birine atanabilir olmayan herhangi bir koleksiyon türüdür:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [IDictionary\<dize, T >](xref:System.Collections.Generic.IDictionary%602)

.NET Core 3,0 Preview 9 ' dan itibaren, seri hale getirici desteklenmeyen bir koleksiyon türüyle karşılaşıldığında bir <xref:System.NotSupportedException> oluşturur. Yeni özel durum türü, serisini kaldırma işleminin başarısız olduğunu daha iyi yansıtır.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Seri durumdan çıkarma sırasında <xref:System.Text.Json.JsonException> bulundursanız, <xref:System.NotSupportedException>de yakalamak isteyebilirsiniz.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->

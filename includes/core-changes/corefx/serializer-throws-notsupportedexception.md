---
ms.openlocfilehash: a35439efce25db94e70420fc6aeaf04816525758
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263315"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>JSON serileştirici özel durum türü `JsonException` iken`NotSupportedException`

.NET Core 3,0 Preview 6 ' dan 8 ' de, seri hale getirici <xref:System.Text.Json.JsonException> desteklenmeyen bir türetilmiş koleksiyon türüyle karşılaşıldığında bir oluşturur. .NET Core 3,0 Preview 9 ' dan başlayarak, serileştirici bir <xref:System.NotSupportedException> yerine bir atar.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 Preview 6 ' da Preview 8 ' de, seri hale getirici <xref:System.Text.Json.JsonException> desteklenmeyen bir türetilmiş koleksiyon türüyle karşılaşıldığında bir oluşturur. *Desteklenmeyen bir türetilmiş koleksiyon türü* , aşağıdaki türlerden birine atanabilir olmayan herhangi bir koleksiyon türüdür:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>`
- <xref:System.Collections.IDictionary>
- [IDictionary\<dizesi, T >](xref:System.Collections.Generic.IDictionary%602)

.NET Core 3,0 Preview 9 ' dan itibaren, seri hale getirici <xref:System.NotSupportedException> desteklenmeyen bir koleksiyon türüyle karşılaşıldığında bir oluşturur. Yeni özel durum türü, serisini kaldırma işleminin başarısız olduğunu daha iyi yansıtır.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Seri durumdan çıkarma sırasında <xref:System.Text.Json.JsonException> yakalama yapıyorsanız, bunu <xref:System.NotSupportedException>da ele almanız gerekebilir.

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

---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568184"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Json serializer özel `JsonException` durum türü nden`NotSupportedException`

.NET Core 3.0 Preview 6 ile 8'de, <xref:System.Text.Json.JsonException> serileştirici desteklenmeyen türemiş bir koleksiyon türüyle karşılaştığında bir atar. .NET Core 3.0 Preview 9'dan başlayarak, <xref:System.NotSupportedException> serileştirici yerine bir atar.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 Preview 6 ile Preview 8'de, serileştirici desteklenmeyen türemiş bir koleksiyon türüyle karşılaştığında bir <xref:System.Text.Json.JsonException> atar. *Desteklenmeyen türemiş koleksiyon türü,* aşağıdaki türlerden birine atayılamayan herhangi bir koleksiyon türüdür:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [IDictionary\<Dize,T>](xref:System.Collections.Generic.IDictionary%602)

.NET Core 3.0 Preview 9 ile başlayarak, <xref:System.NotSupportedException> serializer desteklenmeyen bir koleksiyon türüyle karşılaştığında bir a atar. Yeni özel durum türü, deserialization işleminin neden başarısız olduğunu daha iyi yansıtır.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Deserializing yaparken <xref:System.Text.Json.JsonException> yakalamak iseniz, aynı zamanda yakalamak <xref:System.NotSupportedException>düşünebilirsiniz.

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

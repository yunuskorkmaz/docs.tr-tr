---
ms.openlocfilehash: 572ebc47d26e30738fc4e5b8a8fab1f2643e3d83
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997721"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a>Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor

Tüm desteklenen hedef çerçeve adları (TFMs) genelinde tutarlılık için, genel olmayan ve parametresiz oluşturucular, varsayılan olarak ile seri durumdan çıkarma için artık kullanılmamaktadır <xref:System.Text.Json.JsonSerializer> .

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ve 3,1 ' de iç ve özel oluşturucular seri durumundan çıkarma için kullanılabilir. .NET Standard 2,0 ve 2,1 ' de iç ve özel oluşturuculara izin verilmez ve <xref:System.MissingMethodException> hiçbir ortak, parametresiz Oluşturucu tanımlanmadığında oluşturulur.

.NET 5,0 ' den başlayarak, parametresiz oluşturucular da dahil olmak üzere genel olmayan oluşturucular varsayılan olarak serileştirici tarafından yok sayılır. Serileştirici, seri durumdan çıkarmak için aşağıdaki oluşturuculardan birini kullanır:

- Ortak Oluşturucu ile açıklama eklenir <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .
- Ortak parametresiz Oluşturucu.
- Ortak parametreli Oluşturucu (tek ortak Oluşturucu varsa).

Bu oluşturuculardan hiçbiri kullanılabilir değilse, <xref:System.NotSupportedException> türün serisini kaldırma girişiminde bulunursa bir oluşturulur.

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

- <xref:System.Text.Json?displayProperty=fullName>(.NET Core 3,0 ve sonraki sürümleri ve .NET Standard 2,0 ve 2,1) için derleme yapan tüm hedef çerçeve adları (TFMs) arasında tutarlı davranışları zorlamak için
- Çünkü bir <xref:System.Text.Json.JsonSerializer> türün bir Oluşturucu, özellik veya alan gibi genel olmayan yüzey alanını çağırmamalıdır.

#### <a name="recommended-action"></a>Önerilen eylem

- Türü sahibiyseniz ve mümkünse, parametresiz oluşturucuyu herkese açık hale getirin.
- Aksi takdirde, `JsonConverter<T>` türü için bir uygulayın ve serisini kaldırma davranışını denetleyin.

#### <a name="category"></a>Kategori

Serileştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->

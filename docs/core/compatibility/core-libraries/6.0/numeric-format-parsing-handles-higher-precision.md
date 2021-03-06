---
title: 'Son değişiklik: standart sayısal biçim ayrıştırma duyarlığı'
description: Standart sayısal biçim ayrıştırma 'nın artık daha yüksek olan ön ekleri işlediği çekirdek .NET kitaplıklarında .NET 6 ' dan fazla değişiklik hakkında bilgi edinin.
ms.date: 02/26/2021
ms.openlocfilehash: ad1555493bbc6198541365132cc421db7c01a5a2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256926"
---
# <a name="standard-numeric-format-parsing-precision"></a>Standart sayısal biçim ayrıştırma duyarlığı

.NET artık, ve kullanarak sayıları dize olarak biçimlendirirken daha büyük duyarlık değerlerini desteklemektedir `ToString` `TryFormat` .

## <a name="change-description"></a>Açıklamayı Değiştir

Sayıları dize olarak biçimlendirirken, [biçim dizesindeki](../../../../standard/base-types/standard-numeric-format-strings.md) *duyarlık belirleyicisi* , sonuçta elde edilen dizedeki basamak sayısını temsil eder. [Dizenin başındaki karakter](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers)olan *Biçim belirticisine* bağlı olarak duyarlık, toplam basamak sayısını, önemli basamak sayısını veya ondalık basamak sayısını temsil edebilir.

Önceki .NET sürümlerinde, standart sayısal biçim ayrıştırma mantığı 99 veya daha az bir duyarlıkla sınırlandırılmıştır. Bazı sayısal türler daha fazla duyarlığa sahiptir, ancak `ToString(string format)` doğru bir şekilde kullanıma sunmaz. Örneğin, 99 'den büyük bir duyarlık belirtirseniz, `32.ToString("C100")` Biçim dizesi "precision 100 ile para birimi" yerine [özel bir sayısal biçim dizesi](../../../../standard/base-types/custom-numeric-format-strings.md) olarak yorumlanır. Özel sayısal biçim dizelerinde, karakterler [karakter sabit değerleri](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)olarak yorumlanır. Ayrıca, geçersiz Biçim belirleyicisi içeren bir biçim dizesi duyarlık değerine göre farklı şekilde yorumlanır. `H99`<xref:System.FormatException>geçersiz biçim belirticisi için, `H100` özel bir sayısal biçim dizesi olarak yorumlanırken bir oluşturur.

.Net 6 ' dan başlayarak, .NET, hassasiyetini destekler <xref:System.Int32.MaxValue?displayProperty=nameWithType> . Herhangi bir sayıda basamakla bir biçim belirticisinden oluşan bir biçim dizesi, standart bir sayısal biçim dizesi olarak yorumlanır. <xref:System.FormatException>Aşağıdaki koşullardan biri veya her ikisi için bir oluşturulur:

- Biçim belirleyicisi karakteri [Standart bir biçim belirticisi](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers)değil.
- Duyarlık daha büyüktür <xref:System.Int32.MaxValue?displayProperty=nameWithType> .

Bu değişiklik, tüm sayısal türleri etkileyen ayrıştırma mantığı 'nda uygulandı.

Aşağıdaki tabloda, çeşitli biçim dizeleri için davranış değişiklikleri gösterilmektedir.

| Biçimlendirme dizesi | Önceki davranış | .NET 6 + davranışı |
| - | - | - |
| `C2` | İki ondalık basamaklı para birimini belirtir | İki ondalık basamaklı para birimini belirtir (*değişiklik yok*) |
| `C100` | "C100" yazdıran özel sayısal biçim dizesini belirtir | 100 ondalık basamak içeren para birimini belirtir |
| `H99` | <xref:System.FormatException>Geçersiz Standart Biçim belirleyicisi "H" nedeniyle atar | <xref:System.FormatException>Geçersiz Standart Biçim belirleyicisi "H" (*değişiklik yok*) nedeniyle atar |
| `H100` | Özel sayısal biçim dizesini belirtir | <xref:System.FormatException>Geçersiz Standart Biçim belirleyicisi "H" nedeniyle atar |

## <a name="version-introduced"></a>Sunulan sürüm

6,0 Preview 2

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, sayısal biçim ayrıştırma için daha yüksek duyarlık kullanılırken beklenmeyen davranışı düzeltir.

## <a name="recommended-action"></a>Önerilen eylem

Çoğu durumda, hiçbir eylem gerekmez ve sonuçta elde edilen dizelerde doğru duyarlık gösterilir.

Ancak, duyarlık 99 ' den büyükse, Biçim belirticisinin sabit karakter olarak yorumlanacağı önceki davranışa geri dönmek istiyorsanız, bu karakteri tek tırnak içinde sarın ve ters eğik çizgiyle kaçış yapabilirsiniz. Örneğin, önceki .NET sürümlerinde, `42.ToString("G999")` döndürür `G999` . Bu davranışı sürdürmek için, biçim dizesini veya olarak değiştirin `"'G'999"` `"\\G999"` . Bu işlem .NET Framework, .NET Core ve .NET 5 + ' da çalışır.

Aşağıdaki biçim dizeleri özel sayısal biçim dizeleri olarak yorumlanmasına devam edecektir:

- ASCII alfabetik karakteri olmayan herhangi bir karakterle başlayın, örneğin `$` veya `è` .
- Örneğin, bir ASCII basamağına ait olmayan bir ASCII alfabetik karakteriyle başlayın `A$` .
- ASCII sayı dizisi ve ardından ASCII basamak karakteri olmayan herhangi bir karakterle (örneğin,) ASCII alfabetik karakteriyle başlayın `A12A` .

## <a name="affected-apis"></a>Etkilenen API’ler

Bu değişiklik, tüm sayısal türleri etkileyen ayrıştırma mantığı 'nda uygulandı.

- <xref:System.Numerics.BigInteger.ToString(System.String)?displayProperty=fullName>
- <xref:System.Numerics.BigInteger.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Numerics.BigInteger.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int32.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int32.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt32.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt32.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Byte.ToString(System.String)?displayProperty=fullName>
- <xref:System.Byte.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Byte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.SByte.ToString(System.String)?displayProperty=fullName>
- <xref:System.SByte.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.SByte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int16.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int16.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt16.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt16.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int64.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int64.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt64.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt64.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Half.ToString(System.String)?displayProperty=fullName>
- <xref:System.Half.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Half.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Single.ToString(System.String)?displayProperty=fullName>
- <xref:System.Single.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Single.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Double.ToString(System.String)?displayProperty=fullName>
- <xref:System.Double.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Double.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Decimal.ToString(System.String)?displayProperty=fullName>
- <xref:System.Decimal.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Decimal.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>

## <a name="see-also"></a>Ayrıca bkz.

- [Standart sayısal biçim dizeleri](../../../../standard/base-types/standard-numeric-format-strings.md)
- [Özel Biçim dizelerinde karakter sabit değerleri](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.BigInteger.ToString(System.String)`
- `M:System.Numerics.BigInteger.ToString(System.String,System.IFormatProvider)`
- `M:System.Numerics.BigInteger.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int32.ToString(System.String)`
- `M:System.Int32.ToString(System.String,System.IFormatProvider)`
- `M:System.Int32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt32.ToString(System.String)`
- `M:System.UInt32.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Byte.ToString(System.String)`
- `M:System.Byte.ToString(System.String,System.IFormatProvider)`
- `M:System.Byte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.SByte.ToString(System.String)`
- `M:System.SByte.ToString(System.String,System.IFormatProvider)`
- `M:System.SByte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int16.ToString(System.String)`
- `M:System.Int16.ToString(System.String,System.IFormatProvider)`
- `M:System.Int16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt16.ToString(System.String)`
- `M:System.UInt16.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int64.ToString(System.String)`
- `M:System.Int64.ToString(System.String,System.IFormatProvider)`
- `M:System.Int64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt64.ToString(System.String)`
- `M:System.UInt64.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Half.ToString(System.String)`
- `M:System.Half.ToString(System.String,System.IFormatProvider)`
- `M:System.Half.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Single.ToString(System.String)`
- `M:System.Single.ToString(System.String,System.IFormatProvider)`
- `M:System.Single.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Double.ToString(System.String)`
- `M:System.Double.ToString(System.String,System.IFormatProvider)`
- `M:System.Double.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Decimal.ToString(System.String)`
- `M:System.Decimal.ToString(System.String,System.IFormatProvider)`
- `M:System.Decimal.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`

-->

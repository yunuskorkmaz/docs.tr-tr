---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568230"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3.0, kötü biçimlendirilmiş UTF-8 bayt dizilerini değiştirirken Unicode en iyi uygulamalarını takip eder

<xref:System.Text.UTF8Encoding> Sınıf, bayt-karakter transkodlama işlemi sırasında kötü biçimlendirilmiş bir UTF-8 bayt dizisiyle karşılaştığında, bu diziyi çıkış dizesinde ' ' (U+FFFD REPLACEMENT CHARACTER) karakteriyle değiştirir. .NET Core 3.0, transkodlama işlemi sırasında bu değişikliği gerçekleştirmek için Unicode en iyi uygulama aşağıdaki .NET Core ve .NET Framework önceki sürümlerinden farklıdır.

Bu, yeni <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> ve <xref:System.Text.Rune?displayProperty=nameWithType> türler de dahil olmak üzere .NET boyunca UTF-8 işleme geliştirmek için daha büyük bir çabanın bir parçasıdır. Tür, <xref:System.Text.UTF8Encoding> yeni tanıtılan türlerle tutarlı çıktı üretecek şekilde geliştirilmiş hata işleme mekaniği verildi.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 3.0 ile başlayarak, karakterlere baytlar transcoding yaparken, <xref:System.Text.UTF8Encoding> sınıf Unicode en iyi uygulamaları dayalı karakter değiştirme gerçekleştirir. Kullanılan ikame mekanizması [Unicode Standard, Sürüm 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) tarafından _Maksimal Alt Parçaların U+FFFD Ikamesi_başlığıaltında tanımlanmıştır.

Bu _davranış_ yalnızca giriş bayt dizisi kötü biçimlendirilmiş UTF-8 verileri içeriyorsa geçerlidir. Ayrıca, <xref:System.Text.UTF8Encoding> örnek ([UTF8Encoding constructor documentation] ile `throwOnInvalidBytes: true` <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>oluşturulmuşsa, `UTF8Encoding` örnek U+FFFD değiştirme gerçekleştirmek yerine geçersiz giriş atmaya devam edecektir.

Aşağıda, bu değişikliğin geçersiz bir 3 bayt girişiyle etkisi gösteriş ve gösteriş gösteriş ve

|Kötü biçimlendirilmiş 3 bayt girişi|.NET Core 3.0'dan önceki çıktı|.NET Core 3.0 ile başlayan çıktı|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(2 karakterçıkış)| `[ FFFD FFFD FFFD ]`(3 karakterçıkış)|

Bu 3-char çıktı, tablo _3-9'a_ göre daha önce bağlı olan Unicode Standart PDF'ye göre tercih edilen çıktıdır.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Geliştirici adına herhangi bir eylem gerekmez.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
